# 问题分析
给定一个正整数 num，编写一个函数，如果 num 是一个完全平方数，则返回 True，否则返回 False。

注意：不要使用任何内置的库函数，如  sqrt。

	示例 1：
	
	输入： 16
	
	输出： True
	 
	
	示例 2：
	
	输入： 14
	
	输出： False
# 代码实现
```C
bool isPerfectSquare(int num) {
    if (num <= 1) return true;
    for (int i = 2; i <= num/2; i++){
        if (num == i * i) return true;
    }
    return false;
}
```
# 总结体会
这道题的逻辑比较简单，就是求i²=num，为了减少运行时间，可以将最后的i设置为num/2。