---
layout:     post
titile:     编程珠玑开篇1.3"
date:       2018-11-04
author:     "Katsu"
---



## 3.运行时效率是设计目标的一个重要组成部分，所得到的程序需要足够高效。 在你自己的系统上实现位图排序并度量其运行时间。该时间与系统排序的运行时间以及习题1中排序的运行时间相比如何？假设n为10000000，且输入文件包含1000000个整数。
<br>
<br>
```c
int main(void){
    int i;
    for(i = 0; i < N; i ++)
        cir(i);
    while(scanf("%d", &i) != EOF)
        set(i);
    for(i = 0; i < N; i ++)
        if(test(i))
            print("%d\n", i);

    return 0;
}
```
