---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: 水道料金 (Water Rate)
time: 2024-09-16 15:19
aliases: 
Description: 
tags: 
lastEdit: 2024-09-16-15:21
---

```toc
style: number
max_depth: 3
```

# 链接
[水道料金 (Water Rate)](https://www.luogu.com.cn/problem/AT_joi2015yo_a) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409161520757.png)


# 分类
#语法题 

# 思路
- 思路 1：
语法题，模拟即可


```cpp
#include<iostream>
using namespace std;
int main()
{
	int x, a, b, c, n,ta,tb;
	cin >> x >> a >> b >> c >> n;
	ta = n*x;
	tb = a;
	if (n > b) { tb = a + (n - b)*c; }
	if (ta > tb) { cout << tb << endl; }
	else { cout << ta << endl; }
	return 0;
}
```


- 时间复杂度：${O\left( 1 \right)  }$ 
- 空间复杂度：${O\left( 1 \right)  }$ 


---

