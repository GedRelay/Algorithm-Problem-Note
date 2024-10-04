---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1219 【USACO1.5】 八皇后 Checker Challenge
time: 2024-10-01 00:46
aliases: 
Description: 
tags: 
lastEdit: 2024-10-01-20:03
---

```toc
style: number
max_depth: 3
```

# 链接
[P1219 【USACO1.5】 八皇后 Checker Challenge](https://www.luogu.com.cn/problem/P1219) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202410010046762.png)


# 分类
#搜索 

# 思路
- 思路 1：
深度优先搜索
使用数组记录某一列，某一主对角线，副对角线上是否有棋子
主对角线上的所有点 ${\left( x,y \right)  }$ 的 ${x-y }$ 都是一个定值，忘了防止越界所以加上 ${n }$ 作为键
副对角线上的所有点 ${\left( x,y \right)  }$ 的 ${x+y }$ 都是一个定值，因此将其作为键


```cpp
#include<iostream>
#include<vector>
using namespace std;

int n;
int ansnum = 0;
vector<int> path;
// unordered_set<int> st1, st2, st3; // 会超时
bool st1[30], st2[30], st3[30]; // 列，主对角线，副对角线

void dfs(int x){ // 当前为第x行
    if(x > n){
        ansnum++;
        if(ansnum <= 3){
            for(int i = 0; i < path.size(); i++){
                cout << path[i] << " ";
            }
            cout << endl;
        }
        return;
    }
    for(int y = 1; y <= n; y++){ // 枚举每一列
        if(!st1[y] && !st2[x - y + n] && !st3[x + y]){
            path.push_back(y);
            st1[y] = st2[x - y + n] = st3[x + y] = 1;
            dfs(x + 1);
            path.pop_back();
            st1[y] = st2[x - y + n] = st3[x + y] = 0;
        }
    }
}

int main(){
    cin >> n;
    dfs(1);
    cout << ansnum;
    return 0;
}
```


- 时间复杂度：
- 空间复杂度：


---

