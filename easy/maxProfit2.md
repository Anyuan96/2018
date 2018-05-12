# 问题分析
给定一个数组，它的第 i 个元素是一支给定股票第 i 天的价格。

设计一个算法来计算你所能获取的最大利润。你可以尽可能地完成更多的交易（多次买卖一支股票）。

注意：你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。
# 代码实现
```C
int maxProfit(int* prices, int pricesSize) {
    int sum = 0;
    for (int i = 1; i < pricesSize; i++){
        int price = prices[i] - prices[i-1];
        if (price > 0){
            sum += price;
        }
    }
    return sum;
}
```
# 总结体会
本题是贪心算法的应用，只要利润大于零就卖出，如果利润连续大于零，则当天卖出又买入，相当于当天并没有操作，对应于所给的第二个例子。