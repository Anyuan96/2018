# 问题分析
	
	给定一个整数数列，找出其中和为特定值的那两个数。

	你可以假设每个输入都只会有一种答案，同样的元素不能被重用。
# 代码实现
	```C
		int* twoSum(int* nums, int numsSize, int target) {
		    int *result = (int*)malloc(2*sizeof(int));
		    for(int i = 0;i < numsSize; i++){
			int temp = target - *(nums + i);
			for(int j = i + 1; j < numsSize; j++){
			    if(temp == *(nums + j)){
				result[0] = i;
				result[1] = j;
				return result;
			    }
			}  
		    }
		    return 0;
		}
	```
# 总结体会
	1. 由于同样的元素不能被重用，故j的起始位置应该是j+1
	2. 应该为*result分配动态内存
	3. *(nums)是指针nums对应的值
