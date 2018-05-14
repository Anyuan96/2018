# 问题分析
给定一个大小为 n 的数组，找到其中的众数。众数是指在数组中出现次数大于n/2的元素。

你可以假设数组是非空的，并且给定的数组总是存在众数。

示例 1:

输入: [3,2,3]

输出: 3

示例 2:

输入: [2,2,1,1,1,2,2]

输出: 2
# 代码实现
```C
int majorityElement(int* nums, int numsSize) {
    if (numsSize == 1) return *nums;
    int count=1;
    int ret=nums[0];
    for(int i=1;i<numsSize;i++){
        if(count==0){
            ret = nums[i];
            count =1;
        }
        else if(nums[i]==ret)
            count++;
        else
            count--;
    }
    return ret;
}
```
# 总结体会
因为众数是数组中出现次数>n/2的数，因此至少要比数组中的其他元素出现总次数多出现一次，也就是上述代码中众数的count至少为1。