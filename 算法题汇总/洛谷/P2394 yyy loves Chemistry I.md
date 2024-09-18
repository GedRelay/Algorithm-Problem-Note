---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P2394 yyy loves Chemistry I
time: 2024-09-16 16:43
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
[P2394 yyy loves Chemistry I](https://www.luogu.com.cn/problem/P2394) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409161644043.png)


# 分类
#语法题 

# 思路
- 思路 1：


```cpp
#include <stdio.h>
int main()
{
    long double m;
    scanf ( "%15Lf", &m );//强制提高精度
    printf ( "%.8Lf", m / 23 );//输出保留8位小数
    return 0;
}
```


- 时间复杂度：${O\left( 1 \right)  }$ 
- 空间复杂度：${O\left( 1 \right)  }$ 


---

