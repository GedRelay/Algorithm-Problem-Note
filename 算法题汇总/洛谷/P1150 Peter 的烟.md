---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1150 Peter 的烟
time: 2024-09-16 15:35
aliases: 
Description: 
tags: 
lastEdit: 2024-09-16-15:36
---

```toc
style: number
max_depth: 3
```

# 链接
[P1150 Peter 的烟](https://www.luogu.com.cn/problem/P1150) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409161535383.png)


# 分类
#模拟 

# 思路
- 思路 1：
按照题目要求模拟即可


```cpp
#include <iostream>
using namespace std;
int main()
{
    int n, k, ans = 0; //手里的烟头数，k，吸的烟总根数
    cin >> n >> k;
    ans += n;
    while (n >= k){ //能换
        ans += n / k; //能换n/k根烟
        n = n % k + n / k; //换完还剩n%k个烟头
    }
    cout << ans;
    return 0;
}
```


- 时间复杂度：${O\left( 1 \right)  }$ 
- 空间复杂度：${O\left( 1 \right)  }$ 


---

