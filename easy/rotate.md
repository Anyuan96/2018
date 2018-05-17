# 问题分析
给定一个数组，将数组中的元素向右移动 k 个位置，其中 k 是非负数。

	示例 1:
	
	输入: [1,2,3,4,5,6,7] 和 k = 3
	输出: [5,6,7,1,2,3,4]
	解释:
	向右旋转 1 步: [7,1,2,3,4,5,6]
	向右旋转 2 步: [6,7,1,2,3,4,5]
	向右旋转 3 步: [5,6,7,1,2,3,4]
	示例 2:
	
	输入: [-1,-100,3,99] 和 k = 2
	输出: [3,99,-1,-100]
	解释: 
	向右旋转 1 步: [99,-1,-100,3]
	向右旋转 2 步: [3,99,-1,-100]
# 代码实现
```C
void reverse(int *nums, int i, int j){
    int temp;
    for (;i < j; i++, j--){
        temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
void rotate(int *nums, int numsSize, int k){
    k = k % numsSize;
    reverse(nums, 0, numsSize-1);
    reverse(nums, 0, k-1);
    reverse(nums, k, numsSize-1);
}
```
# 总结体会
这道题的总体思路是现将数组整体旋转，然后再翻转前k个，最后翻转k+1到最后一个。要注意，如果k比numsSize大时，数组只要旋转k%numsSize位就可以了。一开始解这道题的方法用了直接的方法，将数组每次移动一位，这样的运行效率非常低