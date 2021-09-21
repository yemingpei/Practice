### LeetCode-456-132-pattern

> 题目链接

[LeetCode-456-132-pattern](https://leetcode-cn.com/problems/132-pattern/)

> 思路

利用队列，枚举求值

> 代码

```java
class Solution {
    public boolean find132pattern(int[] nums) {
        int n = nums.length;
        Deque<Integer> candidateK = new LinkedList<Integer>();
        candidateK.push(nums[n - 1]);
        int maxK = Integer.MIN_VALUE;
        for (int i = n - 2; i >= 0; --i) {
            if (nums[i] < maxK) {
                return true;
            }
            while (!candidateK.isEmpty() && nums[i] > candidateK.peek()) {
                maxK = candidateK.pop();
            }
            if (nums[i] > maxK) {
                candidateK.push(nums[i]);
            }
        }
        return false;
    }
}
```

> 复杂度分析

循环结合队列，时间复杂度O(nlogn)

额外使用队列，空间复杂度O(n)

> 总结

执行用时：10 ms, 在所有 Java 提交中击败了91.03%的用户

内存消耗：62.5 MB, 在所有 Java 提交中击败了31.85%的用户
