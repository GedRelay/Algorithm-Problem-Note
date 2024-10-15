---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P2879 【USACO07JAN】 Tallest Cow S
time: 2024-10-05 00:03
aliases: 
Description: 
tags: 
lastEdit: 2024-10-10-09:15
---

```toc
style: number
max_depth: 3
```

# 链接
[P2879 【USACO07JAN】 Tallest Cow S](https://www.luogu.com.cn/problem/P2879) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202410050003270.png)


# 分类
#差分 #哈希表 

# 思路
- 思路 1：
如果 ${x }$ 和 ${y }$ 出现在一条信息则表示 ${x }$ 和 ${y }$ 之间的所有数都比 ${x }$ 和 ${y }$ 要小。这样的约束不可能出现跨越的情况，比如不可能出现 ${a,x,b,y }$ 的情况，但能出现嵌套，比如 ${a,x,y,b }$ 
首先将所有牛的身高设置为最高，若 ${x }$ 和 ${y }$ 有约束，则将 ${x }$ 和 ${y }$ 之间的所有牛全部减 ${1 }$，若再遇到 ${a }$ 与 ${b }$ 有约束，考虑三种情况：
1. ${a,b }$ 与 ${x,y }$ 区间不相交，如 ${a,*,*,b,*,x,*,*,y }$ ，此时只要将 ${a }$ 和 ${b }$ 之间的所有牛全部减 ${1 }$ 满足 ${a }$ 与 ${b }$ 的约束
2. ${a,b }$ 在 ${x,y }$ 区间内部，如 ${x,*,a,*,*,b,*,*,y }$ ，此时 ${x }$ 与 ${y }$ 之间高度已经满足 ${x }$ 和 ${y }$ 的约束，若将 ${a }$ 和 ${b }$ 之间的所有牛全部减 ${1 }$ ，则会满足 ${a }$ 与 ${b }$ 的约束，且不会影响 ${x }$ 与 ${y }$ 之间的约束
3. ${a,b }$ 区间内部包含 ${x,y }$ 区间，如 ${a,*,x,*,*,y,*,*,a }$ ，此时 ${x }$ 与 ${y }$ 之间高度已经满足 ${x }$ 和 ${y }$ 的约束，若将 ${a }$ 和 ${b }$ 之间的所有牛全部减 ${1 }$ ，则会满足 ${a }$ 与 ${b }$ 的约束，且不会破坏 ${x }$ 与 ${y }$ 之间的约束
总结：首先将所有牛的身高设置为最高，若两头牛有约束，则将这两头牛之间的所有牛的高度减 ${1 }$ 
注意需要判重（哈希表），不要重复减


```cpp
#include<iostream>
#include<unordered_set>
using namespace std;

int n, I, h, R;
int d[10010]; // 差分数组
struct pair_hash{
    size_t operator()(const pair<int, int> &p) const{
        return p.first ^ p.second;
    }
};
unordered_set<pair<int, int>, pair_hash> st;

int main()
{
    cin >> n >> I >> h >> R;
    d[1] += h;
    d[n + 1] -= h;
    while(R--){
        int l, r;
        cin >> l >> r;
        if(l > r) swap(l, r);
        if(!st.count({l ,r})){
            d[l + 1] -= 1;
            d[r] += 1;
            st.insert({l, r});
        }
    }
    for(int i = 1; i <= n; i++){
        d[i] += d[i - 1];
        cout << d[i] << endl;
    }
	return 0;
}
```


- 时间复杂度：${O\left( n+R \right)  }$ 
- 空间复杂度：${O\left( n+R \right)  }$ 


---

