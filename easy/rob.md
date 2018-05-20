# 问题分析
你是一个专业的小偷，计划偷窃沿街的房屋。每间房内都藏有一定的现金，影响你偷窃的唯一制约因素就是相邻的房屋装有相互连通的防盗系统，如果两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警。

给定一个代表每个房屋存放金额的非负整数数组，计算你在不触动警报装置的情况下，能够偷窃到的最高金额。

	示例 1:
	
	输入: [1,2,3,1]
	输出: 4
	解释: 偷窃 1 号房屋 (金额 = 1) ，然后偷窃 3 号房屋 (金额 = 3)。
	     偷窃到的最高金额 = 1 + 3 = 4 。
	示例 2:
	
	输入: [2,7,9,3,1]
	输出: 12
	解释: 偷窃 1 号房屋 (金额 = 2), 偷窃 3 号房屋 (金额 = 9)，接着偷窃 5 号房屋 (金额 = 1)。
	     偷窃到的最高金额 = 2 + 9 + 1 = 12 。
# 代码实现
```C
int rob(int* nums, int numsSize) {
    if (numsSize == 0) return 0;
    if (numsSize == 1) return nums[0];
    if (numsSize == 2) return nums[0] > nums[1] ? nums[0] : nums[1];
    int *ret = (int*)malloc(numsSize*sizeof(int));
    ret[0] = nums[0];
    ret[1] = nums[1] > ret[0] ? nums[1] : ret[0];
    for (int i = 2; i < numsSize; i++){
        ret[i] = ret[i-1] > ret[i-2] + nums[i] ? ret[i-1] : ret[i-2] + nums[i];
    }
    return ret[numsSize - 1];
}
```
# 总结体会
由于输入数组中的数都是正数，所以这个题就是求数组中连续不相邻元素的和，也就是数组[a1,a2,a3,a4,a5],a1+a3+a5和a2+a4的最大值的问题。我们定义一个数组ret来存储当前可以偷到的最大值，也就是ret[i] = max{ret[i-1], ret[i-2] + nums[i]}，是一个递推的问题。