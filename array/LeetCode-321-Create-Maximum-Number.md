### LeetCode-321-Create-Maximum-Number

> 题目链接

[LeetCode-321-Create-Maximum-Number](https://leetcode.com/problems/create-maximum-number/)

> 思路

在数组1寻找i个数字的最大子序列，在数组2寻找k - i个数字的最大子序列，最后再合并

> 代码

```java
class Solution {
    public int[] maxNumber(int[] nums1, int[] nums2, int k) {
        int[][] v1 = new int[k + 1][];
        int[][] v2 = new int[k + 1][];
        int k1 = Math.min(k, nums1.length);
        int k2 = Math.min(k, nums2.length);
        v1[k1] = bestPick(nums1, k1);
        v2[k2] = bestPick(nums2, k2);
        if (nums1.length + nums2.length > k) {
            for (int i = k1; i > 0; i--) v1[i - 1] = trim(v1[i], i);
            for (int i = k2; i > 0; i--) v2[i - 1] = trim(v2[i], i);
        }
        int[] merged = null;
        for (int i = 0; i <= k; i++) {
            if (v1[i] == null || v2[k - i] == null) continue;
            merged = merge(v1[i], i, v2[k - i], k - i, merged);
        }
        return merged;
    }
    
    int[] merge(int[] in1, int len1, int[] in2, int len2, int[] prev) {
        int[] merged = new int[len1 + len2];
        int i1 = 0, i2 = 0, cur = 0;
        while (i1 < len1 && i2 < len2) {
            if (in1[i1] > in2[i2]) merged[cur++] = in1[i1++];
            else if (in1[i1] < in2[i2]) merged[cur++] = in2[i2++];
            else {
                int ii1 = i1, ii2 = i2;
                while (in1[ii1] == in2[ii2]) {
                    if (ii1 < len1 - 1) ii1++;
                    if (ii2 < len2 - 1) ii2++;
                    if (ii1 == len1 - 1 && ii2 == len2 - 1) break;
                }
                if (in1[ii1] > in2[ii2]) merged[cur++] = in1[i1++];
                else if (in2[ii2] > in1[ii1]) merged[cur++] = in2[i2++];
                else merged[cur++] = in2[i2++];
            }
            if (prev != null) {
                if (merged[cur - 1] < prev[cur - 1]) return prev;
                if (merged[cur - 1] > prev[cur - 1]) prev = null;
            }
        }
        if (i1 == len1) {
            while (i2 < len2) {
                merged[cur++] = in2[i2++];
                if (prev != null) {
                    if (merged[cur - 1] < prev[cur - 1]) return prev;
                    if (merged[cur - 1] > prev[cur - 1]) prev = null;
                }
            }
        } else {
            while (i1 < len1) {
                merged[cur++] = in1[i1++];
                if (prev != null) {
                    if (merged[cur - 1] < prev[cur - 1]) return prev;
                    if (merged[cur - 1] > prev[cur - 1]) prev = null;
                }
            }
        }
        return merged;
    }
    
    int[] trim(int[] in, int k) {
        if (k == 1) return new int[0];
        int[] out = new int[k - 1];
        int j = 0;
        for (int i = 0; i < k; i++) {
            if (i == j && (i == k - 1 || in[i] < in[i + 1])) continue;
            out[j++] = in[i];
        }
        return out;
    }
    
    int[] bestPick(int[] in, int k) {
        if (k == 0) return new int[0];
        int[] stack = new int[Math.max(k, in.length)];
        int cur = 1;
        stack[0] = in[0];
        for (int i = 1; i < in.length; i++) {
            while (cur > 0 && in[i] > stack[cur - 1] && in.length - i > k - cur) cur--;
            stack[cur++] = in[i];
        }
        return stack;
    }
}
```

> 复杂度分析

遍历多重数组，时间复杂度O(n ^ 2)

临时保存了子序列的数据，空间复杂度O(n)

> 总结

Runtime: 3 ms, faster than 100.00% of Java online submissions for Create Maximum Number.

Memory Usage: 39.4 MB, less than 85.05% of Java online submissions for Create Maximum Number.
