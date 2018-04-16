# 问题分析
	给定一个数组 nums 和一个值 val，你需要原地移除所有数值等于 val 的元素，返回移除后数组的新长度。
	不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。
	元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。
# 代码实现
```C
int removeElement(int* nums, int numsSize, int val) {
    if (numsSize == 0) return 0;
    int newSize = 0;
    for (int i = 0; i < numsSize; i++){
        if (nums[i] != val){
            nums[newSize] = nums[i];
            newSize++;
        }
    }
    return newSize;
}
```
# 总结体会
	这道题和移除重复元素有相似之处，但是本题并不是有序数组。而且需要移除的是与val值相同的元素，因此可能需要从数组的第一个元素开始更改。
	
