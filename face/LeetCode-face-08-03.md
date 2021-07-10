### LeetCode-face-08-03

> 题目链接

[LeetCode-face-08-03](https://leetcode-cn.com/problems/magic-index-lcci/)

> 思路

遍历数组，寻找nums[i] == i的数字，提前结束

> 代码

```java
class Solution {
    public int findMagicIndex(int[] nums) {
        for(int i = 0; i < nums.length; i++){
            if(nums[i] == i) return i;
        }
        return -1;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n) 

无额外使用变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.9 MB, 在所有 Java 提交中击败了48.49%的用户
