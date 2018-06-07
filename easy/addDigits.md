# 问题分析
给定一个非负整数 num，反复将各个位上的数字相加，直到结果为一位数。

	示例:
	
	输入: 38
	输出: 2 
	解释: 各位相加的过程为：3 + 8 = 11, 1 + 1 = 2。 由于 2 是一位数，所以返回 2。
# 代码实现
```C
int addDigits(int num) {
    while(num/10){
        num = num/10 + num%10;
    }
    return num;
}
```
# 总结体会
这道题的逻辑很简单，就是一直循环各位上相加，直到结果是个一位数为止。