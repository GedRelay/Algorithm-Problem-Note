---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1217 【USACO1.5】 回文质数 Prime Palindromes
time: 2024-09-17 18:37
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
[P1217 【USACO1.5】 回文质数 Prime Palindromes](https://www.luogu.com.cn/problem/P1217) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409171837083.png)


# 分类
#枚举 #构造 #质数判断 

# 思路
- 思路 1：
枚举构造出所有可能的回文数，再判断构造出来的数是否为质数


```cpp
//根据上方代码做出的答案发现没有4,6,8位的回文质数，所以再次更改一下代码：
#include<iostream>
using namespace std;
bool prime(int n)
{
	for (int i = 2; i*i <= n; i++)
		if (n % i == 0)
			return 0;
	return 1;
}
int main()//从5到1亿之间的所有的回文质数
{
	int a, b;
	cin >> a >> b;
	if (a <= 5 && b >= 5)cout << "5" << endl;
	if (a <= 7 && b >= 7)cout << "7" << endl;
	if (a <= 11 && b >= 11)cout << "11" << endl;
	//特判1位和2位的回文质数
	for (int d1 = 1; d1 <= 9; d1 += 2)//构造3位数
	{
		for (int d2 = 0; d2 <= 9; d2++)
		{
			int num = d1 * 100 + d2 * 10 + d1;
			if (num < a)continue;
			if (num > b)return 0;
			if (prime(num))cout << num << endl;
		}
	}
	for (int d1 = 1; d1 <= 9; d1 += 2)//构造5位数
	{
		for (int d2 = 0; d2 <= 9; d2++)
		{
			for (int d3 = 0; d3 <= 9; d3++)
			{
				int num = d1 * 10000 + d2 * 1000 + d3 * 100 + d2 * 10 + d1;
				if (num < a)continue;
				if (num > b)return 0;
				if (prime(num))cout << num << endl;
			}
		}
	}
	for (int d1 = 1; d1 <= 9; d1 += 2)//构造7位数
	{
		for (int d2 = 0; d2 <= 9; d2++)
		{
			for (int d3 = 0; d3 <= 9; d3++)
			{
				for (int d4 = 0; d4 <= 9; d4++)
				{
					int num = d1 * 1000000 + d2 * 100000 + d3 * 10000 + d4 * 1000 + d3 * 100 + d2 * 10 + d1;
					if (num < a)continue;
					if (num > b)return 0;
					if (prime(num))cout << num << endl;
				}
			}
		}
	}
	return 0;
}
```


- 时间复杂度：
- 空间复杂度：


---

