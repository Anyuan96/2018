# 问题分析
不使用运算符 + 和-，计算两整数a 、b之和。

	示例：
	若 a = 1 ，b = 2，返回 3。
# 代码实现
```C
int getSum(int a, int b) {
        if(b == 0) return a;
        int sum = a ^ b;      
        int carry = (a & b) << 1;
        return getSum(sum, carry);  
}
```
# 总结体会
如果不考虑进位的话，结果应该是sum = a ^ b，而加法计算是考虑进位的。当两个数对应位置同为一时，才可能产生进位，也就是a&b，由于是进位，所以得到的carry = a & b 要向左移一位。然后再将和sum和进位carry相加。当carry = 0 时就是最终的结果了。