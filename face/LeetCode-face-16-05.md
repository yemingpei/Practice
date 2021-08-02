### LeetCode-face-16-05

> 题目链接

[LeetCode-face-16-05](https://leetcode-cn.com/problems/factorial-zeros-lcci/)

> 思路

有多少个0就是有多少个5，相乘，25有2个5依次类推

> 代码

```java
class Solution {
    public int trailingZeroes(int n) {
        int count =0;
        while(n > 0){ 
            count += n/5; 
            n /= 5;
        }
        return count;
    }
}
```

> 复杂度分析

不断除5到等于0，时间复杂度O(logn)

额外使用int值，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.5 MB, 在所有 Java 提交中击败了23.70%的用户
