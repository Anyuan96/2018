# 问题分析
给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。

说明：本题中，我们将空字符串定义为有效的回文串。

示例 1:

输入: "A man, a plan, a canal: Panama"
输出: true
示例 2:

输入: "race a car"
输出: false
# 代码实现
```C
bool isPalindrome(char* s) {
    if (strlen(s) == 0) return true;
    int slen = strlen(s);
    char *slow = (char*)malloc(slen*sizeof(char));
    int j = 0;
    for(int i = 0; i < slen; i++){
        if (s[i] >= 'a' && s[i] <= 'z' || s[i] >= 'A' && s[i] <= 'Z'|| s[i] >= '0' && s[i] <='9'){
            slow[j++] = s[i];
        }
    }
    slow[j] = '\0';
    int slowlen = strlen(slow);
    for (int i = 0; i < slowlen; i++){
        slow[i] = tolower(slow[i]);
    }
    for (int i = 0; i < slowlen/2; i++){
        if (slow[i] != slow[slowlen - 1 - i])
            return false;
    }
    return true;
}
```
# 总结体会
解这道题的思路是现将字符串中的非英文数字字符删除，然后将同一转换为小写字母，然后对字符串里的字符进行逐一比较。