# 问题分析
给定一个仅包含大小写字母和空格' '的字符串，返回其最后一个单词的长度。

如果不存在最后一个单词，请返回0。

说明：一个单词是指由字母组成，但不包含任何空格的字符串。
# 代码实现
```C
int lengthOfLastWord(char* s) {
    int sLen = strlen(s);
    int count = 0;
    while (s[sLen - 1] == ' ')
        sLen--;
    for (int i = sLen -1; i > -1; i--){
        if (s[i] != ' '){
            count++;
        }
        else{
            break;
        }
    }
    return count;
}
```
# 总结体会
首先去除字符串末尾的' ', 然后从后向前遍历字符串直到遇到' ', 或者到第一个字母循环结束。