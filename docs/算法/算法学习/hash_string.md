# 字符串哈希
> 2023年2月28 


>参考《代码源初级课：字符串哈希》《acwing算法初级课：字符串哈希》
## 一、概念
---
将一段字符串转换为数字（即哈希值），通过比对数字（也就是哈希值）来快速确定两段字符串是否是相等的。

## 二、模板
---
字符串哈希有很多种写法，我了解到的模板大致有两种，一种是让它直接溢出，一种是所谓的多项式哈希即 `Polynomial Rolling`算法。

### 1. 多项式哈希
**哈希公式：**

+ $\operatorname{Hash}\left(s_{l, r}\right) = \left(a[r]-a[l-1] * b a s e^{r-l+1}\right) \bmod p$
  
+ $\operatorname{Hash}(s)=\left(\sum_{i=1}^{n} c_{i} * b a s e^{n-i}\right) \bmod p$




**初始化**
```cpp
int hash_a[10000], hash_b[10000];//记录两个字符串的哈希值
int c[10000];//记录base的初始化值，因为pow函数效率太低
const int p = 9999971;//取mod的数，本质上一个足够大的素数就行。
int base = 101;//base应该严格大于字符串内字母种类数，比如只有小写字母，应该保证最少大于26

```
两种输入方式
```cpp
/**
第一种输入方式，如果字符串内有空格。
**/
string a, b;
getline(cin, a);
getline(cin, b);
/**
第二种输入方式。
**/
char a[10000], b[10000];
scanf("%s%s", a+1, b+1);
```
将哈希值记录进数组中
```cpp
int len_a = strlen(a);
for(int i = 1; i <= len_a; i++ ){
    hash_a[i] = (hash_a[i-1]*base + a[i]-'a' - 1) % p;
}
```
记录字符串a中出现过多少次字符串b

```cpp
for(int i = 1; i <= lena; i++ ){
    if(( hash_a[i+lenb-1] - 1LL * hash_a[i - 1] * c[lenb] % p + p) % p == hash_b[lenb])
        ans++;
}
cout<<ans<<endl;
```
