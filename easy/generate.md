# 问题分析
给定一个非负整数 numRows，生成杨辉三角的前 numRows 行。

在杨辉三角中，每个数是它左上方和右上方的数的和。

示例:

	输入: 5
	输出:
	[
	     [1],
	    [1,1],
	   [1,2,1],
	  [1,3,3,1],
	 [1,4,6,4,1]
	]
# 代码实现
```C
/**
 * Return an array of arrays.
 * The sizes of the arrays are returned as *columnSizes array.
 * Note: Both returned array and *columnSizes array must be malloced, assume caller calls free().
 */
int** generate(int numRows, int** columnSizes) {
    *columnSizes = (int*)malloc(numRows*sizeof(int));
    int **ret = (int**)malloc(numRows*sizeof(int*));
    for (int i = 0; i < numRows; i++){
        *(ret+i) = (int*)malloc((i+1)*sizeof(int));
        *(*(columnSizes)+i) = i+1;
        ret[i][0] = ret[i][i] = 1;
        for (int j = 1; j < i; j++){
            ret[i][j] = ret[i-1][j-1] + ret[i-1][j];
        }
    }
    return ret;
}
```
# 总结体会
1. 在对二维数组分配空间时，sizeof()函数里面的参数应该是int*。
2. 在杨辉三角中，每一行的第一个数字和最后一个数字都是1，其他数是左上方和右上方的和。根据这个规律就可以生成杨辉三角了。
3. columnSizes是个二维数组，每个元素存储的是该行元素的个数```[[1],[2],[3],...]```