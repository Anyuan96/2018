# �������
���������ַ��� s �� t ����дһ���������ж� t �Ƿ��� s ��һ����ĸ��λ�ʡ�

ʾ�� 1:

����: s = "anagram", t = "nagaram"
���: true
ʾ�� 2:

����: s = "rat", t = "car"
���: false
# ����ʵ��
```C++
class Solution {
public:
    bool isAnagram(string s, string t) {
       int temp[26] = {0};
        if (s.size() != t.size())
            return false;
        for (int i = 0; i < s.size(); i++){
            temp[s[i] - 'a']++;
        }
        for (int i = 0; i < t.size(); i++){
            temp[t[i] - 'a']--;
        }
        for (int i = 0; i < 26; i++){
            if (temp[i] != 0)
                return false;
        }
        return true;
    }
};
```
# �ܽ����
����ֻҪ�ж������ַ�����ÿ���ַ��ĸ�����ͬ���ɡ�