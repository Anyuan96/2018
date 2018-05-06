# 问题分析
给定一个正整数，返回它在Excel表中相对应的列名称。

	例如，
	
	    1 -> A
	    2 -> B
	    3 -> C
	    ...
	    26 -> Z
	    27 -> AA
	    28 -> AB 
	    ...
	示例 1:
	
	输入: 1
	输出: "A"
	示例 2:
	
	输入: 28
	输出: "AB"
	示例 3:
	
	输入: 701
	输出: "ZY"
# 代码实现
```C
char* convertToTitle(int n) {
    void Reverse(char *s){
        char c;
        for(int i =0,j=strlen(s)-1;i<j; ++i,--j){
            c=s[i];
            s[i]=s[j];
            s[j]=c;
        }
    }
    char alphbet[26] = {'A','B','C','D','E','F','G','H',
                        'I','J','K','L','M','N','O','P',
                        'Q','R','S','T','U','V','W','X',
                        'Y','Z'};
    if (n <= 26) {
        char *ret = (char*)malloc(sizeof(char));
        *ret = alphbet[n-1];
        return ret;
    }
    char *m = (char*)malloc(10000000*sizeof(char));
    int mlen = 1;
    while(n){
        int temp = (n-1)%26;
        m[mlen-1] = alphbet[temp];
        mlen++;
        n = (n-1)/26;
    }
    m[mlen] = '\0';
    Reverse(m);
    return m;
}
```
# 总结体会
1. 这道题的思路是将十进制数转换为二十六进制数，不同点是数从1-26而不是常见的0-25，因此在处理时应该在原数的基础上减1
2. 我们用对除以26取余的方法来得到26进制上的每一位数，与十进制转换为二进制相似，要将余数的顺序颠倒过来就可以得到正确的顺序了。