### LeetCode-face-05-04

> 题目链接

[LeetCode-face-05-04](https://leetcode-cn.com/problems/closed-number-lcci/)

> 思路

大一点的数字，寻找到第一个01，然后交换，右侧的1全部后移；小一点的数字，找到第一个10，交换，然后右边的1，全部左移

> 代码

```java
class Solution {
    public int[] findClosedNumbers(int num) {
        if(num == 1) return new int[]{2, -1};
        if(num == Integer.MAX_VALUE) return new int[]{-1, -1};
        int MAX = getNextMax(num);
        int MIN = ~(getNextMax(~num));
        if(MAX < 0) MAX = -1;
        return new int[]{MAX, MIN};
    }

    int getNextMax(long num){
        long X = num & -num;
        long Y = X + num;
        return (int)((num & ~Y) / X >> 1 | Y) ;
    }
}
```

> 复杂度分析

位运算，时间复杂度O(1) 

额外使用int变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.8 MB, 在所有 Java 提交中击败了66.78%的用户
