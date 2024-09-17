---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1464 Function
time: 2024-09-17 22:04
aliases: 
Description: 
tags: 
lastEdit: 2024-09-17-22:07
---

```toc
style: number
max_depth: 3
```

# 链接
[P1464 Function](https://www.luogu.com.cn/problem/P1464) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409172204273.png)


# 分类
#记忆化搜索 

# 思路
- 思路 1：


```cpp
#include<cstdio>
#include<iostream>
using namespace std;
typedef long long ll;
ll mem[22][22][22];
ll w(ll a, ll b, ll c)
{
	if (a <= 0 || b <= 0 || c <= 0)
		return 1;
	else if (a > 20 || b > 20 || c > 20)
		return w(20, 20, 20);
	else if (mem[a][b][c])
		return mem[a][b][c];
	else if (a < b * a && b * a < b && b < c * b && b * c < c)
		return mem[a][b][c] = w(a, b, c - 1) + w(a, b - 1, c - 1) - w(a, b - 1, c);
	else return mem[a][b][c] = w(a - 1, b, c) + w(a - 1, b - 1, c) + w(a - 1, b, c - 1) - w(a - 1, b - 1, c - 1);
}
int main()
{
	ll a, b, c;
	while (1)
	{
		cin >> a >> b >> c;
		if (a == -1 && b == -1 && c == -1)break;
		printf("w(%lld, %lld, %lld) = ", a, b, c);
		printf("%lld\n", w(a, b, c));
	}
	return 0;
}
```


- 时间复杂度：
- 空间复杂度：


---

