---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: LCP 06. 拿硬币
time: 2024-09-16 15:02
aliases: 
Description: 
tags: 
lastEdit: 2024-09-16-15:05
---

```toc
style: number
max_depth: 3
```

# 链接
[LCP 06. 拿硬币](https://leetcode.cn/problems/na-ying-bi/) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409161504141.png)


# 分类
#贪心

# 思路
- 思路 1：
贪心
每次都拿 $2$ 个金币，直到都拿完 


```cpp
class Solution {
public:
    int minCount(vector<int>& coins) {
        int ans = 0;
        for(int& coin : coins){
            ans += (coin + 1) >> 1;
        }
        return ans;
    }
};
```


- 时间复杂度：${O\left( n \right)  }$ 
- 空间复杂度：${O\left( 1 \right)  }$ 


---

