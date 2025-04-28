---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P4018 Roy&October之取石子
time: 2025-04-24 00:52
aliases: 
Description: 
tags: 
lastEdit: 2025-04-24-01:22
---

```toc
style: number
max_depth: 3
```

# 链接
[P4018 Roy&October之取石子](https://www.luogu.com.cn/problem/P4018) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202504240052746.png)


# 分类
#博弈论 

# 思路
- 思路 1：
${n\%6\neq 0 }$ 先手必胜

```cpp
#include <iostream>
using namespace std;

int main(){
    int t, n;
    cin >> t;
    while(t--){
        cin >> n;
        if(n % 6 != 0) cout << "October wins!\n";
        else cout << "Roy wins!\n";
    }
    return 0;
}
```


- 时间复杂度：${O\left( 1 \right)  }$ 
- 空间复杂度：${O\left( 1 \right)  }$ 


---

