---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1208 【USACO1.3】 混合牛奶 Mixing Milk
time: 2024-09-17 18:24
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
[P1208 【USACO1.3】 混合牛奶 Mixing Milk](https://www.luogu.com.cn/problem/P1208) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409171825013.png)


# 分类
#贪心 

# 思路
- 思路 1：


```cpp
#include<bits/stdc++.h>
using namespace std;
int n, m;
int bucket, money;
struct milk
{
	int x, y;
}a[5010];

bool cmp(milk a, milk b)
{
	return a.x < b.x;
}

int main()
{
	cin >> n >> m;
	for (int i = 1; i <= m; i++)
		cin >> a[i].x >> a[i].y;
	sort(a + 1, a + m + 1, cmp);
	for (int i = 1; i <= m; i++)
	{
		if (a[i].y <= n - bucket)
		{
			money += a[i].x * a[i].y;
			bucket += a[i].y;
		}
		else
		{
			money += a[i].x * (n - bucket);
			break;
		}
	}
	cout << money;
	return 0;
}
```


- 时间复杂度：${O\left( m\log m \right)  }$ 
- 空间复杂度：${O\left( m \right)  }$ 


---

