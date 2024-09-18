---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1596 【USACO10OCT】 Lake Counting S
time: 2024-09-17 23:05
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
[P1596 【USACO10OCT】 Lake Counting S](https://www.luogu.com.cn/problem/P1596) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409172308019.png)


# 分类
#搜索/floodfill 

# 思路
- 思路 1：
遍历每个点，若遇到没有遍历过的 `'W'` 则使用 floodfill 算法遍历其所在湖的联通块，同时计数器 `+1` 


```cpp
#include<iostream>
using namespace std;
char mp[110][110];
int vis[110][110];
int ans = 0;
int dx[8] = { -1,-1,-1,0,0,1,1,1 };//8个方向
int dy[8] = { -1,0,1,-1,1,-1,0,1 };
int n, m;

void dfs(int x, int y)
{
	for (int i = 0; i < 8; i++){
		int nx = x + dx[i];
		int ny = y + dy[i];
		if (1 <= nx && nx <= n && 1 <= ny && ny <= m && mp[nx][ny] == 'W' && !vis[nx][ny]){
			vis[nx][ny] = 1;
			dfs(nx, ny);
		}
	}
}

int main()
{
	cin >> n >> m;
	for (int i = 1; i <= n; i++)
		for (int j = 1; j <= m; j++)
			cin >> mp[i][j];
	for (int i = 1; i <= n; i++){
		for (int j = 1; j <= m; j++){
			if (mp[i][j] == 'W' && !vis[i][j]){
				dfs(i, j);
				ans++;
			}
		}
	}
	cout << ans;
	return 0;
}
```


- 时间复杂度：${O\left( nm \right)  }$ 
- 空间复杂度：${O\left( nm \right)  }$ 


---

