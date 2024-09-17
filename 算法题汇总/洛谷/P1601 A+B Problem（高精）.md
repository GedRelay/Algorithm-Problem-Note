---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1601 A+B Problem（高精）
time: 2024-09-17 23:14
aliases: 
Description: 
tags: 
lastEdit: 2024-09-17-23:20
---

```toc
style: number
max_depth: 3
```

# 链接
[P1601 A+B Problem（高精）](https://www.luogu.com.cn/problem/P1601) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409172314025.png)


# 分类
#高精度 

# 思路
- 思路 1：
高精度加法


```cpp
#include<iostream>
#include<vector>
using namespace std;

vector<int> input(){
    string s;
    cin >> s;
    vector<int> A;
    for(int i = s.size() - 1; i >= 0; i--){
        A.push_back(s[i] - '0');
    }
    return A;
}

void print(vector<int> A){
    for(int i = A.size() - 1; i >= 0; i--){
        cout << A[i];
    }
}

vector<int> add(vector<int> &A, vector<int> &B){
    vector<int> C;
    int r = 0;
    for(int i = 0; i < A.size() || i < B.size(); i++){
        if(i < A.size()) r += A[i];
        if(i < B.size()) r += B[i];
        C.push_back(r % 10);
        r /= 10;
    }
    if(r) C.push_back(r);
    return C;
}

int main()
{
    vector<int> A = input();
    vector<int> B = input();
    vector<int> C = add(A, B);
    print(C);
	return 0;
}
```


- 时间复杂度：${O\left( \log n \right)  }$ 
- 空间复杂度：${O\left( \log n \right)  }$ 


---

