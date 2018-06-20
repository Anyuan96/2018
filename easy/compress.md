# 问题分析
给定一组字符，使用原地算法将其压缩。

压缩后的长度必须始终小于或等于原数组长度。

数组的每个元素应该是长度为1 的字符（不是 int 整数类型）。

在完成原地修改输入数组后，返回数组的新长度。
	输入：
	["a","a","b","b","c","c","c"]
	
	输出：
	返回6，输入数组的前6个字符应该是：["a","2","b","2","c","3"]
	
	说明：
	"aa"被"a2"替代。"bb"被"b2"替代。"ccc"被"c3"替代。
# 代码实现
```C++
class Solution {
public:
    int compress(vector<char>& chars) {
        int i = 0, j = 0, n = chars.size();  
        while (j < n) {  
            if (j == n - 1 || chars[j] != chars[j + 1]) {  
                chars[i++] = chars[j++];  
            } else {  
                chars[i++] = chars[j];  
                int k = j;  
                while (j < n && chars[j] == chars[k]) j++;  
                string s = to_string(j - k);  
                for (char c : s) chars[i++] = c;  
            }  
        }  
        return i;  
    }
};
```
# 总结体会
指针i指向修改内容的位置，指针j遍历整个chars，当下一个字符与当前字符不相同时，直接将字符赋值到i处，然后i指向下一个位置；若相同，k指向j所在的位置，j遍历剩下的字符串，相同的字符为j-k。