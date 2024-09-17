---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1216 【USACO1.5】 【IOI1994】数字三角形 Number Triangles
time: 2024-09-17 18:27
aliases: 
Description: 
tags: 
lastEdit: 2024-09-17-18:36
---

```toc
style: number
max_depth: 3
```

# 链接
[P1216 【USACO1.5】 【IOI1994】数字三角形 Number Triangles](https://www.luogu.com.cn/problem/P1216) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409171827328.png)


# 分类
#动态规划 

# 思路
- 思路 1：
动态规划
- 状态表示
${dp\left[ i,j \right]  }$ 表示从 ${mp\left[ i,j \right]  }$ 出发直到最后一层，所能拿到最大和

- 目标答案：
${dp\left[ 0,0 \right]  }$ 

- 初始状态：
${dp\left[ r-1,j \right] =mp\left[ r-1,j \right] \quad,j=0,1,\cdots ,r-1 }$ 

- 状态转移：
$$
dp\left[ i,j \right] =mp\left[ i,j \right] +\max\{ dp\left[ i+1,j \right] ,dp\left[ i+1,j+1 \right]  \} 
$$


```cpp
#include<iostream>
using namespace std;

int r;
int mp[1010][1010];
int dp[1010][1010];


int main()
{
	cin >> r;
	for(int i = 0; i < r; i++){
	    for(int j = 0; j <= i; j++){
	        cin >> mp[i][j];
	        if(i == r - 1){
	            dp[i][j] = mp[i][j];
	        }
	    }
	}
	
	for(int i = r - 2; i >= 0; i--){
	    for(int j = 0; j <= i; j++){
	        dp[i][j] = mp[i][j] + max(dp[i + 1][j], dp[i + 1][j + 1]);
	    }
	}
	
	cout << dp[0][0];
	return 0;
}
```


- 时间复杂度：${O\left( r^{2}  \right)  }$ 
- 空间复杂度：${O\left( r^{2}  \right)  }$ 


---

