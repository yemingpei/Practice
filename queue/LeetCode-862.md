### LeetCode-862-Shortest-Subarray-with-Sum-at-Least-K

> 题目链接

[LeetCode-862-Shortest-Subarray-with-Sum-at-Least-K](https://leetcode.com/problems/shortest-subarray-with-sum-at-least-k/)

> 思路

先用数组记录最小子集，从后往前记录，如果prefixMinSum[i + 1] < 0，则证明下一个趋势是变小，则prefixMinSum[i] = prefixMinSum[i + 1] + A[i]，
否则就表示变大或者不变，prefixMinSum[i] =  A[i]，prefixMinSum和sum的差就是i和j区间的和，prefixMinSum表示数组大小趋势，便于sum恢复大小，更快找到
大于等于k的最小区间，避免额外的运算

> 代码

```java
class Solution {
    public int shortestSubarray(int[] A, int K) {
        int N = A.length;
        int[] prefixMinSum = new int[N];
        prefixMinSum[N - 1] = A[N - 1];
        for (int i = N - 2; i >= 0; i--) {
            prefixMinSum[i] = prefixMinSum[i + 1] < 0 ? prefixMinSum[i + 1] + A[i] : A[i];
        }
        int len = N + 1;
        int sum = 0, j = 0;
        for (int i = 0; i < N; i++) {
            sum += A[i];
            while (j < i && sum - prefixMinSum[j] >= K) {
                sum -= A[j];
                j++;
            }
            if (sum >= K) {
                len = Math.min(len, i - j + 1);
            }
        }
        return len == N + 1 ? -1 : len;
    }
}
```

> 复杂度分析

先遍历一遍，获取最小子集之和，用时n，然后在遍历一遍，获取数组之和，最后再比较两个数组的差值，最坏情况j再走一次0到n，时间复杂度O(n)

额外使用int数组，空间复杂度O(n)

> 总结

Runtime: 6 ms, faster than 100.00% of Java online submissions for Shortest Subarray with Sum at Least K.
Memory Usage: 48.9 MB, less than 100.00% of Java online submissions for Shortest Subarray with Sum at Least K.
