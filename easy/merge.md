# 问题分析
	给定两个有序整数数组 nums1 和 nums2，将 nums2 合并到 nums1 中，使得 num1 成为一个有序数组。
	
	说明:
	
	初始化 nums1 和 nums2 的元素数量分别为 m 和 n。
	你可以假设 nums1 有足够的空间（空间大小大于或等于 m + n）来保存 nums2 中的元素。
	示例:
	
	输入:
	nums1 = [1,2,3,0,0,0], m = 3
	nums2 = [2,5,6],       n = 3
	
	输出: [1,2,2,3,5,6]
# 代码实现
```C
void merge(int* nums1, int m, int* nums2, int n) {
    if (m == 0){
        for (int i = 0; i < n; i++){
            nums1[i] = nums2[i];
        }
    }
    while( m != 0 & n != 0){
        for (int i = m; i < m+n; i++){
            nums1[i] = nums2[i-m];
        }
        for (int i = 0; i < m+n-1; i++){
            for (int j = 0; j < m+n-i-1; j++){
                if (nums1[j] > nums1[j+1]){
                    int temp = nums1[j];
                    nums1[j] = nums1[j+1];
                    nums1[j+1] = temp;
                }
            }
        }
        break;
    }
   
}
```
# 总结体会
	1. 因为函数的类型为void，因此我们需要对nums1数组进行修改。
	2. 先判断两个数组的大小，如果nums1的大小为0，那么直接将nums2的所有元素复制到nums1数组，如果nums2数组大小为0，那么不需要对nums1进行修改。如果都不为0，那么现将两个数组合并，然后进行冒泡排序。