#　问题分析
编写一个函数，以字符串作为输入，反转该字符串中的元音字母。

	示例 1：
	给定 s = "hello", 返回 "holle".
	
	示例 2：
	给定 s = "leetcode", 返回 "leotcede".
# 代码实现
```C
char* reverseVowels(char* s) {
    bool isVowels(char a){
        char Vowels[] = "aeiouAEIOU";
        for (int i = 0; i < strlen(Vowels); i++){
            if (a == Vowels[i]) 
                return true;
        }
        return false;
    }
    int i = 0;
    int j = strlen(s) - 1;
    while(i < j){
        if (!isVowels(s[i])) i++;
        if (!isVowels(s[j])) j--;
        if (isVowels(s[i]) && isVowels(s[j])){
            char temp = s[i];
            s[i] = s[j];
            s[j] = temp;
            i++;
            j--;
        }
    }
    return s;
}
```
# 总结体会
这道题用到了双指针，当两个指针同时遇到元音字母时，交换这两个字母。