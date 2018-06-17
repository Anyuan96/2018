# 问题分析
给定两个字符串形式的非负整数 num1 和num2 ，计算它们的和。

注意：

	1. num1 和num2 的长度都小于 5100.
	2. num1 和num2 都只包含数字 0-9.
	3. num1 和num2 都不包含任何前导零。
	4. 你不能使用任何內建 BigInteger 库，也不能直接将输入的字符串转换为整数形式。
# 代码实现
```C++
class Solution {
public:
    string addStrings(string num1, string num2) {
       string num;
        int length1 = num1.length();
        int length2 = num2.length();
        int carry = 0;

        for (int i = length1 - 1, j = length2 - 1; i >= 0 || j >= 0; i--, j--)
        {
            int temp = 0;
            if (i >= 0)
            {
                temp += num1[i] - '0';
            }
            if (j >= 0)
            {
                temp += num2[j] - '0';
            }
            if (carry)
            {
                temp++;
            }
            carry = temp / 10;
            temp = temp % 10;
            num = char(temp + '0') + num;
        }
        if (carry)
        {
            num = char(carry + '0') + num;
        }
        return num;
    } 
};
```
# 总结体会
从字符串的最低位开始加，并用carry标识进位。