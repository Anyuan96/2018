# 问题分析
	给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。
	不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。
# 代码实现
```C
int removeDuplicates(int* nums, int numsSize) {
    if(numsSize==0) return 0;
    int newSize = 0;
    for(int i = 1; i<numsSize;i++){
        if (nums[newSize] != nums[i]){
            newSize++;
            nums[newSize] = nums[i];
        }
    }
    newSize++;
    return newSize;
}
```
# 总结体会
	1. 首先判断给定数组是否是空数组，若是空数组则直接返回0。
	2. 需要设定一个新变量newSize来储存引出后数组的新长度。
	3. 由于newSize在循环中是表明元素位置的，因此在循环结束返回其值之前，需要进行自加一。