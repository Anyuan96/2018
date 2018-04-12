# 问题分析
    给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。
    括号必须以正确的顺序关闭，"()" 和 "()[]{}" 是有效的但是 "(]" 和 "([)]" 不是。
# 代码实现
```C
bool isValid(char* s) {
    char nextChar(char s){
        switch(s){
            case ')': return '(';
            case ']': return '[';
            case '}': return '{';
            default: return 'other';    
        }
    }
    int length = strlen(s);
    if(length%2) return false;
    if(*(s+length-1)=='('|*(s+length-1)=='['|*(s+length-1)=='{')
        return false;
    char* x = (char*)malloc((length/2)*sizeof(char));
    char* xx = (char*)malloc((length/2)*sizeof(char));
    char y=*x;
    char yy = *xx;
    int j=0;
    int jj=0;
    for(int i = 0; i< length; i++){
        if(*(s+i)=='(' | *(s+i)=='['|*(s+i)=='{'){
            x[j] = s[i];
            j++;
        }
        else{
            xx[jj] = *(s+i);
            jj++;
            j--;
            if(*(x+j)!=nextChar(*(s+i))) return false;
        }
    }
    if(yy==*xx|y==*x)
        return false;
    else
        return true;
}
```
# 总结体会
    1. 若给定字符串的长度是奇数，则不可能以正确的顺序关闭。如果字符串不是以")","]","}"结尾
    则也不可能正确关闭。
    2. 分别定义一个字符数组，来储存遇到的左右括号，若任意一个字符数组未被改变，则也不能正确关闭。
    3. 若遇到的第一个右括号与最后储存在字符数组x中的左括号不是对应的，则不可能正确关闭。
    4. 顺序比较右括号和左括号的对应关系，来判断是否能正确关闭。
