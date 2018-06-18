# 问题分析
在无限的整数序列 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ...中找到第 n 个数字。

注意:
n 是正数且在32为整形范围内 ( n < 231)。

	示例 1:
	
	输入:
	3
	
	输出:
	3
	示例 2:
	
	输入:
	11
	
	输出:
	0
	
	说明:
	第11个数字在序列 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ... 里是0，它是10的一部分。
# 代码实现
```C++
class Solution {
public:
    int findNthDigit(int n) {
        long digit = 1, ith = 1, base = 9;  
        while(n > base*digit)  
        {  
            n -= base*(digit++);  
            ith += base;  
            base *= 10;  
        }  
        return to_string(ith+(n-1)/digit)[(n-1)%digit]-'0';     
    }
};
```
# 总结体会
先判断第n个数字是落在几位数字的范围，然后再判断是落在第几个数字的第几位。
