# �������
�����������飬дһ���������������ǵĽ�����

����:

 ���� num1= [1, 2, 2, 1], nums2 = [2, 2], ���� [2].
# ����ʵ��
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
# �ܽ����
�ֽ����������������Ȼ��������������е�Ԫ�أ��Ƚ���Ӧ��Ԫ�أ������ȣ�����ݵ�ǰֵ�Ƿ������һ�α����ֵ��ͬ�����д����������ȣ��򽫽�Сֵ����������ơ�