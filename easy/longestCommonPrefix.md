# 问题分析
	编写一个函数来查找字符串数组中的最长公共前缀。
# 代码实现
```C
char* longestCommonPrefix(char** strs, int strsSize) {
    if(strsSize == 0 || strlen(strs[0])==0) 
        return "";
    if(strsSize == 1)
        return strs[0];
    int ele_len = strlen(strs[0]);
    int min_index = 0;
    for(int i = 0; i < strsSize; i++){
        if(ele_len >= strlen(strs[i])){
            ele_len = strlen(strs[i]);
        }
    }
    int com_len = 0;
    bool exit_flag = false;
    for(int i = 0; i < ele_len;i++){
        char temp = strs[0][i];
        for(int j = 0; j < strsSize; j++){
            if(temp!=strs[j][i]){
                exit_flag = true;
                break;
            }
        }
        if(exit_flag) break;
        com_len ++;
    }
    char* com_str = (char*)calloc(com_len,sizeof(char));//用calloc不用malloc！！！！！
    for(int i = 0; i < com_len; i++){
      *(com_str+i) = strs[0][i];  
    }
    return com_str;
}
```
# 总结体会
	1. 当字符串数组的元素个数strsSize为0，或者字符串数组中有空字符串，那么最长公共前缀为""；
	2. 找出字符串数组中长度最小的元素，将它作为最长公共前缀的最大值ele_len。
	3. 比较每个字符串元素的字符，用com_len储存公共前缀的长度。
	4. 在给com_str分配内存时，要用calloc不用malloc，因为malloc不清除内存中的内容，会造成错误。