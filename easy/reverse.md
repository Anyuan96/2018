# 问题分析
	给定一个范围为 32 位 int 的整数，将其颠倒。
	假设我们的环境只能处理 32 位 int 范围内的整数。
	根据这个假设，如果颠倒后的结果超过这个范围，则返回 0。
# 代码实现
```C
int reverse(int x) {
    long x_new = abs(x);
    long ret = 0;
    long int_max = pow(2,31) - 1;
    long int_min = -pow(2,31);
    while(x_new){
	ret = ret*10 + x_new%10;
	x_new /= 10;
    }
    if(x < 0){
	ret = (-1)*ret;
    }
    if(ret > int_min & ret<int_max){
	return ret;
    }
    return 0;
}
```
# 总结体会
	1. 计算幂要用pow(x,y)，不能用^
	2. 要判断翻转后是否溢出，最大值为2^31-1，最小值为-2^31
	3. 因为翻转后的数可能会大于int的范围，所以返回值ret应该用long定义
