---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P4391【BalticOI 2009】Radio Transmission 无线传输
time: 2025-04-27 12:06
aliases: 
Description: 
tags: 
lastEdit: 2025-04-27-12:08
---

```toc
style: number
max_depth: 3
```

# 链接
[P4391【BalticOI 2009】Radio Transmission 无线传输](https://www.luogu.com.cn/problem/P4391) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202504271206793.png)


# 分类
#KMP 

# 思路
- 思路 1：
利用 next 数组求循环节
`循环节长度 = s.size() - next[s.size() - 1]` 

```cpp
#include <iostream>
using namespace std;

int n;
int nxt[1000010];

int main(){
    string s;
    cin >> n >> s;
	// 求next数组
    for(int i = 1, j = 0; i < n; i++){
        while(j != 0 && s[i] != s[j]) j = nxt[j - 1];
        if(s[i] == s[j]) j++;
        nxt[i] = j;
    }
    
    cout << n - nxt[n - 1];
    return 0;
}
```


- 时间复杂度：${O\left( n \right)  }$ 
- 空间复杂度：${O\left( n \right)  }$ 


---

