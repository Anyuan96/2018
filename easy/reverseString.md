# 问题分析
请编写一个函数，其功能是将输入的字符串反转过来。

示例：

输入：s = "hello"
返回："olleh"
# 代码实现
```C
char* reverseString(char* s) {
    int slen = strlen(s);
    int i = 0;
    int j = slen-1;
    while(i < j){
        char temp = s[i];
        s[i++] = s[j];
        s[j--] = temp;
    }
    return s;
}
```
# 总结体会
这道题用双指针分别从前后对换字符就可以了