# 问题分析
给定一个整数数组和一个整数 k，判断数组中是否存在两个不同的索引 i 和 j，使得 nums [i] = nums [j]，并且 i 和 j 的差的绝对值最大为 k。

	示例 1:
	
	输入: [1,2,3,1], k = 3
	输出: true
	示例 2:
	
	输入: [1,0,1,1], k = 1
	输出: true
	示例 3:
	
	输入: [1,2,1], k = 0
	输出: false
# 代码实现
```C
bool containsNearbyDuplicate(int* nums, int numsSize, int k) {
    if (numsSize == 0 || k == 0) return  false;
    for (int i = 0; i < numsSize; i++){
        for (int j = i + 1; j < numsSize; j++){
            if (nums[i] == nums[j] && j - i <= k)
                return true;
        }
    }
    return false;
}
```
# 总结体会
这道题和上一题的思路一样，只是要多加一个判断条件，使两个数的差不大于k