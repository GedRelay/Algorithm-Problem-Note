---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P5116 【USACO18DEC】 Mixing Milk B
time: 2024-09-21 00:49
aliases: 
Description: 
tags: 
lastEdit: 2024-09-21-00:50
---

```toc
style: number
max_depth: 3
```

# 链接
[P5116 【USACO18DEC】 Mixing Milk B](https://www.luogu.com.cn/problem/P5116) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409210049926.png)


# 分类
#模拟 

# 思路
- 思路 1：
按照题目要求模拟即可


```cpp
#include<iostream>
using namespace std;
int main()
{
	int c[4], b[4];
	for (int i = 1; i < 4; i++)
	{
		cin >> c[i] >> b[i];
	}
	int x=1, y=2;
	for (int i = 1; i <= 100; i++)/*模拟倒100次*/
	{
		if (x == 4)x = 1;
		if (y == 4)y = 1;
		//后桶倒满
		if (b[x] + b[y] > c[y])
		{
			b[x] = b[x] + b[y] - c[y];
			b[y] = c[y];
		 }
		else//前桶倒空
		{
			b[y] = b[y] + b[x];
			b[x] = 0;
		}
		x++;
		y++;
	}
	for (int i = 1; i <= 3; i++)
	{
		cout << b[i] << endl;
	}
	return 0;
}
```


- 时间复杂度：${O\left( 1 \right)  }$ 
- 空间复杂度：${O\left( 1 \right)  }$ 


---

