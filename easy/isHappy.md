# 问题分析

编写一个算法来判断一个数是不是“快乐数”。

一个“快乐数”定义为：对于一个正整数，每一次将该数替换为它每个位置上的数字的平方和，然后重复这个过程直到这个数变为 1，也可能是无限循环但始终变不到 1。如果可以变为 1，那么这个数就是快乐数。

	示例: 
	
	输入: 19
	输出: true
	解释: 
	1 + 92 = 82
	82 + 22 = 68
	62 + 82 = 100
	12 + 02 + 02 = 1

# 代码实现
```C
bool isHappy(int n) {
    int result(int n){
        int tmp = n;
        int ret = 0;
        while(tmp){
            ret += (tmp % 10) * (tmp % 10);
            tmp /= 10;
        }
        return ret;
    }
    bool isIn(int a, int *nums){
        int len = sizeof(nums)/sizeof(int);
        for (int i = 0; i < len; i++){
            if( nums[i] == a) return true;
        }
        return false;
    }
    if (n == 1 | n == 7) return true;
    if (n < 10) return false;
    int table[10000];
    int cnt = 0;
    while(true){
        int temp = 0;
        temp = result(n);
        if (temp < 10 && (temp != 1 && temp != 7)) return false;
        if (temp == 1 || temp == 7) return true;
        if (isIn(temp, table)) return false;
        table[cnt] = temp;
        n = temp;
        cnt++;
    }
}
```
# 总结体会
这道题中需要构造两个函数，result来计算平方和，isIn来查找是否结果是否出现过。在个位数中，只有1和7是快乐数。然后用table数组来存储已经出现过的结果，如果结果出现过，则不可能是快乐数。也就是来判断死循环的状况。