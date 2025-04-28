---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P4824【USACO15FEB】Censoring S
time: 2025-04-27 13:01
aliases: 
Description: 
tags: 
lastEdit: 2025-04-27-13:04
---

```toc
style: number
max_depth: 3
```

# 链接
[P4824【USACO15FEB】Censoring S](https://www.luogu.com.cn/problem/P4824) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202504271301656.png)


# 分类
#栈 #KMP 

# 思路
- 思路 1：
栈 + KMP
对于每个 ${i }$，在栈中记录与之匹配的 ${j }$，如果不匹配，则存入 ${-1 }$，当完全匹配时，栈中弹出字符串 ${p }$ 长度的信息，并将 ${j }$ 指针转到栈顶存储的位置 ${+1 }$ 


```cpp
#include <iostream>
#include <algorithm>
#include <vector>
#include <stack>
using namespace std;

int nxt[1000010];

int main(){
    string s, p;
    cin >> s >> p;
    
    // 求p的next数组
    for(int i = 1, j = 0; i < p.size(); i++){
        while(j != 0 && p[i] != p[j]) j = nxt[j - 1];
        if(p[i] == p[j]) j++;
        nxt[i] = j;
    }
    
    stack<pair<int, int>> stk;  // 已匹配成功的{i, j}
    
    for(int i = 0, j = 0; i < s.size(); i++){
        while(j != 0 && s[i] != p[j]) j = nxt[j - 1];
        if(s[i] == p[j]){
            stk.emplace(i, j);
            j++;
        }
        else stk.emplace(i, -1);
        if(j == p.size()){
            for(int k = 0; k < j; k++) stk.pop();
            j = (stk.empty() ? 0 : stk.top().second + 1);
        }
    }
    
    vector<char> ans;
    while(!stk.empty()){
        ans.push_back(s[stk.top().first]);
        stk.pop();
    }
    for(int i = ans.size() - 1; i >= 0; i--){
        cout << ans[i];
    }
    return 0;
}
```


- 时间复杂度：${O\left( n+m \right)  }$ 
- 空间复杂度：${O\left( m \right)  }$ 


---

