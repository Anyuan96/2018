# 问题分析
给定一个数组 nums，编写一个函数将所有 0 移动到数组的末尾，同时保持非零元素的相对顺序。

	示例:
	
	输入: [0,1,0,3,12]
	输出: [1,3,12,0,0]
# 代码实现
```C
void moveZeroes(int* nums, int numsSize) {
    int zeros = 0;
    int cnt = 0;
    for (int i = 0; i < numsSize; i++){
        if ( nums[i] == 0) 
            zeros++;
        else{
            nums[cnt] = nums[i];
            cnt++;
        }
    }
    for (;zeros > 0; zeros--){
        nums[numsSize - zeros ] = 0;
    }
}
```
# 总结体会
先将数组中的非零数字按照顺序放到数组的前面，然后根据0的个数，将原数组的末尾变成0.