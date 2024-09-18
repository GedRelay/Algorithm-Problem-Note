---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P2021 faebdc玩扑克
time: 2024-09-18 21:32
aliases: 
Description: 
tags: 
lastEdit: 2024-09-18-21:38
---

```toc
style: number
max_depth: 3
```

# 链接
[P2021 faebdc玩扑克](https://www.luogu.com.cn/problem/P2021) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409182136513.png)


# 分类
#模拟 #双端队列 

# 思路
- 思路 1：
利用双端队列进行模拟


```cpp
#include<iostream>
#include<deque>
using namespace std;
deque <int> s;
int main()
{
	int n, k;
	cin >> n;
	for (int i = n; i >= 1; i--){
		s.push_front(i);
		k = s.back();
		s.pop_back();
		s.push_front(k);
	}
	for (int i = 1; i <= n; i++){
		cout << s.front() << " ";
		s.pop_front();
	}
	return 0;
}
```


- 时间复杂度：${O\left( n \right)  }$ 
- 空间复杂度：${O\left( n \right)  }$ 


---

