# 问题分析
给定两个数组，写一个方法来计算它们的交集。

例如:
给定 nums1 = [1, 2, 2, 1], nums2 = [2, 2], 返回 [2, 2].
# 代码实现
```C++
class Solution {
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
            sort(nums1.begin(), nums1.end());
            sort(nums2.begin(), nums2.end());
            vector<int> result;
            for (int i = 0, j = 0; i < nums1.size() && j < nums2.size(); )
            {
                if (nums1[i] < nums2[j])
                    i++;
                else if (nums1[i] > nums2[j])
                    j++;
                else if (nums1[i] == nums2[j])
                {
                    result.push_back(nums1[i]);
                    i++;
                    j++;
                }
            } 
            return result;
    }
};
```
# 总结体会
本题和上一题的思想差不多，但是不需要判断是否与最后一个相等的元素相同。