### LeetCode-52-N-Queens-II

> 题目链接

[LeetCode-52-N-Queens-II](https://leetcode.com/problems/n-queens-ii/)

> 思路

思路同[LeetCode-51-N-Queens](https://leetcode.com/problems/n-queens/)，有公式法，查文献

> 代码

```java
class Solution {
    private int sum;
    public int totalNQueens(int n) {
        sum = 0;
        int[] position = new int[n];
        find(0,0,0,0, position, n);
        return sum;
    }
    private void find(int index, int upBits, int leftBits, int rightBits, int[] positions ,int size) {
        int n = size;
        int usedBits = upBits | leftBits | rightBits;
        for (int i = 0; i < n; i++) {
            int availableBit = (~usedBits) & (usedBits + 1);
            if (availableBit == (1 << i)) {
                positions[index] = i;
                usedBits |= availableBit;
                if (index == n - 1) {
                    sum++;
                } else {
                    find(index + 1, 
                        upBits | availableBit,
                        (leftBits | availableBit) << 1,
                        (rightBits | availableBit) >> 1,
                        positions,
                        size);
                }
            }
        }
    }
}
```

> 复杂度分析

从每一行开始，不断向下推理，时间复杂度O(n!)

额外使用有int数组，空间复杂度O(n)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for N-Queens II.

Memory Usage: 36.2 MB, less than 61.20% of Java online submissions for N-Queens II.
