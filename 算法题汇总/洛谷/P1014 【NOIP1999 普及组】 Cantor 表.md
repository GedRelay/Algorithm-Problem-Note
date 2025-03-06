---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1014 【NOIP1999 普及组】 Cantor 表
time: 2024-11-04 20:52
aliases: 
Description: 
tags: 
lastEdit: 2024-11-04-20:58
---

```toc
style: number
max_depth: 3
```

# 链接
[P1014 【NOIP1999 普及组】 Cantor 表](https://www.luogu.com.cn/problem/P1014) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202411042052645.png)


# 分类
#找规律 #二分 

# 思路
- 思路 1：
找规律
分子的规律，依次是：
1
12
321
1234
54321
...

分母的规律，依次是：
1
21
123
4321
12345
...

可以发现对于分子，奇数行逆序，偶数行顺序，对于分母，奇数行顺序，偶数行逆序
因此只需要找到 ${n }$ 在第几行第几列即可
假设 ${n }$ 在第 ${x }$ 行，那么前面 ${x-1 }$ 行一共有 ${\frac{\left( 1+x-1 \right) \times \left( x-1 \right) }{2} =\frac{x\left( x-1 \right) }{2}  }$ 个数字
因此只需要找到最后一个 ${x }$ 使得 ${\frac{x\left( x-1 \right) }{2} <n }$ 就找到了所在的行数，可以使用二分查找


```cpp
#include<iostream>
using namespace std;

int n;

int main(){
    cin >> n;
    // 看n是在第几行
    int l = 1, r = 10000;
    while(l < r){
        int mid = l + r + 1 >> 1;
        if(mid * (mid - 1) / 2 < n) l = mid;
        else r = mid - 1;
    }
    // 在第l行，第n - l * (l - 1) / 2列
    int row = l, col = n - l * (l - 1) / 2;
    // 分子：奇数行逆序，偶数行顺序
    cout << (row & 1 ? row - col + 1 : col) << "/";
    // 分母：奇数行顺序，偶数行逆序
    cout << (row & 1 ? col : row - col + 1);
    return 0;
}
```


- 时间复杂度：${O\left( \log n \right)  }$ 
- 空间复杂度：${O\left( 1 \right)  }$ 


---

