---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1055 【NOIP2008 普及组】 ISBN 号码
time: 2024-09-17 15:11
aliases: 
Description: 
tags: 
lastEdit: 2024-09-17-15:12
---

```toc
style: number
max_depth: 3
```

# 链接
[P1055 【NOIP2008 普及组】 ISBN 号码](https://www.luogu.com.cn/problem/P1055) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409171511853.png)


# 分类
#模拟 #字符串 

# 思路
- 思路 1：


```cpp
#include<iostream>
using namespace std;
int main()
{
	char win[12], sbm;
	int check = 0, num = 0;
	for (int i = 0; i < 12; i++)
	{
		cin >> win[i];
		if (win[i] == '-')continue;
		check += ++num * (win[i] - '0');
	}
	check %= 11;
	cin >> sbm;
	if ((check == 10 && sbm == 'X') || (check == sbm - '0'))
		cout << "Right";
	else 
	{
		for (int i = 0; i < 12; i++)cout << win[i];
		if (check == 10)cout << "X";
		else cout << check;
	}
	return 0;
}
```


- 时间复杂度：
- 空间复杂度：


---

