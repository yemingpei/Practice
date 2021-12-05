### LeetCode-553-optimal-division

> 题目链接

[LeetCode-553-optimal-division](https://leetcode-cn.com/problems/optimal-division/)

> 思路

要使得数最大，等式必然是a/(b/c/d)这个样子

> 代码

```java
class Solution {
    public String optimalDivision(int[] nums) {
        StringBuilder sb = new StringBuilder();
        sb.append(nums[0]);
        for (int i = 1; i < nums.length; i++) {
            sb.append('/');
            sb.append(nums[i]);
        }
        if (nums.length >= 3) {
            sb.insert(String.valueOf(nums[0]).length() + 1, '(');
            sb.append(')');
        }
        return sb.toString();
    }
}
```

> 复杂度分析

遍历整个数组，时间复杂度O(n)

额外使用StringBuilder，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.9 MB, 在所有 Java 提交中击败了90.46%的用户
