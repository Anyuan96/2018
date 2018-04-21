# 问题分析
给定一个非负整数组成的非空数组，在该数的基础上加一，返回一个新的数组。

最高位数字存放在数组的首位， 数组中每个元素只存储一个数字。

你可以假设除了整数 0 之外，这个整数不会以零开头。
# 代码实现
```C
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* plusOne(int* digits, int digitsSize, int* returnSize) {
    int *ret = (int*)malloc((digitsSize+1)*sizeof(int));
    int c = 1;
    for (int i = digitsSize -1; i >= 0; i--){
        ret[i] = (digits[i] + c) % 10;
        c = (digits[i] + c) / 10;
    }
    if (c == 1){
        for (int i = digitsSize; i>=0; i--)
            ret[i] = ret[i-1];
        ret[0] = 1;
        *returnSize = digitsSize +1;
    }else{
        *returnSize = digitsSize;
    }
    return ret;
}
```
# 总结体会
1. 根据题目要求，返回的数组需要用malloc进行分配。
2. 设置c为进位标志，从输入数组的最后一位开始加1。
3. 当运行到最高位仍然产生进位时（也就是各位都是9的情况），则在返回数组ret的最高位前面添加一个1，并且returnSize比输入数组的大小returnSize多1。