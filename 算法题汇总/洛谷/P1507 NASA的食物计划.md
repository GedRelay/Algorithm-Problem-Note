---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1507 NASA的食物计划
time: 2024-09-17 22:36
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
[P1507 NASA的食物计划](https://www.luogu.com.cn/problem/P1507) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409172237258.png)


# 分类
#动态规划/背包问题/二维费用背包 

# 思路
- 思路 1：
体积作为第一维费用
质量作为第二维费用
卡路里为价值
该问题为二维费用背包


```cpp
#include<iostream>
using namespace std;
int dp[420][420];
int main()
{
	int maxv, maxw, n;
	cin >> maxv >> maxw >> n;
	for (int i = 1; i <= n; i++){
		int v, w, val;
		cin >> v >> w >> val;
		for (int j = maxv; j >= v; j--)
			for (int k = maxw; k >= w; k--)
				dp[j][k] = max(dp[j][k], dp[j - v][k - w] + val);
	}
	cout << dp[maxv][maxw];
	return 0;
}
```


- 时间复杂度：${O\left( nVW \right)  }$ 
- 空间复杂度：${O\left( VW \right)  }$ 


---

