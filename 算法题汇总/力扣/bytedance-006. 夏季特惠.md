---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: bytedance-006. 夏季特惠
time: 2025-03-07 12:22
aliases: 
Description: 
tags: 
lastEdit: 2025-03-07-14:17
---

```toc
style: number
max_depth: 3
```

# 链接
[bytedance-006. 夏季特惠](https://leetcode.cn/problems/tJau2o/) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202503071222255.png)


# 分类
#贪心 #动态规划/背包问题/01背包 

# 思路
- 思路 1：
贪心 + 01 背包动态规划
一开始的心理预期是 `X` 
一个物品消耗的心理预期为 `消耗的心理预期 = 实际花费的金额 - 优惠的金额 = b - (a - b) = 2b - a` 
贪心策略：当一个物品 `消耗的心理预期 <= 0` 时，那么这个物品一定要选，因为选择了这个物品可以提高心理预期，还可以获得其快乐值
对于 `消耗的心理预期 > 0` 的物品，可以考虑选和不选，该问题是 01 背包问题

因此该题解法为，首先遍历所有物品，计算其消耗的心理预期 `real_cost = 2b-a`，如果 `real_cost <= 0`，那么直接将其快乐值加入答案，并且心理预期提升: `X += -real_cost`。如果 `real_cost > 0`，则将其加入候选数组中。最后对候选数组求 01 背包问题，答案加上 01 背包的解即可

注意该题爆 `int` 

```cpp
#include <iostream>
#include <vector>
using namespace std;

const int N = 510;
int n, X;
int cost[N], m = 0;
long long val[N];
long long ans = 0;

int main(){
    cin >> n >> X;
    int a, b;
    long long w;
    for(int i = 1; i <= n; i++){
        cin >> a >> b >> w;
        int real_cost = 2 * b - a; // 消耗的心理预期
        if(real_cost <= 0){ // 必选
            X += -real_cost;
            ans += w;
        }
        else{ // 进入候选
            cost[m] = real_cost;
            val[m] = w;
            m++;
        }
    }
    // 01背包: 背包容量X，体积cost，价值val
    vector<long long> dp(X + 1, 0);
    for(int i = 0; i < m; i++){
        for(int j = X; j - cost[i] >= 0; j--){
            dp[j] = max(dp[j], dp[j - cost[i]] + val[i]);
        }
    }
    cout << ans + dp[X];
    return 0;
}
```


- 时间复杂度：${O\left( n \right)  }$ 
- 空间复杂度：${O\left( X+n\times \left( maxA-2minB \right)  \right)  }$ 

---

