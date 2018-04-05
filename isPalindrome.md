# 问题分析
  判断一个整数是否是回文数。不能使用辅助空间。
  
# 代码实现
## 错误示例
  ```
  class Solution:
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        if x < 0:
            return False
        else:
            digit = 1
            while x // digit >= 10:
                digit *= 10
            while x >= 10:
                left = x // digit
                right = x % 10
                if left != right:
                    return False
                else:
                    x = (x % digit) // 10
                    digit /= 100
            else:
                return True
    ```
    
## 正确示例
  ```
  class Solution:
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        if x < 0:
            return False
        else:
            return str(x) == str(x)[::-1]
  ```
# 总结体会
  1. 在错误示例中，如果高位遇到0，则会错误
  2. Python中字符操作非常灵活，str[::-1]则是颠倒字符串
  3. 注意回文数是正整数
