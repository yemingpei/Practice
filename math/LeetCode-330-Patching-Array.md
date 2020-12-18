### LeetCode-330-Patching-Array

> 题目链接

[LeetCode-330-Patching-Array](https://leetcode.com/problems/patching-array/)

> 思路

最小的数字组合表示最大的数，则是1，2，4，8，16，二进制的特点满足上述情况，但是题目要求个数最少，所以必须结合原数组的元素，如果curr <= n且nums[index] > curr或者数组用完了，直接翻倍，作为补充元素

> 代码

```java
class Solution {
    public int minPatches(int[] nums, int n) {
        int count = 0, index = 0;
        long curr = 1;
        while (curr <= n) {
          if (index >= nums.length || nums[index] > curr) {
             count++;
             curr *= 2;
          } else {
             curr += nums[index++];
          }
        }
        return count;
    }
}
```

> 复杂度分析

curr不断变大，直到大于目标n，时间复杂度O(n + logn)

需要三个原始变量来辅助，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Patching Array.

Memory Usage: 38.6 MB, less than 61.14% of Java online submissions for Patching Array.
