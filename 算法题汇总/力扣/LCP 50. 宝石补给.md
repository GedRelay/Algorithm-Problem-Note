---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: LCP 50. 宝石补给
time: 2024-09-16 15:05
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
[LCP 50. 宝石补给](https://leetcode.cn/problems/WHnhjV/) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409161506752.png)


# 分类
#模拟 

# 思路
- 思路 1：
按照题目模拟即可


```cpp
class Solution {
public:
    int giveGem(vector<int>& gem, vector<vector<int>>& operations) {
        int n = gem.size();
        for(auto& op : operations){
            int x = op[0], y = op[1];
            int gemNum = gem[x] / 2;
            gem[x] -= gemNum;
            gem[y] += gemNum;
        }
        int maxx = gem[0], minn = gem[0];
        for(int i = 0; i < gem.size(); i++){
            maxx = max(maxx, gem[i]);
            minn = min(minn, gem[i]);
        }
        return maxx - minn;
    }
};
```


- 时间复杂度：${O\left( n \right)  }$ 
- 空间复杂度：${O\left( 1 \right)  }$ 


---

