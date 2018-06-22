# 问题分析
给定两个数组，写一个函数来计算它们的交集。

例子:

 给定 num1= [1, 2, 2, 1], nums2 = [2, 2], 返回 [2].
# 代码实现
```C++
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
            sort(nums1.begin(), nums1.end());
            sort(nums2.begin(), nums2.end());
            vector<int> result;
            int temp;
            for (int i = 0, j = 0; i < nums1.size() && j < nums2.size(); )
            {
                if (nums1[i] < nums2[j])
                    i++;
                else if (nums1[i] > nums2[j])
                    j++;
                else if (nums1[i] == nums2[j])
                {
                    if (result.size() == 0 || nums1[i] != temp)
                    {
                        result.push_back(nums1[i]);
                        temp = nums1[i];
                    }
                    i++;
                    j++;
                }
            } 
            return result;
    }
};
```
# 总结体会
现将两个数组进行排序，然后遍历两个数组中的元素，比较相应的元素，如果相等，则根据当前值是否与最后一次保存的值相同来进行处理，如果不想等，则将较小值的索引向后移。