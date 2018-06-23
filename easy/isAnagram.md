# 问题分析
给定两个字符串 s 和 t ，编写一个函数来判断 t 是否是 s 的一个字母异位词。

示例 1:

输入: s = "anagram", t = "nagaram"
输出: true
示例 2:

输入: s = "rat", t = "car"
输出: false
# 代码实现
```C++
class Solution {
public:
    bool isAnagram(string s, string t) {
       int temp[26] = {0};
        if (s.size() != t.size())
            return false;
        for (int i = 0; i < s.size(); i++){
            temp[s[i] - 'a']++;
        }
        for (int i = 0; i < t.size(); i++){
            temp[t[i] - 'a']--;
        }
        for (int i = 0; i < 26; i++){
            if (temp[i] != 0)
                return false;
        }
        return true;
    }
};
```
# 总结体会
本题只要判断两个字符串中每个字符的个数相同即可。