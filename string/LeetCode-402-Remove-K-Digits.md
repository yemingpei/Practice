### LeetCode-402-Remove-K-Digits

> 题目链接

[LeetCode-402-Remove-K-Digits](https://leetcode.com/problems/remove-k-digits/)

> 思路

快慢指针来比较推算k的位置，贪心算法，如果一个数字比后一个数字大，则该数字应该被移走

> 代码

```java
class Solution {
    public String removeKdigits(String num, int k) {
        if (num == null || k >= num.length()) {
            return "0";
        }
        int slow = 0;
        int fast = 0;
        char[] arr = num.toCharArray();
        int n = arr.length;
        while (fast < n) {
            while (slow > 0 && arr[fast] < arr[slow - 1] && k > 0) {
                slow--;
                k--;
            }
            arr[slow++] = arr[fast++];
        }
        while (k > 0) {
            slow--;
            k--;
        }
        int head = 0;
        while (head < slow && arr[head] == '0') {
            head++;
        }
        if (head == slow) return "0";
        return new String(arr, head, slow-head);
    }
}
```

> 复杂度分析

快慢指针遍历字符串，时间复杂度O(n)

额外使用数组来保存字符，空间复杂度O(n)。

> 总结

Runtime: 2 ms, faster than 98.67% of Java online submissions for Remove K Digits.

Memory Usage: 38.9 MB, less than 84.61% of Java online submissions for Remove K Digits.
