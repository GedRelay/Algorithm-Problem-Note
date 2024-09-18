---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P3654 First Step (ファーストステップ)
time: 2024-09-18 22:52
aliases: 
Description: 
tags: 
lastEdit: 2024-09-18-22:56
---

```toc
style: number
max_depth: 3
```

# 链接
[P3654 First Step (ファーストステップ)](https://www.luogu.com.cn/problem/P3654) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409182252065.png)


# 分类
#枚举 

# 思路
- 思路 1：
遍历每个点，再从该点开始向右和向下分别看最长能有多长的空地，答案加上该空地可能的方案数即可


```cpp
#include<bits/stdc++.h>
using namespace std;
int n, m, k;
char mp[110][110];
int main()
{
	cin >> n >> m >> k;
	for (int i = 1; i <= n; i++)
		for (int j = 1; j <= m; j++)
			cin >> mp[i][j];
	int ans = 0;
	for (int i = 1; i <= n; i++)
	{
		int cnt = 0;
		for (int j = 1; j <= m; j++)//横搜
		{
			if (mp[i][j] == '.')
			{
				cnt++;
				if (j == m && cnt >= k)
					ans += cnt - k + 1;
			}
			else if (mp[i][j] == '#')
			{
				if (cnt >= k)
					ans += cnt - k + 1;
				cnt = 0;
			}
		}
	}
	for (int j = 1; j <= m; j++)
	{
		int cnt = 0;
		for (int i = 1; i <= n; i++)//竖搜
		{
			if (mp[i][j] == '.')
			{
				cnt++;
				if (i == n && cnt >= k)
					ans += cnt - k + 1;
			}
			else if (mp[i][j] == '#')
			{
				if (cnt >= k)
					ans += cnt - k + 1;
				cnt = 0;
			}
		}
	}
    cout << (k == 1 ? ans / 2 : ans);
	return 0;
}
```


- 时间复杂度：${O\left( nm \right)  }$ 
- 空间复杂度：${O\left( nm \right)  }$ 


---

