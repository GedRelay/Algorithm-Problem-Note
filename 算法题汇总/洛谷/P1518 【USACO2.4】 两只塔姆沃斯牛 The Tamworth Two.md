---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1518 【USACO2.4】 两只塔姆沃斯牛 The Tamworth Two
time: 2024-10-03 21:31
aliases: 
Description: 
tags: 
lastEdit: 2024-10-03-21:36
---

```toc
style: number
max_depth: 3
```

# 链接
[P1518 【USACO2.4】 两只塔姆沃斯牛 The Tamworth Two](https://www.luogu.com.cn/problem/P1518) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202410032132188.png)
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202410032132185.png)


# 分类
#模拟 #哈希表 

# 思路
- 思路 1：
按照题意进行模拟
如何判断 john 和牛永远不会相遇：当某个状态重复出现时，那么 john 和牛永远不会相遇。可以使用哈希表记录状态，这里使用的是数组


```cpp
#include<iostream>
using namespace std;
char mp[12][12];
bool vis[11][11][11][11][4][4];//1,2维为约翰的坐标，3,4维为牛的坐标，5,6维为约翰和牛的方向
int dtx[4] = { -1,0,1,0 };
int dty[4] = { 0,1,0,-1 };
int main() 
{
	int jx, jy, jd = 0, cx, cy, cd = 0;//约翰和牛的坐标和方向,0上，1右，2下，3左
	for (int i = 1; i <= 10; i++)
		for (int j = 1; j <= 10; j++) {
			cin >> mp[i][j];
			if (mp[i][j] == 'F')
				jx = i, jy = j, mp[i][j] = '.';
			if (mp[i][j] == 'C')
				cx = i, cy = j, mp[i][j] = '.';
		}
	int cnt = 0;
	do {
		if (vis[jx][jy][cx][cy][jd][cd] == 1) {
			cout << 0;
			return 0;
		}
		vis[jx][jy][cx][cy][jd][cd] = 1;
		cnt++;
		//调整约翰的信息
		int nx = jx + dtx[jd];
		int ny = jy + dty[jd];
		if (nx < 1 || nx>10 || ny < 1 || ny>10 || mp[nx][ny] == '*')//走不了换方向
			jd = (jd + 1) % 4;
		else //走得了就往前走
			jx = nx, jy = ny;
		//调整牛的信息
		nx = cx + dtx[cd];
		ny = cy + dty[cd];
		if (nx < 1 || nx>10 || ny < 1 || ny>10 || mp[nx][ny] == '*')
			cd = (cd + 1) % 4;
		else
			cx = nx, cy = ny;
	} while (jx != cx || jy != cy);
	cout << cnt;
	return 0;
}
```


- 时间复杂度：
- 空间复杂度：


---

