---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1827 【USACO3.4】 美国血统 American Heritage
time: 2024-09-18 00:02
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
[P1827 【USACO3.4】 美国血统 American Heritage](https://www.luogu.com.cn/problem/P1827) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409180002943.png)


# 分类
#递归 #字符串 

# 思路
- 思路 1：
同 P1030


```cpp
#include<iostream>
using namespace std;
void post(string pre, string in)
{
	if (pre == "")return;
	char root = pre[0];
	int pos = in.find(root);
	post(pre.substr(1, pos), in.substr(0, pos));//左
	post(pre.substr(pos + 1), in.substr(pos + 1));//右
	cout << root;
}
int main()
{
	string in, pre;
	cin >> in >> pre;
	post(pre, in);
	return 0;
}
```


- 时间复杂度：${O\left( n \right)  }$ 
- 空间复杂度：${O\left( n \right)  }$ 


---

