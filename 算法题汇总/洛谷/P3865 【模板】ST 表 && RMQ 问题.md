---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P3865 【模板】ST 表 && RMQ 问题
time: 2024-10-04 17:22
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
[P3865 【模板】ST 表 && RMQ 问题](https://www.luogu.com.cn/problem/P3865) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202410041722696.png)


# 分类
#ST表 

# 思路
- 思路 1：
ST 表模板题
ST 表利用倍增思想，是用于解决可重复贡献问题的数据结构，如最大值、最小值、最大公约数、最小公倍数、按位或、按位与等
一般用来解决区间最大值/最小值查询 (RMQ) 问题：有一个数列 ${a_{1} ,a_{2} ,\cdots a_{n}  }$，有 ${m }$ 次查询，每次查询提供左右端点 ${l,r }$，需要快速求出区间 ${\left[ l,r \right]  }$ 的最大值或最小值

- 建表：时间复杂度 ${O\left( n\log n \right)  }$ ，空间复杂度 ${O\left( n\log n \right)  }$ 
状态表示：${f\left[ i,j \right]  }$ 表示以第 ${i }$ 个数为起点，长度为 ${2^{j}  }$ 的区间中的最大值
状态转移：${f\left[ i,j \right] =\max\left( f\left[ i,j-1 \right] ,f\left[ i+2^{j-1},j-1  \right]  \right)  }$ 
初始状态：${f\left[ i,0 \right] =a\left[ i \right]  }$ 
- 查询：时间复杂度 ${O\left( 1 \right)  }$ 
区间 ${\left[ l,r \right]  }$ 的最大值为 ${\max\left( f\left[ l,k \right] ,f\left[ r-2^{k} +1 ,k\right]  \right)  }$ ，其中 ${k=\log _{2} \left( r-l+1 \right)  }$ 

注意该题卡常数：需要使用快读，对数预处理，`print` 输出


```cpp
#include<iostream>
using namespace std;

int n, m;
int f[100010][20];
int Log2[100010];

void pre() {
  Log2[1] = 0;
  Log2[2] = 1;
  for (int i = 3; i < 100010; i++) {
    Log2[i] = Log2[i / 2] + 1;
  }
}

inline int read(){
	int x=0,f=1;char ch=getchar();
	while (ch<'0'||ch>'9'){if (ch=='-') f=-1;ch=getchar();}
	while (ch>='0'&&ch<='9'){x=x*10+ch-48;ch=getchar();}
	return x*f;
}


int main(){
    pre();
    cin >> n >> m;
    for(int i = 1; i <= n; i++){
        f[i][0] = read();
    }
    for(int j = 1; 1 << j <= n; j++){
        for(int i = 1; i + (1 << j) - 1 <= n; i++){
            f[i][j] = max(f[i][j - 1], f[i + (1 << (j - 1))][j - 1]);
        }
    }
    while(m--){
        int l, r;
        l = read();
        r = read();
        int k = Log2[r - l + 1];
        printf("%d\n", max(f[l][k], f[r - (1 << k) + 1][k]));
    }
    return 0;
}
```


- 时间复杂度：${O\left( n\log n \right)  }$ 
- 空间复杂度：${O\left( n\log n \right)  }$ 


---

