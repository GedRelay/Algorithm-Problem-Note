---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1508 Likecloud-吃、吃、吃
time: 2024-10-03 19:33
aliases: 
Description: 
tags: 
lastEdit: 2024-10-03-21:01
---

```toc
style: number
max_depth: 3
```

# 链接
[P1508 Likecloud-吃、吃、吃](https://www.luogu.com.cn/problem/P1508) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202410031934851.png)


# 分类
#动态规划/路径dp 

# 思路
- 思路 1：


```cpp
#include<iostream>
using namespace std;
int mp[210][210];
int dp[210][210];
inline int max3(int a, int b, int c)
{
	int t;
	t = a > b ? a : b;
	t = t > c ? t : c;
	return t;
}
inline int max2(int a, int b)
{
	return a > b ? a : b;
}
int main()
{
	int n, m;
	cin >> n >> m;
	for (int i = 1; i <= n; i++)
		for (int j = 1; j <= m; j++)
			cin >> mp[i][j];
	for (int j = 1; j <= m; j++)
		dp[1][j] = mp[1][j];
	for (int i = 2; i <= n; i++)
		for (int j = 1; j <= m; j++)
			if (j == 1)
				dp[i][j] = max2(dp[i - 1][j], dp[i - 1][j + 1]) + mp[i][j];
			else if (j == m)
				dp[i][j] = max2(dp[i - 1][j - 1], dp[i - 1][j]) + mp[i][j];
			else
				dp[i][j] = max3(dp[i - 1][j - 1], dp[i - 1][j], dp[i - 1][j + 1]) + mp[i][j];
	int ans = max3(dp[n][m / 2], dp[n][m / 2 + 1], dp[n][m / 2 + 2]);
	cout << ans;
	return 0;
}
```


- 时间复杂度：${O\left( nm \right)  }$ 
- 空间复杂度：${O\left( nm \right)  }$ 


---

