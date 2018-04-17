# 问题分析
	给定一个 haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从0开始)。
	如果不存在，则返回  -1。
# 代码实现
```C
int strStr(char* haystack, char* needle) {
    int haystackSize = strlen(haystack);
    int needleSize = strlen(needle);
    if (needleSize == 0) return 0;
    if (haystackSize < needleSize) return -1;
    int i = 0;
    int j = 0;
    while (true){
        if (haystack[i + j] == needle[j]){
            j++;
            if (j == needleSize) break;
        }
        else{
            j = 0;
            i++;
            if (i + needleSize > haystackSize){
                i = -1; 
                break;
            }
                
        }
    }
    return i;
}
```
# 总结体会
	1. 当needle为空字符串时，应当返回0。
	2. 如果当前起始位置加上needle字符串的长度，超过了原字符串的索引范围，则haystack里不可能包含needle字符串，直接返回-1，
	若继续进行循环可能会导致超时。
