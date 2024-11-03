---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: LCP 74. 最强祝福力场
time: 2024-10-31 12:47
aliases: 
Description: 
tags: 
lastEdit: 2024-10-31-12:55
---

```toc
style: number
max_depth: 3
```

# 链接
[LCP 74. 最强祝福力场](https://leetcode.cn/problems/xepqZ5/) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202410311248869.png)
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202410311248373.png)


# 分类
#差分/二维差分 #离散化 

# 思路
- 思路 1：
离散化 + 二维差分
原数据会出现 ${0.5 }$ 的小数点，通过对中心点乘以 ${2 }$ 再加上或减去半径 ${r }$ 就可以将整个坐标点扩大一倍以消除小数
$$
\begin{align} x_{1} =2\times x_{c} -r\\y_{1} =2\times y_{c} -r\\x_{2}= 2\times x_{c} +r\\y_{2} =2\times y_{c} +r \end{align} 
$$
第一步转换后数值范围可能很大，但是数据量很小，因此可以通过离散化将数据映射到小范围，之后再进行二维差分

```cpp
class Solution {
public:
    vector<vector<int>> d; // 差分数组

    int fieldOfGreatestBlessing(vector<vector<int>>& forceField) {
        vector<long long> xs, ys; // 离散化数组
        for(auto &f : forceField){
            xs.push_back(f[0] * 2ll + f[2]);
            xs.push_back(f[0] * 2ll - f[2]);
            ys.push_back(f[1] * 2ll + f[2]);
            ys.push_back(f[1] * 2ll - f[2]);
        }
        sort(xs.begin(), xs.end());
        xs.erase(unique(xs.begin(), xs.end()), xs.end());
        sort(ys.begin(), ys.end());
        ys.erase(unique(ys.begin(), ys.end()), ys.end());
 
        d.resize(xs.size() + 2, vector<int>(ys.size() + 2, 0)); // 差分数组

        for(auto &f : forceField){
            int x1 = rank(f[0] * 2ll - f[2], xs);
            int y1 = rank(f[1] * 2ll - f[2], ys);
            int x2 = rank(f[0] * 2ll + f[2], xs);
            int y2 = rank(f[1] * 2ll + f[2], ys);
            add(x1, y1, x2, y2, 1);
        }

        int ans = 0;
        for(int i = 1; i <= xs.size(); i++){ // 还原差分数组
            for(int j = 1; j <= ys.size(); j++){
                d[i][j] += d[i][j - 1] + d[i - 1][j] - d[i - 1][j - 1];
                ans = max(ans, d[i][j]);
            }
        }
        return ans;
    }

    int rank(long long x, vector<long long> &d){
        int l = 0, r = d.size() - 1;
        while(l < r){
            int mid = l + r >> 1;
            if(d[mid] >= x) r = mid;
            else l = mid + 1;
        }
        return l + 1;
    }

    void add(int x1, int y1, int x2, int y2, int x){
        d[x1][y1] += x;
        d[x2 + 1][y1] -=x;
        d[x1][y2 + 1] -= x;
        d[x2 + 1][y2 + 1] += x;
    }
};
```


- 时间复杂度：${O\left( n^{2}  \right)  }$ 
- 空间复杂度：${O\left( n^{2}  \right)  }$ 


---

