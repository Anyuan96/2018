# 问题分析：
    给定一个整数数列，找出其中和为特定值的那两个数。
    你可以假设每个输入都只会有一种答案，同样的元素不能被重用。

# 代码实现：
  
  ```python
      class Solution:
        def twoSum(self, nums, target):
            """
            :type nums: List[int]
            :type target: int
            :rtype: List[int]
            """
            exit_flag = False
            for i in range(len(nums)):
                for j in range(i + 1, len(nums)):
                    if target == nums[i] + nums[j]:
                        exit_flag = True
                        break
                if exit_flag:
                    break
            return [i,j]
  ```
  
# 总结体会：
  1. 由于同样的元素不能被重用，故j的起始位置应该是j+1
  2. 运用了两层循环，故要设置一个exit_flag来退出两层循环
