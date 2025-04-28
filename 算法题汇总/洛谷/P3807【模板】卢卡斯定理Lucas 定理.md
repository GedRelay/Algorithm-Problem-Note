---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P3807【模板】卢卡斯定理Lucas 定理
time: 2025-04-26 15:41
aliases: 
Description: 
tags: 
lastEdit: 2025-04-26-15:46
---

```toc
style: number
max_depth: 3
```

# 链接
[P3807【模板】卢卡斯定理Lucas 定理](https://www.luogu.com.cn/problem/P3807) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202504261542173.png)


# 分类
#组合数/卢卡斯定理  

# 思路
- 思路 1：
lucas 定理求组合数

```cpp
#include <iostream>
using namespace std;

int qpow(int a, int b, int p){
    long long res = 1, t = a;
    while(b){
        if(b & 1) res = res * t % p;
        t = t * t % p;
        b >>= 1;
    }
    return res % p;
}

int C(int n, int m, int p){
    long long res = 1;
    for(int i = 1, j = n; i <= m; i++, j--){
        res = res * qpow(i, p - 2, p) % p;
        res = res * j % p;
    }
    return res;
}

int lucas(int n, int m, int p){
    if(n < p && m < p) return C(n, m, p);
    return 1ll * C(n % p, m % p, p) * lucas(n / p, m / p, p) % p;
}

void solve(){
    int n, m, p;
    cin >> n >> m >> p;
    cout << lucas(n + m, m, p) << endl;
}

int main(){
    int T;
    cin >> T;
    while(T--){
        solve();
    }
    return 0;
}
```


- 时间复杂度：${O\left( m\log p\log _{p} n  \right)  }$ 
- 空间复杂度：${O\left( 1 \right)  }$ 


---

