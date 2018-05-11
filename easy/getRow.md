# 问题分析
给定一个非负索引 k，其中 k ≤ 33，返回杨辉三角的第 k 行。

![杨辉三角](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)

# 代码实现
```C
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* getRow(int rowIndex, int* returnSize) {
    int **triangle = (int**)malloc((rowIndex+1)*sizeof(int*));
    for (int i = 0; i <= rowIndex; i++){
        triangle[i] = (int*)malloc((i+1)*sizeof(int));
        triangle[i][0] = triangle[i][i] = 1;
        for (int j = 1; j < i; j++){
            triangle[i][j] = triangle[i-1][j-1] + triangle[i-1][j];
        }
    }
    int *ret;
    ret = triangle[rowIndex];
    *returnSize = rowIndex+1;
    return ret;
}
```
# 总结体会
本题和杨辉三角I的思路差不多，只是本题只需要输出第rowIndex行就可以了。建立一个二维数组来存储生成的杨辉三角，然后定义一个指针变量ret，指向杨辉三角的第rowIndex行就可以了。
