# 问题分析
	给定两个二进制字符串，返回他们的和（用二进制表示）。
	
	输入为非空字符串且只包含数字 1 和 0。
# 代码实现
```C
char* addBinary(char* a, char* b) {
    int aLen = strlen(a);
    int bLen = strlen(b);
    int maxLen = aLen>bLen?aLen:bLen;
    char *ext_str = (char*)malloc((maxLen)*sizeof(char));
    memset(ext_str, '0', maxLen);
    char *add_str = aLen > bLen ? a:b;
    int c = 0;
    if (aLen > bLen){
        for (int i = 0; i < bLen; i++){
            ext_str[maxLen-bLen+i] = b[i];
        }
    }else{
        for (int i = 0; i < aLen; i++){
            ext_str[maxLen-aLen+i] = a[i];
        }
    }
    int temp;
    int num_min;
    int num_max;
    for (int i = maxLen - 1; i >= 0; i--){
        num_min = (int)(add_str[i] - '0');
        num_max = (int)(ext_str[i] - '0');
        temp = num_min + num_max + c;
        add_str[i] = (char)(temp%2 + '0');
        c = temp/2;
    }
    if (c == 1){
        char *ret = (char*)calloc((maxLen+2),sizeof(char));
        ret[0] = '1';
        for (int i = 1; i <= maxLen; i++)
            ret[i] = add_str[i-1];
        return ret;
    }else{
        return add_str;
    }
}
```
# 总结分析
	1. 现将较短的二进制数字高位补零，补成与较长的二进制数位数相同。
	2. 然后将处理后的两个二进制数和进位进行相加，然后对每位相加的结果进行处理。本位数为结果对2取余，进位为结果除以2的伤。
	3. 若最高位产生进位，则定义一个新的数组，长度为较长二进制数组+1，最高位为1，余下的几位与相加结果相同，否则直接返回结果即可。