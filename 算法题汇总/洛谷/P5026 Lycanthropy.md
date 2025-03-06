---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P5026 Lycanthropy
time: 2025-02-20 19:55
aliases: 
Description: 
tags: 
lastEdit: 2025-02-20-20:03
---

```toc
style: number
max_depth: 3
```

# 链接
[P5026 Lycanthropy](https://www.luogu.com.cn/problem/P5026) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202502201955228.png)
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202502201956885.png)


# 分类
#差分/等差数列差分 

# 思路
- 思路 1：
等差数列差分，注意数组越界问题
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202502202002825.png)


```cpp
#include<iostream>
using namespace std;

int n, m;
int a[1000010];

void add(int l, int r, int s, int d){
    if(l > m || r < 1) return;
    r = min(m, r); // 右端点越界，直接截断
    if(l < 1){ // 左端点越界，调整左端点与首项
        s = s + (1 - l) * d;
        l = 1;
    }
    // [l, r]添加一个首项为s，末项为e，公差为d的等差数列
    int e = s + (r - l) * d;
    a[l] += s;
	a[l + 1] += d - s;
	a[r + 1] -= d + e;
	a[r + 2] += e;
}

int main(){
    int v, x;
    scanf("%d%d", &n, &m);
    while(n--){
        scanf("%d%d", &v, &x);
        add(x - 3 * v, x - 2 * v - 1, 0, 1);
        add(x - 2 * v, x - 1, v, -1);
        add(x, x + 2 * v - 1, -v, 1);
        add(x + 2 * v, x + 3 * v, v, -1);
    }
    for(int i = 1; i <= m; i++){
        a[i] += a[i - 1];
    }
    for(int i = 1; i <= m; i++){
        a[i] += a[i - 1];
        printf("%d ", a[i]);
    }
    return 0;
}
```


- 时间复杂度：${O\left( n+m \right)  }$ 
- 空间复杂度：${O\left( m \right)  }$ 


---

