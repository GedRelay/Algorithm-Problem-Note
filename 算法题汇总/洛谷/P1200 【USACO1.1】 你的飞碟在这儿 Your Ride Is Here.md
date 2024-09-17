---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1200 【USACO1.1】 你的飞碟在这儿 Your Ride Is Here
time: 2024-09-16 15:47
aliases: 
Description: 
tags: 
lastEdit: 2024-09-16-15:49
---

```toc
style: number
max_depth: 3
```

# 链接
[P1200 【USACO1.1】 你的飞碟在这儿 Your Ride Is Here](https://www.luogu.com.cn/problem/P1200) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409161548660.png)


# 分类
#字符串 #模拟 

# 思路
- 思路 1：


```cpp
#include<iostream>
#include<cstring>
using namespace std;
int main()
{
	string ufo, team;
	cin >> ufo >> team;
	int u = 1, t = 1;
	for (int i = 0; i < ufo.length(); i++)
	{
		u *= ufo[i]-64;
	}
	for (int i = 0; i < team.length(); i++)
	{
		t *= team[i]-64;
	}
	if (u % 47 == t % 47)
	{
		cout << "GO";
	}
	else
	{
		cout << "STAY";
	}
	return 0;
}
```


- 时间复杂度：${O\left( 1 \right)  }$ 
- 空间复杂度：${O\left( 1 \right)  }$ 


---

