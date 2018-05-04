# 问题分析
给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。
	
	示例 1:
	
	输入: [2,2,1]
	输出: 1
	
	示例 2:
	
	输入: [4,1,2,1,2]
	输出: 4
# 代码实现
```C
int singleNumber(int* nums, int numsSize) {
    if (numsSize == 1) return nums[0];
    int sum = 0;
    for (int i = 0; i < numsSize; i++){
        sum ^= nums[i];
    }
    return sum;
}
```
# 总结体会
要注意^异或运算符运算符的使用，a^a=0。因此a^b^c^b^a=c,因为只有一个元素出现一次，所以只要将所有的元素异或就可以得到只出现一次的元素。