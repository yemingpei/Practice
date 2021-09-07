### LeetCode-face-17-19

> 题目链接

[LeetCode-face-17-19](https://leetcode-cn.com/problems/missing-two-lcci/)

> 思路

寻找两个不同的数，利用异或的方法对数组和1到（n + 2）进行异或，然后得出两个数的异或，

> 代码

```java
class Solution {
    public int[] missingTwo(int[] nums) {
        int n = nums.length + 2;
        int bit = n ^ (n - 1);
        for(int i = 0; i < nums.length; i++){
            bit = bit ^ (i + 1) ^ nums[i];
        }
        int diff = bit & (-bit);
        int number = 0;
        for(int i = 0; i < nums.length; i++){
            if((diff & nums[i]) == 0) number = number ^ nums[i];
        }
        for(int i = 1; i <= n; i++){
            if((diff & i) == 0) number = number ^ i;
        }
        return new int[]{number, bit ^ number};
    }
}
```

> 复杂度分析

遍历数组3次，时间复杂度O(n)

额外使用int常量，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：39.9 MB, 在所有 Java 提交中击败了52.96%的用户
