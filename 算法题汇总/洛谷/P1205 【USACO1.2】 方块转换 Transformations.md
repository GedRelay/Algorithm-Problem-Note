---
author: GedRelay
Email: gedrelay@stu.jnu.edu.cn
title: P1205 【USACO1.2】 方块转换 Transformations
time: 2024-10-01 00:26
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
[P1205 【USACO1.2】 方块转换 Transformations](https://www.luogu.com.cn/problem/P1205) 

# 题目
![image.png](https://ged-pic-bed.oss-cn-guangzhou.aliyuncs.com/img/202410010027963.png)


# 分类
#模拟 #数组构造 

# 思路
- 思路 1：
实现将数组顺时针旋转 90 度以及将数组水平翻转这两个操作
其他所有操作可以由这两个操作组合而来


```cpp
#include<iostream>
using namespace std;

int n;
char mp1[12][12], mp2[12][12];

// 顺时针旋转90度
void rotate90(char mp[12][12]){
    char tmp[12][12];
    for(int i = 0, y = n - 1; i < n; i++, y--){
        for(int j = 0, x = 0; j < n; j++, x++){
            tmp[x][y] = mp[i][j];
        }
    }
    for(int i = 0; i < n; i++){
        for(int j = 0; j < n; j++){
            mp[i][j] = tmp[i][j];
        }
    }
}

// 水平翻转
void flip(char mp[12][12]){
    char tmp[12][12];
    for(int i = 0, x = 0; i < n; i++, x++){
        for(int j = 0, y = n - 1; j < n; j++, y--){
            tmp[x][y] = mp[i][j];
        }
    }
    for(int i = 0; i < n; i++){
        for(int j = 0; j < n; j++){
            mp[i][j] = tmp[i][j];
        }
    }
}


bool same(){
    for(int i = 0; i < n; i++){
        for(int j = 0; j < n; j++){
            if(mp1[i][j] != mp2[i][j]){
                return false;
            }
        }
    }
    return true;
}

int main(){
    cin >> n;
    // 输入原始矩阵
    for(int i = 0; i < n; i++){
        for(int j = 0; j < n; j++){
            cin >> mp1[i][j];
        }
    }
    // 输入目标矩阵
    for(int i = 0; i < n; i++){
        for(int j = 0; j < n; j++){
            cin >> mp2[i][j];
        }
    }
    // 旋转1次
    rotate90(mp1);
    if(same()){
        cout << "1" << endl;
        return 0;
    }
    // 旋转2次
    rotate90(mp1);
    if(same()){
        cout << "2" << endl;
        return 0;
    }
    // 旋转3次
    rotate90(mp1);
    if(same()){
        cout << "3" << endl;
        return 0;
    }
    // 恢复原始矩阵, 然后水平翻转
    rotate90(mp1);
    flip(mp1);
    if(same()){
        cout << "4" << endl;
        return 0;
    }
    // 旋转1次
    rotate90(mp1);
    if(same()){
        cout << "5" << endl;
        return 0;
    }
    // 旋转2次
    rotate90(mp1);
    if(same()){
        cout << "5" << endl;
        return 0;
    }
    // 旋转3次
    rotate90(mp1);
    if(same()){
        cout << "5" << endl;
        return 0;
    }
    // 恢复原始矩阵
    rotate90(mp1);
    flip(mp1);
    if(same()){
        cout << "6" << endl;
        return 0;
    }
    cout << "7" << endl;
    return 0;
}
```


- 时间复杂度：${O\left( n^{2}  \right)  }$ 
- 空间复杂度：${O\left( n^{2}  \right)  }$ 


---

