### LeetCode-319-Bulb-Switcher

> 题目链接

[LeetCode-319-Bulb-Switcher](https://leetcode.com/problems/bulb-switcher/)

> 思路

寻找小于n的平方数，因为平方数只有三个约数，灯必亮，非平方数的约数都是偶数个，所以灯不亮

> 代码

```java
class Solution {
    public int bulbSwitch(int n) {
        if(n == 0) return 0;
        int i = 1;
        while(i * i <= n){
            i++;
        }
        return i - 1;
    }
}
```

> 复杂度分析

寻找小于n的平方数，时间复杂度O(logn)

无额外使用空间，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Bulb Switcher.

Memory Usage: 35.7 MB, less than 61.98% of Java online submissions for Bulb Switcher.
