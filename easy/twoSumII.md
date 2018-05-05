# 问题分析
给定一个已按照升序排列 的有序数组，找到两个数使得它们相加之和等于目标数。

函数应该返回这两个下标值 index1 和 index2，其中 index1 必须小于 index2。

说明:

- 返回的下标值（index1 和 index2）不是从零开始的。
- 你可以假设每个输入只对应唯一的答案，而且你不可以重复使用相同的元素。
	
		示例:
		
		输入: numbers = [2, 7, 11, 15], target = 9
		输出: [1,2]
		解释: 2 与 7 之和等于目标数 9 。因此 index1 = 1, index2 = 2 。
# 代码实现
```C
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* twoSum(int* numbers, int numbersSize, int target, int* returnSize) {
    int *ret = (int*)malloc(2*sizeof(int));
    int index1 = 0;
    int index2 = 1;
    while(numbers[index1] + numbers[index2] != target){
        index2++;
        if (index2 == numbersSize){
            index1++;
            index2 = index1 + 1;
        }
        if(index1 == numbersSize){
            *returnSize = 0;
            return ret;
        }
    }
    ret[0] = index1 + 1;
    ret[1] = index2 + 1;
    *returnSize = 2;
    return ret;
}
```
# 总结体会
1. 当index1遍历到最后一个数时，说明数组中不可能有两数之和等于target，返回一个空数组。
2. 当数组中的两数之和等于target时，returnSize = 2，否则returnSize = 0。