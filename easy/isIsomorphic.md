# 问题分析
给定两个字符串 s 和 t，判断它们是否是同构的。

如果 s 中的字符可以被替换得到 t ，那么这两个字符串是同构的。

所有出现的字符都必须用另一个字符替换，同时保留字符的顺序。两个字符不能映射到同一个字符上，但字符可以映射自己本身。

示例 1:

输入: s = "egg", t = "add"

输出: true

示例 2:

输入: s = "foo", t = "bar"

输出: false

示例 3:

输入: s = "paper", t = "title"

输出: true
# 代码实现
```C++
class Solution {
public:
    bool isIsomorphic(string s, string t) {
        if (s.length() != t.length())
            return false;
        if (transferStr(s) == transferStr(t))
            return true;
        return false;
    }
    string transferStr (string s){
        char table[128] = {0};
        char sub = '0';
        for (int i = 0; i < s.length(); i++){
            char c = s.at(i);
            if (table[c] == 0){
                table[c] = sub++;
            }
            s[i] = table[c];
        }
     return s;       
    }
};
```
# 总结体会
题目要求判断一个字符串是否能由另一个字符串转换得来，因此分别将两个字符串中的字符分别进行替换，看最后得到的新字符串是否相同。