---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1181 数列分段 Section I
time: 2024-09-17 18:17
aliases: 
Description: 
tags: 
lastEdit: 2024-09-17-18:23
---

```toc
style: number
max_depth: 3
```

# 链接
[P1181 数列分段 Section I](https://www.luogu.com.cn/problem/P1181) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409171817900.png)


# 分类
#数组分段 

# 思路
- 思路 1：


```cpp
#include<iostream>
using namespace std;

int n, m;

int main()
{
	cin >> n >> m;
	int cnt = 1;
	int sum = 0;
	for(int i = 0; i < n; i++){
	    int x;
	    cin >> x;
	    if(sum + x > m){
	        cnt++;
	        sum = x;
	    }
	    else sum += x;
	}
	cout << cnt;
	return 0;
}
```


- 时间复杂度：${O\left( n \right)  }$ 
- 空间复杂度：${O\left( 1 \right)  }$ 


---

