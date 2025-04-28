---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: AT_abc368_f【ABC368F】Dividing Game
time: 2025-04-24 16:28
aliases: 
Description: 
tags: 
lastEdit: 2025-04-25-12:32
---

```toc
style: number
max_depth: 3
```

# 链接
[洛谷 AT_abc368_f【ABC368F】Dividing Game](https://www.luogu.com.cn/problem/AT_abc368_f) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202504241629673.png)


# 分类
#博弈论/SG定理 #质因数分解 

# 思路
- 思路 1：
SG 定理 + 因数分解

```cpp
#include <iostream>
#include <cstring>
#include <unordered_set>
using namespace std;

int n;
int mem[100010];

int sg(int x){
    if(mem[x] != -1) return mem[x];
    unordered_set<int> h;
    for(int i = 2; i <= x / i; i++){
        if(x % i == 0){
            h.insert(sg(i));
            h.insert(sg(x / i));
        }
    }
    if(x != 1) h.insert(sg(1));
    for(int i = 0; ; i++){
        if(!h.count(i)){
            mem[x] = i;
            break;
        }
    }
    return mem[x];
}

int main(){
    memset(mem, -1, sizeof mem);
    cin >> n;
    int res = 0;
    for(int i = 0, x; i < n; i++){
        cin >> x;
        res ^= sg(x);
    }
    if(res != 0) cout << "Anna";
    else cout << "Bruno";
    return 0;
}
```


- 时间复杂度：${O\left( n\sqrt{ x }  \right)  }$ 
- 空间复杂度：${O\left( x \right)  }$ 


---

