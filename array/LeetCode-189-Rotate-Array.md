### LeetCode-189-Rotate-Array

> 题目链接

[LeetCode-189-Rotate-Array](https://leetcode.com/problems/rotate-array/)

> 思路
```java
原始数组                  : 1 2 3 4 5 6 7
反转所有数字后             : 7 6 5 4 3 2 1
反转前 k 个数字后          : 5 6 7 4 3 2 1
反转后 n-k 个数字后        : 5 6 7 1 2 3 4
```
反转规律如上，先反转一次全序列，然后是反转前k个，最后是反转剩下的

> 代码

```java
class Solution {
    public void rotate(int[] nums, int k) {
        k %= nums.length;
        reverse(nums, 0, nums.length - 1);
        reverse(nums, 0, k - 1);
        reverse(nums, k, nums.length - 1);
    }
    public void reverse(int[] nums, int start, int end) {
        while (start < end) {
            int temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
            start++;
            end--;
        }
    }
}
```

> 复杂度分析

反转了两次，时间复杂度O(n)

只有一个辅助交换的变量，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Rotate Array.

Memory Usage: 39.4 MB, less than 6.85% of Java online submissions for Rotate Array.
