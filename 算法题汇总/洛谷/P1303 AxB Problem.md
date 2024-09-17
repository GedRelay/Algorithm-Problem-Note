---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1303 AxB Problem
time: 2024-09-17 21:06
aliases: 
Description: 
tags: 
lastEdit: 2024-09-17-21:14
---

```toc
style: number
max_depth: 3
```

# 链接
[P1303 AxB Problem](https://www.luogu.com.cn/problem/P1303) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409172106833.png)


# 分类
#高精度 

# 思路
- 思路 1：
高精度乘以高精度


```cpp
#include<iostream>
#include<algorithm>
#include<vector>
using namespace std;
typedef long long LL;

vector<int> read(){
    vector<int> A;
    string x;
    cin >> x;
    for(int i = x.size() - 1; i >= 0; i--){
        A.push_back(x[i] - '0');
    }
    return A;
}

void print(vector<int>& A){
    for(int i = A.size() - 1; i >= 0; i--){
        cout << A[i];
    }
    cout << endl;
}

vector<int> mul(vector<int> &A, vector<int> &B) {
    vector<int> C(A.size() + B.size());
    for (int i = 0; i < A.size(); i++) {
        for (int j = 0; j < B.size(); j++) {
            C[i + j] += A[i] * B[j];
        }
    }

    for (int i = 0; i < C.size(); i++) {
        C[i + 1] += C[i] / 10;
        C[i] %= 10;
    }
    
    return C;
}

int main(){
    vector<int> A = read();
    vector<int> B = read();
    vector<int> C = mul(A, B);
    print(C);
    return 0;
}

```


- 时间复杂度：${O\left( \log ^{2} n \right)  }$ 
- 空间复杂度：${O\left( \log n \right)  }$ 


---

