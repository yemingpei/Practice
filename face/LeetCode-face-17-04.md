### LeetCode-face-17-04

> 题目链接

[LeetCode-face-17-04](https://leetcode-cn.com/problems/missing-number-lcci/)

> 思路

因为题目给出的信息是0到n缺少一个，然后可以通过加法0到n的和减去数组的总和，就是缺少的数字

> 代码

```java
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;
        for(int i = 0; i < nums.length; i++){
            n = n + i - nums[i];
        }
        return n;
    }
}
```

> 复杂度分析

遍历一遍数组，时间复杂度O(n)

额外使用int变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.9 MB, 在所有 Java 提交中击败了42.94%的用户
