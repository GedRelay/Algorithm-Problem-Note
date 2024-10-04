---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1842 【USACO05NOV】 奶牛玩杂技
time: 2024-10-03 22:52
aliases: 
Description: 
tags: 
lastEdit: 2024-10-03-22:54
---

```toc
style: number
max_depth: 3
```

# 链接
[P1842 【USACO05NOV】 奶牛玩杂技](https://www.luogu.com.cn/problem/P1842) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202410032252270.png)


# 分类
#贪心 

# 思路
- 思路 1：
贪心

|  | 交换前 | 交换后 |
| :--: | :--: | :--: |
| ${i }$ | ${W_{1}  +\cdots +W_{i-1} -S_{i}  }$ | ${W_{1} +\cdots +W_{i-1}+W_{i+1}  -S_{i}  }$ |
| ${i+1 }$ | ${W_{1}  +\cdots +W_{i-1}+W_{i}  -S_{i+1}  }$ | ${W_{1} +\cdots +W_{i-1} -S_{i+1}  }$ |
化简：

|  | 交换前 | 交换后 |
| :--: | :--: | :--: |
| ${i }$ | ${ -S_{i}  }$ | ${W_{i+1}  -S_{i}  }$ |
| ${i+1 }$ | ${W_{i}  -S_{i+1}  }$ | ${ -S_{i+1}  }$ |
只要找到条件使得下式成立即可
$$
\max\{ -S_{i} ,W_{i} -S_{i+1}  \} >\max\{ W_{i+1} -S_{i} ,-S_{i+1}  \} 
$$
若左边取 ${-S_{i}  }$，则该大于号肯定不成立
若左边取 ${W_{i} -S_{i+1}  }$，则右式肯定取 ${W_{i+1} -S_{i}  }$ 
则有
$$
W_{i} -S_{i+1} >W_{i+1} -S_{i} 
$$
即
$$
W_{i} +S_{i} >W_{i+1} +S_{i+1} 
$$
即满足上式条件后，交换后结果会变得更优
最终方案是：按照 ${W_{i} +S_{i}  }$ 从小到大排序


```cpp
#include<bits/stdc++.h>
using namespace std;

int n;
struct cow{
    int W, S;
    bool operator < (const cow &a) const{
        return W + S < a.W + a.S;
    }
}a[50010];

int main(){
    cin >> n;
    for(int i = 0; i < n; i++){
        cin >> a[i].W >> a[i].S;
    }
    sort(a, a + n); // 按照W + S从小到大排序
    int ans = -0x3f3f3f3f, sum = 0;
    for(int i = 0; i < n; i++){
        ans = max(ans, sum - a[i].S);
        sum += a[i].W;
    }
    cout << ans << endl;
    return 0;
}
```


- 时间复杂度：${O\left( n\log n \right)  }$ 
- 空间复杂度：${O\left( n \right)  }$ 


---

