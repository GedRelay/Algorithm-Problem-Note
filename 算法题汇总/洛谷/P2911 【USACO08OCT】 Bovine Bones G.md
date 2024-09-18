---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P2911 【USACO08OCT】 Bovine Bones G
time: 2024-09-16 16:57
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
[P2911 【USACO08OCT】 Bovine Bones G](https://www.luogu.com.cn/problem/P2911) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409161657453.png)


# 分类
#概率 #枚举 

# 思路
- 思路 1：


```cpp
#include<iostream>
using namespace std;
int main()
{
	int s1, s2, s3, a[100] = { 0 }, max = 0, ans;
	cin >> s1 >> s2 >> s3;
	for (int i = 1; i <= s1; i++)
		for (int j = 1; j <= s2; j++)
			for (int k = 1; k <= s3; k++)
				a[i + j + k]++;
	for (int i = 3; i <= (s1 + s2 + s3); i++)
	{
		if (a[i] > max)
		{
			max = a[i];
			ans = i;
		}
	}
	cout << ans;
	return 0;
}
```


- 时间复杂度：${O\left( s1s2s3 \right)  }$ 
- 空间复杂度：${O\left( s1+s2+s3 \right)  }$ 


---

