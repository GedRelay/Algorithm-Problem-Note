---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: 【ABC069B】 i18n
time: 2024-09-16 15:15
aliases: 
Description: 
tags: 
lastEdit: 2024-09-16-15:18
---

```toc
style: number
max_depth: 3
```

# 链接
[【ABC069B】 i18n](https://www.luogu.com.cn/problem/AT_abc069_b) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409161516017.png)


# 分类
#字符串 

# 思路
- 思路 1：


```cpp
#include<iostream>
using namespace std;
int main()
{
	string s;
	cin >> s;
	cout << s[0]
		<< s.size() - 2
		<< s.back();
	return 0;
}
```


- 时间复杂度：${O\left( 1 \right)  }$ 
- 空间复杂度：${O\left( 1 \right)  }$ 


---

