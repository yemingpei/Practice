### LeetCode-offer-45

> 题目链接

[LeetCode-offer-45](https://leetcode-cn.com/problems/ba-shu-zu-pai-cheng-zui-xiao-de-shu-lcof/)

> 思路

通过比较ab和ba的大小，进行排序，最后再小到大拼接

> 代码

```java
class Solution {
    public String minNumber(int[] nums) {
        quickSort(nums, 0, nums.length - 1);
        StringBuilder res = new StringBuilder();
        for (int num : nums) res.append(num);
        return res.toString();
    }
    private void quickSort(int[] nums, int start, int end) {
        if (start >= end) return;
        int pivot = nums[start];
        int i = start;
        int j = end;
        while (i < j) {
            while (i < j && checkIfSmaller(pivot, nums[j])) j--;
            while (i < j && checkIfSmaller(nums[i], pivot)) i++;
            swap(nums, i, j);
        }
        swap(nums, start, i);
        quickSort(nums, start, i - 1);
        quickSort(nums, i + 1, end);
    }
    private boolean checkIfSmaller(int a, int b) {
        long x = 10;
        long y = 10;
        while (a >= x) x *= 10;
        while (b >= y) y *= 10;
        return a + x * b >= b + y * a;
    }
    private void swap(int[] nums, int l, int r) {
        int temp = nums[l];
        nums[l] = nums[r];
        nums[r] = temp;
    }
}
```

> 复杂度分析

排序，时间复杂度O(logn)

额外使用三个int值，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：36.3 MB, 在所有 Java 提交中击败了99.69%的用户
