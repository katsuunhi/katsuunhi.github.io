---
layout:     post
date:       2019-01-25 00:00:00
author:     "Katsu"
title:      python小练习

---




## PythonExercises 
<br>
一些按照难度排列的Python练习题。欢迎提交你的答案！<br>
从开始学Python以来，接触了不少练习题。下面十个练习题，是我做出来的和想做出来的题里比较有趣的，现在按照难度由低到高排列。欢迎到Github上提交你的答案。<br><br>

### 一、猜数字
<br>
经典的猜数字游戏，几乎所有人学编程时都会做。<br>
__功能描述__ ：随机选择一个三位以内的数字作为答案。用户输入一个数字，程序会提示大了或是小了，直到用户猜中。<br><br>

### 二、FizzBuzz
<br>
另一道经典编程题。<br><br>
__功能描述__ ：遍历并打印0到100，如果数字能被3整除，显示Fizz；如果数字能被5整除，显示Buzz；如果能同时被3和5整除，就显示FizzBuzz。结果应该类似：0,1,2，Fizz，4，Buzz，6……14，FizzBuzz，16……<br><br>

### 三、猜数字的AI
<br>
和猜数字一样，不过这次是设计一个能猜数字的AI<br><br>
__功能描述__ :用户输入一个单位以内的数字，AI要用最少的次数猜中，并且显示出猜的次数和数字。<br><br>

### 四、整点报时
<br>
老式挂钟会在整点的报时，响铃的次数和时间相等。我们设计一个在电脑上运行的报时器。<br>
__功能描述__ ：运行后，在每一个整点长响一声，半个整点短响两声。实现睡眠模式，晚上十二点到早上六点不响铃。<br><br><br>


## 代码
### 一、猜数字
__知识点__ : __random.randint(min, max)__,用于随机生成一个[min, max]的整数<br>
```python
# 一、猜数字
# 经典的猜数字游戏，几乎所有人学编程时都会做。
# 功能描述：随机选择一个三位以内的数字作为答案。用户输入一个数字，程序会提示大了或是小了，直到用户猜中
import random
digit = int(input("input a digit:"))
answer = random.randint(0,100)
while digit != answer:
    if answer > digit:
        print(answer, " too big")
    else:
        print(answer, " too small")
    answer = random.randint(0,100)
print("you are right! it is ", digit)
```
<br>
### 二、FizzBuzz
```python
# 二、FizzBuzz
# 功能描述：
# 遍历并打印0到100，
# 如果数字能被3整除，显示Fizz；
# 如果数字能被5整除，显示Buzz；
# 如果能同时被3和5整除，就显示FizzBuzz。
# 结果应该类似：0,1,2，Fizz，4，Buzz，6……14，FizzBuzz，16……
for i in range(0, 101):
    if i%3 == 0 and i%5 != 0:
        print("Fizz", end = " ")
    if i%5 == 0 and i%3 != 0:
        print("Buzz", end = " ")
    if i%3 == 0 and i%5 == 0:
        print("FizzBuzz", end = " ")
    if i%3 != 0 and i%5 != 0:
        print(i, end = " ")
```
<br>
### 三、猜数字的AI
__知识点__ : 二分法查找，取一个四分点用来求下次的猜测值，相比于添加top、base记录上下限省了一个变量
```python
# 三、猜数字的AI
# 和猜数字一样，不过这次是设计一个能猜数字的AI。
# 功能描述：用户输入一个单位以内的数字，AI要用最少的次数猜中，并且显示出猜的次数和数字
import random
digit = int(input("input a digit:"))
times = 0
answer = 100//2
middle = 100//4
times = times + 1
while digit != answer:
    if answer < digit:
        print(answer, " too small")
        answer = answer + middle
        times = times + 1
    if answer > digit:
        print(answer, " too big")
        answer = answer - middle
        times = times + 1
    middle = middle//2
    if middle == 0:
        middle = 1
print(answer, " is right! you have tried for ", times, " times!")
```
<br>
### 四、整点报时
__知识点__  <br>
    1. __winsound.Beep(Hz, ms)__,蜂鸣，频率为Hz，时间为ms，人耳可听到的频率范围为（20，20K）<br>
    2. __time.localtime()__，获取当前时间，tm_hour、tm_minute、tm_sec分别为对应的时分秒<br>
```python
# 四、整点报时
# 老式挂钟会在整点的报时，响铃的次数和时间相等。我们设计一个在电脑上运行的报时器。
# 功能描述：运行后，在每一个整点长响一声，半个整点短响两声。实现睡眠模式，晚上十二点到早上六点不响铃。
import time
import winsound

running = True
def long_Beep():
#   music = "music.mp3"
#   winsound.PlaySound(music, winsound.SND_ALIAS)
    winsound.Beep(370, 4000)
def short_Beep():
    winsound.Beep(370, 2000)    
while running:
    t = time.localtime()
    # fomat = "%H %M"
    # now = time.strftime(fomat, t).split(' ')
    # hour = int(now[0])
    # minute = int(now[1])
    hour = t.tm_hour
    minute = t.tm_min
    second = t.tm_sec
    if hour >= 6 and minute == 0:
        long_Beep()
        time.sleep(60 - second)
    if hour >= 6 and minute == 30:
        short_Beep()
        short_Beep()
        time.sleep(60 - second)
    if hour == 22 and minute == 32:
        long_Beep()
        short_Beep()
        time.sleep(60 - second)
```
