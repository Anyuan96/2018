# 问题分析

给定一个字符串，找到它的第一个不重复的字符，并返回它的索引。如果不存在，则返回 -1。

	案例:
	
	s = "leetcode"
	返回 0.
	
	s = "loveleetcode",
	返回 2.
# 代码实现
```C
int firstUniqChar(char* s) {
    int slen = strlen(s);
    if (slen == 0) return -1;
    if (slen == 1) return 0;
    int ss[26] = {0};
    for (int i = 0; i < slen; i++){
        ss[s[i] - 'a']++;
    }
    for (int i = 0; i < slen; i++){
        if (ss[s[i] - 'a'] == 1)
            return i;
    }
    return -1;
}
```
# 总结体会
先将给定字符串中的字母个数找出来，然后再找出第一个字母个数为1的字母就可以了。