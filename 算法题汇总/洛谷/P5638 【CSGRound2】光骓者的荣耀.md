---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P5638 【CSGRound2】光骓者的荣耀
time: 2024-09-21 00:50
aliases: 
Description: 
tags: 
lastEdit: 2024-09-21-00:58
---

```toc
style: number
max_depth: 3
```

# 链接
[P5638 【CSGRound2】光骓者的荣耀](https://www.luogu.com.cn/problem/P5638) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409210055768.png)


# 分类
#前缀和 #枚举 

# 思路
- 思路 1：
前缀和
枚举每个长度为 ${k }$ 的区间，利用前缀和快速求出该区间的和，求最大的区间和
所有数字的和减去最大区间和就是答案


```cpp
#include<iostream>
#include<climits>
#include<cmath>
using namespace std;
typedef long long ll;
int n, k;
ll a[1000100];
ll sum[1000100];
int main()
{
    cin >> n >> k;
    for (int i = 1; i < n; i++) {
        cin >> a[i];
        sum[i] = sum[i - 1] + a[i];
    }
    ll maxsum = 0;
    if (k != 0) {
        for (int i = 1; i + k - 1 < n; i++) {
           maxsum = max(maxsum, sum[i + k - 1] - sum[i - 1]);
        }
    }
    cout << sum[n - 1] - maxsum;
    return 0;
}

```


- 时间复杂度：${O\left( n \right)  }$ 
- 空间复杂度：${O\left( n \right)  }$ 


---

