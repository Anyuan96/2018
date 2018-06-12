# 问题分析
给定一个赎金信 (ransom) 字符串和一个杂志(magazine)字符串，判断第一个字符串ransom能不能由第二个字符串magazines里面的字符构成。如果可以构成，返回 true ；否则返回 false。

(题目说明：为了不暴露赎金信字迹，要从杂志上搜索各个需要的字母，组成单词来表达意思。)

	注意：
	
	你可以假设两个字符串均只含有小写字母。
	
	canConstruct("a", "b") -> false
	canConstruct("aa", "ab") -> false
	canConstruct("aa", "aab") -> true
# 代码实现
```C
bool canConstruct(char* ransomNote, char* magazine) {
    int rlen = strlen(ransomNote);
    int mlen = strlen(magazine);
    if (rlen > mlen) return false;
    if (rlen == 0 && mlen == 0) return true;
    if (rlen == 0) return true;
    int *r = (int*)calloc(26,sizeof(int));
    int *m = (int*)calloc(26,sizeof(int));;
    for (int i = 0; i < rlen; i++){
        r[ransomNote[i] - 'a']++;
    }
    for (int i = 0; i < mlen; i++){
        m[magazine[i] - 'a']++;
    }
    for (int i = 0; i < 26; i++){
        if (r[i] > m[i]) return false;
    }
    return true;
}
```
# 总结体会
这道题的思路是看看magazine里的字母数量是否多于ransomNote使用的相应字母的个数。