---
layout:     post
title:      "住房月租金预测大数据赛（付费竞赛）"
date:       2018-11-15
author:     "Katsu"
---




## 竞赛时间安排
报名阶段：2018年8月28日-2018 年11月15日<br>
提交阶段：2018年11月01日 10:00--2018年11月27日10:00<br>
评审阶段：2018年11月27日-11月30日<br>
获奖公示：2018年12月1日-2018年12月3日 (比赛获奖公示，并接受异议、申诉和违规举报)<br>
>比赛链接： <http://www.dcjingsai.com/common/cmpt/住房月租金预测大数据赛（付费竞赛）_赛体与数据.html>

<br>

#### 今日上传数据<br>
>历史最高：xgb.train(max_depth:__6__,min_child_weight:__1__,num_boost_round=__7000__)<br>&nbsp;&nbsp;&nbsp;result:train-rmse:0.463355    price[0]:4.228407   __2.05__

<br>

1:xgb.train(max_depth:__7__,min_child_weight:__1__,num_boost_round=__7000__)<br>&nbsp;&nbsp;&nbsp;result:   train-rmse:0.370231    price[0]:4.208009   2.11<br><br>
2:xgb.train(max_depth:__6__,min_child_weight:__5__,num_boost_round=__7000__)<br>&nbsp;&nbsp;&nbsp;result:train-rmse:0.501357    price[0]:4.406598   2.09<br><br>
3:xgb.train(max_depth:__5__,min_child_weight:__1__,num_boost_round=__12877__)<br>&nbsp;&nbsp;&nbsp;result:train-rmse:0.623668       2.22<br><br>
4:xgb.train(max_depth:__5__,min_child_weight:__3__,num_boost_round=__12210__)<br>&nbsp;&nbsp;&nbsp;result:train-rmse:0.640831       2.18<br><br>
5:xgb.cv(max_depth:__5__,min_child_weight:__3__,cv_round=__12210__)<br>&nbsp;&nbsp;&nbsp;result:train-rmse:0.640831       2.18

