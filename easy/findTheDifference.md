 # 问题分析

给定两个字符串 s 和 t，它们只包含小写字母。

字符串 t 由字符串 s 随机重排，然后在随机位置添加一个字母。

请找出在 t 中被添加的字母。

 

	示例:
	
	输入：
	s = "abcd"
	t = "abcde"
	
	输出：
	e
	
	解释：
	'e' 是那个被添加的字母。
# 代码实现
```C
char findTheDifference(char* s, char* t) {
    if (strlen(s) == 0) return t[0];
    int slen = strlen(s);
    int tlen = strlen(t);
    int temp[26] = {0};
    for (int i = 0; i < slen; i++){
        temp[s[i] - 'a']++;
    }
    for (int i = 0; i < tlen; i++){
        temp[t[i] - 'a']--;
    }
    int ret = 0;
    for (int i = 0; i < 26; i++){
        if(temp[i] != 0){
        ret = i;
        break;
        }
    }
    return (char)(ret + 'a');
}
```
# 总结体会
本题就是要对比两个字符串中的字母的个数，因为只多一个字母，因此只需要找到两个字符串差1的那个字母。