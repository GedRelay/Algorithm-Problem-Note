---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P2910【USACO08OPEN】Clear And Present Danger S
time: 2025-02-22 12:37
aliases: 
Description: 
tags: 
lastEdit: 2025-02-22-12:39
---

```toc
style: number
max_depth: 3
```

# 链接
[P2910【USACO08OPEN】Clear And Present Danger S](https://www.luogu.com.cn/problem/P2910) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202502221237434.png)
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202502221237942.png)


# 分类
#最短路/floyd 

# 思路
- 思路 1：
floyd 求出每两点间的最短距离，之后按照访问顺序要求加上答案即可


```cpp
#include<iostream>
using namespace std;

const int N = 110, M = 10010;
int n, m;
int path[M];
int g[N][N]; // 邻接矩阵

int main(){
    cin >> n >> m;
    for(int i = 0; i < m; i++){
        cin >> path[i];
    }
    for(int i = 1; i <= n; i++){
        for(int j = 1; j <= n; j++){
            cin >> g[i][j];
        }
    }
    // floyd
    for(int k = 1; k <= n; k++){
        for(int i = 1; i <= n; i++){
            for(int j = 1; j <= n; j++){
                g[i][j] = min(g[i][j], g[i][k] + g[k][j]);
            }
        }
    }
    int ans = 0, start = 1;
    for(int i = 0; i < m; i++){
        ans += g[start][path[i]];
        start = path[i];
    }
    cout << ans;
    return 0;
}
```


- 时间复杂度：${O\left( n^{3} +m \right)  }$ 
- 空间复杂度：${O\left( n^{2}  \right)  }$ 


---

