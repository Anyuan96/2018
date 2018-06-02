# 问题分析
给定一个包含 0, 1, 2, ..., n 中 n 个数的序列，找出 0 .. n 中没有出现在序列中的那个数。

	示例 1:
	
	输入: [3,0,1]
	输出: 2
	示例 2:
	
	输入: [9,6,4,2,3,5,7,0,1]
	输出: 8
# 代码实现
```C
int missingNumber(int* nums, int numsSize) {
    int sum = numsSize*(numsSize+1)/2;
    for (int i = 0; i < numsSize; i++){
        sum -= nums[i];
    }
    return sum;
}
```
# 总结体会
先求出前n项和，然后减去数组的各项即可得到缺少的数字