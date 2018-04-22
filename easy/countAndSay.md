# 问题分析
	报数序列是指一个整数序列，按照其中的整数的顺序进行报数，得到下一个数。
	其前五项如下：
	
	1.     1
	2.     11
	3.     21
	4.     1211
	5.     111221
	1 被读作  "one 1"  ("一个一") , 即 11。
	11 被读作 "two 1s" ("两个一"）, 即 21。
	21 被读作 "one 2",  "one 1" （"一个二" ,  "一个一") , 即 1211。
	
	给定一个正整数 n ，输出报数序列的第 n 项。
	
	注意：整数顺序将表示为一个字符串。
# 代码实现
```C
char ret[10000];
char a[10000];
char* countAndSay(int n) {
    char temp[3];
    strcpy(ret, "1");
    strcpy(a, "");
    int count = 1;
    for (int i = 1; i < n; i++){
        int len = strlen(ret);
        for (int j = 0; j < len; j++){
            if (ret[j] == ret[j+1])
                count++;
            else{
                temp[0] = count + '0';
                temp[1] = ret[j];
                temp[2] = '\0';
                strcat(a, temp);
                count = 1;
            }
        }
        strcpy(ret,a);
        strcpy(a,"");
    } 
    return ret;
}
```
# 总结体会
	1. 字符串以'\0'结尾，将每个部分存入temp字符串，temp = [count+'0', ret[j], '\0']，其中count代表的是相同字符的个数，ret[j]代表相同的字符，'\0'为字符串的结尾。
	2. 因为第n项的输出与第n-1项有关，因此要进行n-1次循环（将n=1时，返回的字符串预先定义为“1”），然后用a字符串将不同字符的部分连接(strcat)。