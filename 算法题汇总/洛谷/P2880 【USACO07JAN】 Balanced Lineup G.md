---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P2880 【USACO07JAN】 Balanced Lineup G
time: 2024-10-04 16:12
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
[P2880 【USACO07JAN】 Balanced Lineup G](https://www.luogu.com.cn/problem/P2880) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202410041612504.png)


# 分类
#ST表 

# 思路
- 思路 1：
ST 表利用倍增思想，是用于解决可重复贡献问题的数据结构，如最大值、最小值、最大公约数、最小公倍数、按位或、按位与等
一般用来解决区间最大值/最小值查询 (RMQ) 问题：有一个数列 ${a_{1} ,a_{2} ,\cdots a_{n}  }$，有 ${m }$ 次查询，每次查询提供左右端点 ${l,r }$，需要快速求出区间 ${\left[ l,r \right]  }$ 的最大值或最小值

- 建表：时间复杂度 ${O\left( n\log n \right)  }$ ，空间复杂度 ${O\left( n\log n \right)  }$ 
状态表示：${f\left[ i,j \right]  }$ 表示以第 ${i }$ 个数为起点，长度为 ${2^{j}  }$ 的区间中的最大值
状态转移：${f\left[ i,j \right] =\max\left( f\left[ i,j-1 \right] ,f\left[ i+2^{j-1},j-1  \right]  \right)  }$ 
初始状态：${f\left[ i,0 \right] =a\left[ i \right]  }$ 
- 查询：时间复杂度 ${O\left( 1 \right)  }$ 
区间 ${\left[ l,r \right]  }$ 的最大值为 ${\max\left( f\left[ l,k \right] ,f\left[ r-2^{k} +1 ,k\right]  \right)  }$ ，其中 ${k=\log _{2} \left( r-l+1 \right)  }$ 


```cpp
#include<iostream>
#include<cmath>
using namespace std;

int n, q;
int f1[50010][20];
int f2[50010][20];

int main(){
    cin >> n >> q;
    for(int i = 1; i <= n; i++){
         cin >> f1[i][0];
         f2[i][0] = f1[i][0];
    }
    for(int j = 1; 1 << j <= n; j++){
        for(int i = 1; i + (1 << j) - 1 <= n; i++){
            f1[i][j] = max(f1[i][j - 1], f1[i + (1 << (j - 1))][j - 1]);
            f2[i][j] = min(f2[i][j - 1], f2[i + (1 << (j - 1))][j - 1]);
        }
    }
    while(q--){
        int l, r;
        cin >> l >> r;
        int k = log2(r - l + 1);
        int maxx = max(f1[l][k], f1[r - (1 << k) + 1][k]);
        int minn = min(f2[l][k], f2[r - (1 << k) + 1][k]);
        cout << maxx - minn << endl;
    }
    return 0;
}
```


- 时间复杂度：${O\left( n\log n \right)  }$ 
- 空间复杂度：${O\left( n\log n \right)  }$ 


---

