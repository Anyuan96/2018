# 问题分析
给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。
# 代码实现
```C
int searchInsert(int* nums, int numsSize, int target) {
    if (numsSize == 0) return 0;
    for (int i = 0; i < numsSize; i++){
        if (target <= nums[i])
            return i;
    }
    return numsSize;
}
```
# 总结体会
1. 如果数组为空数组，则直接把目标值插入即可。
2. 应当将应该将target插入大于等于它的位置。
