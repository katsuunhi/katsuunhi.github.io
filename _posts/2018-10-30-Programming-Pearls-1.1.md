---
layout:     post
title:      "编程珠玑开篇"
date:       2018-10-30 12:00:00
author:     "Katsu"
---
# 编程珠玑第一章习题
>来自《编程珠玑》第2版修订版
<br>

### 1.如果不缺内存，如何使用一个具有库的语言来实现一种排序算法以表示和排序集合？<br>
#### 方法一： 使用C标准库函数qsort来排序一个整数文件
>qsort()的功能是对待排序数组进行快速排序（有关快速排序的内容会之后更新），定义为<br>
__void qsort(void *base, int nelem, unsigned int width, int ( * pfCompare)( const void *, const void *));__<br>
其中base是待排序数组的基地址，nelem是待排序数组元素个数，width是待排序数组中每个元素的大小（以字节为单位），__pfCompare是一个函数指针，指向一个“比较函数”，该函数需要程序员自己编写__<br><br>
__对于函数pfCompare,从函数声明    int ( * pfCompare)( const void *, const void *));<br>__
__可以看出它的参数有两个指针分别指向两个待比较的元素elem1和elem2，该函数的返回值有三种情况:<br>__
__(1): 返回值为负整数，\*elem1应该排在\*elem2前面；<br>__
__(2): 返回值为0，\*elem1和\*elem2顺序任意；<br>__
__(3): 返回值为正整数，\*elem2应该排在\*elem1前面；__

```c
    //方法一： 使用C标准库函数qsort来排序一个整数文件
    int intcomp(int *x, int *y){
        return *x - *y;
    }

    int a[1000000];
    int main(void){

        int i, n = 0;

        while(scanf("%d", &a[n]) != EOF)
            n ++;
        qsort(a, n, sizeof(int), incomp);
        for(i = 0; i < n; i ++)
            printf("%d\n", a[i]);

        return 0;
    }
```
<br><br>
#### 方法二： 使用C++标准模板库中的set容器完成相同的任务
>set容器的特性是，所有元素都会根据元素的键值自动排序，set的元素不像map那样可以同时拥有实值(value)和键值(key),set元素的键值就是实值，实值就是键值。set不允许两个元素有相同的键值。<br><br><br>
__set的各成员函数列表如下:__<br>
> (1). begin()--返回指向第一个元素的迭代器<br>
> (2). clear()--清除所有元素<br>
> (3). count()--返回某个值元素的个数<br>
> (4). empty()--如果集合为空，返回true<br>
> (5). end()--返回指向最后一个元素的迭代器<br>
> (6). equal_range()--返回集合中与给定值相等的上下限的两个迭代器<br>
> (7). erase()--删除集合中的元素<br>
> (8). find()--返回一个指向被查找到元素的迭代器<br>
> (9). get_allocator()--返回集合的分配器<br>
> (10). insert()--在集合中插入元素<br>
> (11). lower_bound()--返回指向大于（或等于）某值的第一个元素的迭代器<br>
> (12). key_comp()--返回一个用于元素间值比较的函数<br>
> (13). max_size()--返回集合能容纳的元素的最大限值<br>
> (14). rbegin()--返回指向集合中最后一个元素的反向迭代器<br>
> (15). rend()--返回指向集合中第一个元素的反向迭代器<br>
> (16). size()--集合中元素的数目<br>
> (17). swap()--交换两个集合变量<br>
> (18). upper_bound()--返回大于某个值元素的迭代器<br>
> (19). value_comp()--返回一个用于比较元素间的值的函数<br>

```cpp
    //方法二： 使用C++标准模板库中的set容器完成相同的任务
    int main(void){

        set<int> S;
        int i;
        set<int>::iterator j;

        while(cin >> i)
            S.insert(i);
        for(j = S.begin(); j != S.end(); j ++)
            cout << *j << "\n";

        return 0;
    }
```