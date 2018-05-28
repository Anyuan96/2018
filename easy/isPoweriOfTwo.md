# 问题分析

给定一个整数，写一个函数来判断它是否是 2 的幂次方。

	示例 1:
	
	输入: 1
	输出: true
	示例 2:
	
	输入: 16
	输出: true
	示例 3:
	
	输入: 218
	输出: false
# 代码实现
```C
bool isPowerOfTwo(int n) {
    if (n < 1) return false;
    int cnt = 0;
    for (int i = 0; i < 32; i++){
        if ( n&1 == 1) cnt++;
        n >>= 1;
    }
    return (cnt==1);
}
```
# 总结体会
2的幂的二进制数只有一个1，所以我们可以用位计算来做这个题。2的幂的汉明重量为1。