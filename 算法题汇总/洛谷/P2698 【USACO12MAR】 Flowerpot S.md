---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P2698 【USACO12MAR】 Flowerpot S
time: 2024-10-05 00:44
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
[P2698 【USACO12MAR】 Flowerpot S](https://www.luogu.com.cn/problem/P2698) 

# 题目


# 分类
#双指针/滑动窗口 #单调队列 

# 思路
- 思路 1：
滑动窗口 + 单调队列
题意即求一段最短的区间，使得区间中雨滴高度的极差 ${\geq D }$ 
区间长度越长，则越容易满足要求，因此可以使用滑动窗口求解。使用单调队列维护区间中雨滴高度的最大值以及最小值即可


```cpp
#include<iostream>
#include<deque>
#include<algorithm>
using namespace std;

int n, d, ans = 1e9;
pair<int, int> a[100010];

int main(){
    cin >> n >> d;
    for(int i = 0; i < n; i++){
        cin >> a[i].first >> a[i].second;
    }
    sort(a, a + n);
    deque<int> maxq, minq;
    for(int l = 0, r = 0; r < n; r++){
        while(maxq.size() && a[maxq.back()].second <= a[r].second) maxq.pop_back();
        while(minq.size() && a[minq.back()].second >= a[r].second) minq.pop_back();
        maxq.push_back(r);
        minq.push_back(r);
        while(l <= r && a[maxq.front()].second - a[minq.front()].second >= d){
            ans = min(ans, a[r].first - a[l].first);
            if(maxq.front() == l) maxq.pop_front();
            if(minq.front() == l) minq.pop_front();
            l++;
        }
    }
    cout << (ans == 1e9 ? -1 : ans);
	return 0;
}

```


- 时间复杂度：${O\left( n \right)  }$ 
- 空间复杂度：${O\left( n \right)  }$ 


---

