### LeetCode-363-Max-Sum-of-Rectangle-No-Larger-Than-K

> 题目链接

[LeetCode-363-Max-Sum-of-Rectangle-No-Larger-Than-K](https://leetcode.com/problems/max-sum-of-rectangle-no-larger-than-k/)

> 思路

暴力法，先计算列的和，再横着遍历，相同则退出，不同则比较大小赋值，如果比K大，则另一个方向计算。减少重复的计算和没必要的计算

> 代码

```java
class Solution {
    public int maxSumSubmatrix(int[][] matrix, int k) {
        int row = matrix.length;
        int column = matrix[0].length;
        int res = Integer.MIN_VALUE;
        for (int j = 0; j < column; j++) {
            int[] sum = new int[row];
            for (int c = j; c < column; ++c) {
                for (int r = 0; r < row; ++r) {
                    sum[r] += matrix[r][c];
                }     
                int max = sum[0], maxSoFar = 0;
                for (int s : sum) {
                    maxSoFar = Math.max(maxSoFar + s, s);
                    max = Math.max(max, maxSoFar);
                    if (max == k) return k;
                }
                if (max < k) res = Math.max(res, max);
                else {
                    for (int r = 1; r < row; ++r) {
                        int currSum = 0;
                        for (int z = r; z < row; ++z) {
                            currSum += sum[z];
                            if (currSum <= k) res = Math.max(res, currSum);
                        }
                    }
                }
                if (res == k) return res;
            }
        }
        return res;
    }
}
```

> 复杂度分析

最坏时间是n^4，时间复杂度O(n ^ 4)

额外n 个 大小为 n的数组，空间复杂度O(n ^ 2)

> 总结

Runtime: 4 ms, faster than 99.54% of Java online submissions for Max Sum of Rectangle No Larger Than K.
Memory Usage: 40 MB, less than 100.00% of Java online submissions for Max Sum of Rectangle No Larger Than K.
