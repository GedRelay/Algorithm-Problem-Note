---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1480 A÷B Problem
time: 2024-09-17 22:10
aliases: 
Description: 
tags: 
lastEdit: 2024-09-17-22:20
---

```toc
style: number
max_depth: 3
```

# 链接
[P1480 A÷B Problem](https://www.luogu.com.cn/problem/P1480) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202409172211385.png)


# 分类
#高精度 

# 思路
- 思路 1：
高精度除以低精度


```cpp
#include<iostream>
#include<algorithm>
#include<vector>
using namespace std;

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

vector<int> div(vector<int>& A, int& b, long long &r){
	vector<int>C;
	r = 0; // 记录上一位的余数
	for (int i = A.size() - 1; i >= 0; i--){
		r = r * 10 + A[i];
		C.push_back(r / b);
		r %= b;
	}
	reverse(C.begin(), C.end()); // 记得翻转回来
	while (C.size() > 1 && C.back() == 0) C.pop_back();
	return C;
}

int main(){
    vector<int> A = read();
    int b;
    cin >> b;
    long long r = 0;
    vector<int> C = div(A, b, r);
    print(C);
    return 0;
}

```


- 时间复杂度：${O\left( \log n \right)  }$ 
- 空间复杂度：${O\left( \log n \right)  }$ 


---

