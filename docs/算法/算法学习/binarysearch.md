# 二分算法

> 时间：2023-3-20

## 一、概述
 
---

二分是经典中的经典的查找算法。复杂度为`O(logN)`。我主要记录一下二分查找算法、以及二分答案。

## 二、二分查找

---

二分查找大致6种模板，b站UP主`董晓算法`总结得非常好了。
+ 找到最后一个`<=x`查找模板

  找到最后一个数
  如`1 2 2 2 3 4 5 6`，我们要找`2`的最后一个

```cpp
int l = 0,r = n-1;
while(l<r){
    int mid = (l+r)>>1;
    if(a[mid]<=x)l = mid;
    else r = mid-1;
}
ans = l;
```



```cpp
int l = 0-1,r = n+1;
while(l+1<r){
    int mid = (l+r)>>1;
    if(a[mid]<=x)l = mid;
    else r = mid;
}
ans = l;
```

+ 找到第一个`>=x`

  找到最后一个数
  如`1 2 2 2 3 4 5 6`，我们要找`2`的第一个


```cpp
int l = 0,r = n-1;
while(l<r){
    int mid = (l+r)>>1;
    if(a[mid]>=x)l = mid;
    else r = mid-1;
}
ans = l;
```

```cpp
int l = 0-1,r = n+1;
while(l+1<r){
    int mid = (l+r)>>1;
    if(a[mid]>=x)r = mid;
    else l = mid;
}
ans = r;
```
这两个模板不同的地方有三个。
+ 判断的边界不同,`while`循环出循环的条件是不同的。一个是
  
  ```c
    while(l<r)
  ```

  一个是：
  ```c
    while(l+1<r)
  ```

+ l、r初始值不同
  
  一个是：`l = 数组起点` 、`r = 数组终点`
  另一个是：`l = 数组起点-1`、`r = 数组终点+1`

+ mid值的更新不同


这里我现在使用的是`while`循环从`l+1<r`退出的模板。因为首先更简单、其次做题时发现这个模板好像我写的老容易出错。

## 二分答案

---

**使用条件**

+ 答案有上下边界

+ 条件是有单调性的

+ 暴力循环复杂度过大

**使用模板**

```c
bool check(int mid){
    if(mid判断条件)
        return true;
    else
        return false;
}


int main(){
    while(l+1<r){
        int mid = (l+r)>>1;
        if(check(mid))l = mid;
        else r = mid;
    }
    ans = l;
}
```

两道二分答案很类似的经典题：

[晾衣服](https://ac.nowcoder.com/acm/problem/235254)

[跳石头](https://ac.nowcoder.com/acm/problem/16462)