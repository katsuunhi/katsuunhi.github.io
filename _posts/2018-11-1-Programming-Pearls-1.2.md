---
layout:     post
title:      "编程珠玑1.1-1.2"
date:       2018-11-1 12:00:00
author:     "Katsu"
---

## 如何使用位逻辑运算（如与，或，移位）来实现位向量？
<br>
```c
#define BITSPEARWORD 32
#define SHIFT 5
#define MASK 0x1F
#define N 10000000

int a[1 + N/BITSPEARWORD];

void set(int i){
    a[i >> SHIFT] |= (1 << (i & MASK));
}
void clr(int i){
    a[i >> SHIFT] &= ~(1 << (i & MASK));
}
int test(int i){
    return a[i >> SHIFT] & (1 << (i & MASK));
}
```