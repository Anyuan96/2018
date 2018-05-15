# 问题分析
给定一个Excel表格中的列名称，返回其相应的列序号。

例如，

    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
    ...
	示例 1:
	
	输入: "A"
	输出: 1
	示例 2:
	
	输入: "AB"
	输出: 28
	示例 3:
	
	输入: "ZY"
	输出: 701
# 代码实现
```C
int titleToNumber(char* s) {
    int slen = strlen(s);
    int ret = 0;
    for (int i = 0; i < slen; i++){
        ret = ret * 26 + *(s+i) - 'A' +1;
    }
    return ret;
}
```
# 总结体会
这道题是与leetcode168对应的题，是26进制转换问题，要注意，A—Z对应于1—26而不是0-25，所以要在结果后面+1.