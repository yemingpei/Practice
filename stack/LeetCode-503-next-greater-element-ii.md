### LeetCode-503-next-greater-element-ii

> 题目链接

[LeetCode-503-next-greater-element-ii](https://leetcode-cn.com/problems/next-greater-element-ii/)

> 思路

利用单调栈和循环数组寻找下一个更大的值，用数组代替栈

> 代码

```java
class Solution {
    public int[] nextGreaterElements(int[] nums) {
        int  index = 0;
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] > nums[index]) {
                index = i;
            }
        }
        int[] stack = new int[nums.length];
        int top = 0;
        stack[top++] = index;
        int[] ans = new int[nums.length];
        ans[index] = -1;
        for (int i = 1; i < nums.length; i++) {
            int j = index - i;
            if (j < 0) {
                j = nums.length + j;
            }
            if (nums[j] == nums[index]){
                ans[j] = -1;
                stack[top++] = j;
                continue;
            }
            while (nums[stack[top - 1]] <= nums[j]){
                top--;
            }
            ans[j] = nums[stack[top - 1]];
            stack[top++] = j;
        }
        return ans;
    }
}
```

> 复杂度分析

每个数字遍历不超过4次，时间复杂度O(n)

额外使用int数组，空间复杂度O(n)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了99.80%的用户

内存消耗：40.9 MB, 在所有 Java 提交中击败了5.01%的用户
