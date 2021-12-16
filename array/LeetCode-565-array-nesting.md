### LeetCode-565-array-nesting

> 题目链接

[LeetCode-565-array-nesting](https://leetcode-cn.com/problems/array-nesting/)

> 思路

因为不会有相同的数字，寻找闭环，闭环的元素是唯一的，可以通过数组本身作为标记来遍历数组

> 代码

```java
class Solution {
    public int arrayNesting(int[] nums) {
        int size = nums.length;
        int max = 0;
        for (int i = 0; i < size; i++) {
            int count = 0;
            int pos = nums[i];
            if(pos == -1) continue;
            while (nums[pos] != -1) {
                int flag = pos;
                count++;
                pos = nums[pos];
                nums[flag] = -1;
            }
            max = Math.max(count, max);
        }
        return max;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用常量，空间复杂度O(1)

> 总结

执行用时：4 ms, 在所有 Java 提交中击败了90.17%的用户

内存消耗：54.5 MB, 在所有 Java 提交中击败了22.32%的用户
