---

layout:     post
title:      工作展示网页
date:       2018-12-20 12:00:00
author:     "Katsu"

---

## 导师作业：制作一个用作展示的网页
### 原始数据：师兄给的.txt文件

#### 工作进展过程 
    1. 读取文件获取实体名称
    2. 读取文件获取实体对应的编码
    3. 读取文件获取疾病列表
    4. 读取文件获取每个疾病对应的药物
    5. 制作网页，将从文本中抽取到的内容加载到网页中

#### 1.读取文件获取实体名称
    逐行读取，正则表达式匹配，寻找总结的内容，按顺序保存到列表中