# 问题分析
实现 int sqrt(int x) 函数。

计算并返回 x 的平方根，其中 x 是非负整数。

由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。
# 代码实现
```C
int mySqrt(int x) {
    if (x ==0 | x == 1) return x;
    long i = 1;
    while ( x >= i*i){
        i++;
    }
    return i-1;
}
```
# 总结体会
 要将i定义为long，否则可能会数据溢出。