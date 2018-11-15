---
layout:       post
title:      "住房月租金预测大数据赛（付费竞赛）"
date:       2018-11-14
author:     "Katsu"
---

## 竞赛时间安排
报名阶段：2018年8月28日-2018 年11月15日<br>
提交阶段：2018年11月01日 10:00--2018年11月27日10:00<br>
评审阶段：2018年11月27日-11月30日<br>
获奖公示：2018年12月1日-2018年12月3日 (比赛获奖公示，并接受异议、申诉和违规举报)<br>
>比赛链接： <http://www.dcjingsai.com/common/cmpt/住房月租金预测大数据赛（付费竞赛）_赛体与数据.html>

<br>

## 进展

<br>

### 2018-11-14

数据处理代码：

 ```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import matplotlib.pyplot as plt
import xgboost as xgb
from sklearn.ensemble import GradientBoostingClassifier  #GBM algorithm
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error
from xgboost.sklearn import XGBClassifier
from scipy import stats
file= './train.csv'
train=pd.read_csv(file)
file1='./test.csv'
test1=pd.read_csv(file1)

train.rename(columns={'时间':'time', '小区名':'community', '小区房屋出租数量':'house_num', '楼层':'floor', '总楼层':'total_floor', '房屋面积':'area', '房屋朝向':'orientation', '居住状态':'status', '卧室数量':'bedroom_num',
       '厅的数量':'livingroom_num', '卫的数量':'bathroom_num', '出租方式':'method', '区':'Urban', '位置':'location', '地铁线路':'underground', '地铁站点':'underground_station', '距离':'distance', '装修情况':'Decoration', '月租金':'price'},inplace=True)
test1.rename(columns={'时间':'time', '小区名':'community', '小区房屋出租数量':'house_num', '楼层':'floor', '总楼层':'total_floor', '房屋面积':'area', '房屋朝向':'orientation', '居住状态':'status', '卧室数量':'bedroom_num',
       '厅的数量':'livingroom_num', '卫的数量':'bathroom_num', '出租方式':'method', '区':'Urban', '位置':'location', '地铁线路':'underground', '地铁站点':'underground_station', '距离':'distance', '装修情况':'Decoration', 'id':'id'},inplace=True)

id1=test1.id
test1= test1.drop(['id'],axis=1)

quantity = [attr for attr in train.columns if train.dtypes[attr] != 'object']  # 数值变量集合
quality = [attr for attr in train.columns if train.dtypes[attr] == 'object']  # 类型变量集合
def encode(frame,test, feature):
    '''
    对所有类型变量，依照各个类型变量的不同取值对应的样本集内房价的均值，按照房价均值高低
    对此变量的当前取值确定其相对数值1,2,3,4等等，相当于对类型变量赋值使其成为连续变量。
    此方法采用了与One-Hot编码不同的方法来处理离散数据，值得学习
    注意：此函数会直接在原frame的DataFrame内创建新的一列来存放feature编码后的值。
    '''
    ordering = pd.DataFrame()
    ordering['val'] = frame[feature].unique()
    ordering.index = ordering.val
    ordering['price_mean'] = frame[[feature, 'price']].groupby(feature).mean()['price']
    # 上述 groupby()操作可以将某一feature下同一取值的数据整个到一起，结合mean()可以直接得到该特征不同取值的房价均值
    ordering = ordering.sort_values('price_mean')
    ordering['order'] = range(1, ordering.shape[0]+1)
    ordering = ordering['order'].to_dict()
    for attr_v, score in ordering.items():
        # e.g. qualitative[2]: {'Grvl': 1, 'MISSING': 3, 'Pave': 2}
        frame.loc[frame[feature] == attr_v, feature+'_E'] = score
        test1.loc[test1[feature] == attr_v, feature+'_E'] = score

quality_encoded = []
# 由于qualitative集合中包含了非数值型变量和伪数值型变量（多为评分、等级等，其取值为1,2,3,4等等）两类
# 因此只需要对非数值型变量进行encode()处理。
# 如果采用One-Hot编码，则整个qualitative的特征都要进行pd,get_dummies()处理
for q in quality:
    encode(train,test1, q)
    quality_encoded.append(q+'_E')
train.drop(quality, axis=1, inplace=True)
test1.drop(quality, axis=1, inplace=True) # 离散变量已经有了编码后的新变量，因此删去原变量
# df_tr.shape = (1460, 80)
print(quality_encoded, '\n{} qualitative attributes have been encoded.'.format(len(quality_encoded)))


#train,test=train_test_split(train,test_size=0.001)
y = train.price
X = train.drop(['price'],axis=1)
#val_y = test.price
#val_X = test.drop(['price'],axis=1)


#xgb矩阵赋值
#xgb_val = xgb.DMatrix(val_X,label=val_y)
xgb_train = xgb.DMatrix(X, label=y)


 ```

<br>

 矩阵赋值以及写文件:
 ```python
 #xgb矩阵赋值并写try.csv文件
xgb_val2 = xgb.DMatrix(test1)
p=bst.predict(xgb_val2)
id1['price']=p

sp = pd.DataFrame()
sp['id']=id1
sp.drop(sp.index[-1],inplace=True)
sp['price']=p
sp.to_csv('try.csv',index=False)
d=pd.read_csv('try.csv')
print(d)
 ```

<br>

训练代码:
```python
#xgboost训练
watchlist = [(xgb_train,'train')]#,(xgb_val,'val')]
params = {'objective':'reg:linear','eval_metric':'rmse','max_depth':7,'min_child_weight':2 }

bst = xgb.train(params,dtrain=xgb_train,num_boost_round=7000,evals = watchlist,early_stopping_rounds=100)
#make prediction
#p = bst.predict(xgb_val)
#p=np.expm1(p) 对数处理未完善
#print(mean_squared_error(val_y,p)**0.5)


```

<br><br>

1.xgb.cv()，得到的目前最优参数为'max_depth':__9__,'min_child_weight':__5__
```python
select=[];
best=[];
xgtrain = xgb.DMatrix(train_X,label=train_y)
for i in range(9,12,1):
    for j in range(4,8,1):
        select.append((i,j))
for i in select:
    params = {'objective':'reg:linear','eval_metric':'rmse' ,'max_depth':i[0],'min_child_weight':i[1],'tree_method':'gpu_hist'}
    sult = xgb.cv(params,xgtrain,num_boost_round=20000,nfold=5,verbose_eval=True , 
                          metrics='rmse',early_stopping_rounds=50,seed=27)
    best.append(i)
    best.append(sult.iloc[-1]['test-rmse-mean'])
```
相比于使用xgb.train()训练得到的结果，默认参数（'max_depth':__6__,'min_child_weight':__1__）训练结果更好
```python
params = {'objective':'reg:linear','eval_metric':'rmse' ,'max_depth':9,'min_child_weight':5,'tree_method':'gpu_hist'}

#xgtrain = xgb.DMatrix(train_X,label=train_y)
#xgtest = xgb.DMatrix(test_df)
watchlist=[(xgtrain,'train')]

bst=xgb.train(params,dtrain=xgtrain,num_boost_round=2000,evals=watchlist)
test_predictions = bst.predict(xgtest) 
```

<br><br>

#### 今日上传数据<br>

>1:第一次没有记录结果   2.19<br><br>
2:xgb.train(max_depth:__9__,min_child_weight:__5__,num_boost_round=__2000__)  --->   train-rmse:0.409119    price[0]:4.303184   2.18<br><br>
3:xgb.train(max_depth:__9__,min_child_weight:__5__,num_boost_round=__7000__)  --->   train-rmse:0.335323    price[0]:4.175468   2.12<br><br>
4:xgb.train(max_depth:__7__,min_child_weight:__2__,num_boost_round=__7000__)  --->   train-rmse:0.375845    price[0]:4.269687   2.08<br><br>
5:xgb.train(max_depth:__6__,min_child_weight:__1__,num_boost_round=__7000__)  --->   train-rmse:0.463355    price[0]:4.228407   __2.05__


