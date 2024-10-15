---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P2701 【USACO5.3】 巨大的牛棚Big Barn
time: 2024-10-04 15:31
aliases: 
Description: 
tags: 
lastEdit: 2024-10-10-09:15
---

```toc
style: number
max_depth: 3
```

# 链接
[P2701 【USACO5.3】 巨大的牛棚Big Barn](https://www.luogu.com.cn/problem/P2701) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202410041532242.png)


# 分类
#动态规划 

# 思路
- 思路 1：
- 状态表示：
${dp\left[ i,j \right]  }$ 表示以 ${\left( i,j \right)  }$ 为右下角点的最大全 ${0 }$ 矩阵的边长

- 目标答案：
${\max\{ dp\left[ 1,1 \right] ,dp\left[ 1,2 \right] ,\cdots ,dp\left[ n,n \right]  \}  }$ 

- 初始状态：
${dp\left[ i,j \right] =0\quad,i=1\cdots n,j=1\cdots n }$ 

- 状态转移：
$$
dp\left[ i,j \right] =\begin{cases} 0&,mp\left[ i,j \right] =1\\1+\min\{ dp\left[ i-1,j \right] ,dp\left[ i,j-1 \right] ,dp\left[ i-1,j-1 \right]  \} &,mp\left[ i,j \right] \neq 1 \end{cases} 
$$


```cpp
#include<iostream>
#include<algorithm>
using namespace std;
int n, t;
bool mp[1100][1100];
int dp[1100][1100];
int main()
{
	cin >> n >> t;
	while (t--) {
		int x, y;
		cin >> x >> y;
		mp[x][y] = 1; // 1表示有树
	}
	int ans = 0;
	for (int x = 1; x <= n; x++)
		for (int y = 1; y <= n; y++) {
			if (mp[x][y] == 0)
				dp[x][y] = min(dp[x - 1][y], min(dp[x][y - 1], dp[x - 1][y - 1])) + 1;
			ans = max(ans, dp[x][y]);
		}
	cout << ans;
	return 0;
}
```


- 时间复杂度：${O\left( n^{2}  \right)  }$ 
- 空间复杂度：${O\left( n^{2}  \right)  }$ 


---

