### LeetCode-134-Gas-Station

> 题目链接

[LeetCode-134-Gas-Station](https://leetcode.com/problems/gas-station/)

> 思路

1. 若gas（总和） - cost（总和）小于0，则肯定无解
2. 若gas[i] - cost[i]小于0则肯定不能作为起点，且起点开始之后出现和为负则也不可能为起点
3. 根据上述两点能确定起点的位置，但需要验证总和sum大于等于0，存在K点有足够的油可以走完

> 代码

```java
class Solution {
    public int canCompleteCircuit(int[] gas, int[] cost) {
        int length = gas.length;
        int sum = 0;
        int position = 0;
        int count = 0;
        for(int i = 0; i < length; i++){
            int num = gas[i] - cost[i];
            sum += num;
            count += num;
            if(count < 0){
                count = 0;
                position = i + 1;
            }
        }
        return sum < 0 ? -1 : position;
    }
}
```

> 复杂度分析

遍历一遍数组，时间复杂度O(n)

需要三个int来辅助，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Gas Station.

Memory Usage: 39.6 MB, less than 88.49% of Java online submissions for Gas Station.
