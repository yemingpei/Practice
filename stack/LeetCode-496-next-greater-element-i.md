### LeetCode-496-next-greater-element-i

> 题目链接

[LeetCode-496-next-greater-element-i](https://leetcode-cn.com/problems/next-greater-element-i/)

> 思路

利用单调栈来获取右边更大的值，先保存在map表里面

> 代码

```java
class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        Map<Integer, Integer> map = new HashMap<>();
        int[] stack = new int[nums2.length];
        int peek = -1;
        for (int i : nums2) {
            while (peek != -1 && i > stack[peek]) {
                map.put(stack[peek--], i);
            }
            stack[++peek] = i;
        }
        int[] ans = new int[nums1.length];
        for (int i = 0; i < nums1.length; ++i) {
            ans[i] = map.getOrDefault(nums1[i], -1);
        }
        return ans;
    }
}
```

> 复杂度分析

遍历两个数组，时间复杂度O(n + m)

额外使用int数组和hashmap，空间复杂度O(n)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了99.64%的用户

内存消耗：38.6 MB, 在所有 Java 提交中击败了48.90%的用户
