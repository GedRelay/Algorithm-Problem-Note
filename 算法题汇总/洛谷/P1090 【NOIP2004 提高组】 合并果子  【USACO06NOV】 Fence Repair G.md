---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1090 【NOIP2004 提高组】 合并果子  【USACO06NOV】 Fence Repair G
time: 2024-09-28 23:56
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
[P1090 【NOIP2004 提高组】 合并果子 【USACO06NOV】 Fence Repair G](https://www.luogu.com.cn/problem/P1090) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409282357144.png)


# 分类
#贪心 #堆 

# 思路
- 思路 1：
贪心
每次将最小的两堆进行合并，这样合并的总体力消耗是最小的
可以使用堆（优先队列）来快速找出最小的两个元素


```cpp
#include<bits/stdc++.h>
using namespace std;
priority_queue <int, vector<int>, greater<int> > q;
int main()
{
	int n, x, ans = 0;
	cin >> n;
	for (int i = 1; i <= n; i++)
	{
		cin >> x;
		q.push(x);
	}
	for (int i = 1; i < n; i++)
	{
		int a = q.top();
		q.pop();
		int b = q.top();
		q.pop();
		ans += a + b;
		q.push(a + b);
	}
	cout << ans;
	return 0;
}
```


- 时间复杂度：${O\left( n\log n \right)  }$ 
- 空间复杂度：${O\left( n \right)  }$ 


---

