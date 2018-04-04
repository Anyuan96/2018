# 问题分析： 
  给定一个范围为 32 位 int 的整数，将其颠倒。
  注意：如果颠倒后的结果超过这个范围，则返回 0。

# 代码实现：

···
  class Solution:
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        int_32bit_max_positive = 2**31 - 1
        int_32bit_max_negative = -(2)**31
        if  -10 < x < 10:
            return x
        else:
            x_str = str(abs(x))
            new = ''
            for i in range(len(x_str)):
                new = new + x_str[-(i+1)]
            x_reverse = int(new)
            if x < 0:
                x_reverse = -x_reverse
            if int_32bit_max_negative < x < int_32bit_max_positive:
                return x_reverse
            else:
                return 0
  ···

# 总结体会：
  1. 32位整数范围为 -2^31 ~ 2^31 -1
  2. 若只有一位数，则直接输出
  3. 若反转后超出范围，则输出0
