---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1182 数列分段 Section II
time: 2024-10-01 00:12
aliases: 
Description: 
tags: 
lastEdit: 2024-10-01-20:03
---

```toc
style: number
max_depth: 3
```

# 链接
[P1182 数列分段 Section II](https://www.luogu.com.cn/problem/P1182) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202410010012794.png)


# 分类
#二分/二分答案 #数组分段 

# 思路
- 思路 1：
二分答案
函数：f (每段和的最大值) = 段数
趋势：递减
条件：f (x) <= M
目标：找到第一个 x
使用模型 1

```cpp
#include<iostream>
using namespace std;

int n, m;
int a[100010];

int f(int x){ // 当每段和的最大值为x时，最少能分几段
    int sum = 0;
    int cnt = 0;
    for(int i = 1; i <= n; i++){
        if(sum + a[i] <= x){
            sum += a[i];
        }
        else{
            sum = a[i];
            cnt++;
        }
    }
    cnt++;
    return cnt;
}

int main(){
    cin >> n >> m;
    int l = 0, r = 1e9;
    for(int i = 1; i <= n; i++){
        cin >> a[i];
        l = max(l, a[i]);
    }
    while(l < r){
        int mid = l + r >> 1;
        if(f(mid) <= m) r = mid;
        else l = mid + 1;
    }
    cout << l;
    return 0;
}
```


- 时间复杂度：${O\left( n\log r \right)  }$ , ${r }$ 为答案的范围
- 空间复杂度：${O\left( n \right)  }$ 


---

