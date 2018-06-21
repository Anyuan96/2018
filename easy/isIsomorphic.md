# �������
���������ַ��� s �� t���ж������Ƿ���ͬ���ġ�

��� s �е��ַ����Ա��滻�õ� t ����ô�������ַ�����ͬ���ġ�

���г��ֵ��ַ�����������һ���ַ��滻��ͬʱ�����ַ���˳�������ַ�����ӳ�䵽ͬһ���ַ��ϣ����ַ�����ӳ���Լ�����

ʾ�� 1:

����: s = "egg", t = "add"

���: true

ʾ�� 2:

����: s = "foo", t = "bar"

���: false

ʾ�� 3:

����: s = "paper", t = "title"

���: true
# ����ʵ��
```C++
class Solution {
public:
    bool isIsomorphic(string s, string t) {
        if (s.length() != t.length())
            return false;
        if (transferStr(s) == transferStr(t))
            return true;
        return false;
    }
    string transferStr (string s){
        char table[128] = {0};
        char sub = '0';
        for (int i = 0; i < s.length(); i++){
            char c = s.at(i);
            if (table[c] == 0){
                table[c] = sub++;
            }
            s[i] = table[c];
        }
     return s;       
    }
};
```
# �ܽ����
��ĿҪ���ж�һ���ַ����Ƿ�������һ���ַ���ת����������˷ֱ������ַ����е��ַ��ֱ�����滻�������õ������ַ����Ƿ���ͬ��