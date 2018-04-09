# 问题分析
	判断一个整数是否是回文数。不能使用辅助空间。
# 代码实现
```C
bool isPalindrome(int x) {
    int xx = x;
    if(x < 0){
        return false;
    }
    if(x < 10){
        return true;
    }
    int ret = 0;
    while(xx){
        ret = ret*10 + xx%10;
        xx /=10;
    }
    if( ret == x){
        return true;
    }
    else{
     return false;   
    }
    
}
```

# 总结体会
	1. 回文数是正整数和0
	2. C语言中的bool类型：true和false