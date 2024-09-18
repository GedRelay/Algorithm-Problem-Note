---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P2676 【USACO07DEC】 Bookshelf B
time: 2024-09-16 16:55
aliases: 
Description: 
tags: 
lastEdit: 2024-09-18-12:48
---

```toc
style: number
max_depth: 3
```

# 链接
[P2676 【USACO07DEC】 Bookshelf B](https://www.luogu.com.cn/problem/P2676) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409161655352.png)


# 分类
#贪心 #堆 

# 思路
- 思路 1：


```cpp
//20201104
#include<iostream>
#include<queue>
using namespace std;
int main()
{
	int n, b, h[20010], sum = 0, cnt = 0;
	priority_queue <int> q;
	cin >> n >> b;
	for (int i = 1; i <= n; i++)
	{
		int x;
		cin >> x;
		q.push(x);
	}
	while (sum < b)
	{
		sum += q.top();
		q.pop();
		cnt++;
	}
	cout << cnt;
	return 0;
}
```


- 时间复杂度：${O\left( n\log n \right)  }$ 
- 空间复杂度：${O\left( \log n \right)  }$ 


---

