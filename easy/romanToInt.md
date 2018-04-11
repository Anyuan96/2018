# 问题分析
	给定一个罗马数字，将其转换成整数。
	返回的结果要求在 1 到 3999 的范围内。
# 代码实现
```C
int romanToInt(char* s) {
    int roman(char s){
        switch(s)
        {
            case 'I':
                return 1;
            case 'V':
                return 5;
            case 'X':
                return 10;
            case 'L':
                return 50;
            case 'C':
                return 100;
            case 'D':
                return 500;
            case 'M':
                return 1000;
            default:
                return 0;
        }
    }
    int length = strlen(s), ret =0;
    for(int i = 0; i < length; i++){
        ret = roman(*(s + i)) + ret;
        if(roman(*(s+i)) > roman(*(s+i-1)))
            ret -= 2*(roman(*(s+i-1)));
    }
    return ret;
}
```
# 总结体会
	1. 根据罗马数字与阿拉伯数字的对应关系，来确定字符与数字的对应关系。
	2. 要遵循罗马数字的一些规律。比如：IV = 4 IX = 9。
	3. 用switch...case...结构时要注意break和设置default。