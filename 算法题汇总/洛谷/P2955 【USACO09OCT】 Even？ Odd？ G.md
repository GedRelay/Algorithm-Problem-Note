---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P2955 【USACO09OCT】 Even？ Odd？ G
time: 2024-09-16 16:59
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
[P2955 【USACO09OCT】 Even？ Odd？ G](https://www.luogu.com.cn/problem/P2955) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409161659435.png)


# 分类
#字符串 

# 思路
- 思路 1：
由于正整数的范围为 ${10^{60}  }$ 所以只能使用字符串存储，判断字符串最后一个字符是 `'0'` 还是 `'1'` 即可判断奇偶



```cpp
#include<iostream>
using namespace std;
int main()
{
	int n;
	string m,ans[101];
	cin >> n;
	for (int i = 1; i <= n; i++)
	{
		cin >> m;
		int last = int(m[m.length() - 1] - '0');
		if (last % 2)//奇数odd
			ans[i] = "odd";
		else
			ans[i] = "even";
	}
	for (int i = 1; i <= n; i++)
	{
		cout << ans[i] << endl;
	}
	return 0;
}
```


- 时间复杂度：${O\left( n \right)  }$ 
- 空间复杂度：${O\left( 1 \right)  }$ 


---

