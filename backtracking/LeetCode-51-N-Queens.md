### LeetCode-51-N-Queens

> 题目链接

[LeetCode-51-N-Queens](https://leetcode.com/problems/n-queens/)

> 思路

用位运算来查询该位置有没有冲突的皇后位，(~usedBits) & (usedBits + 1)，详细的位运算解析可以自行搜索，用回溯法来校验不同组合的解

> 代码

```java
class Solution {
    public List<List<String>> solveNQueens(int n) {
        List<List<String>> results = new ArrayList<>();
        char[] letters = new char[n];
        Arrays.fill(letters, '.');
        int[] position = new int[n];
        find(0,0,0,0, results, letters, position);
        return results;
    }
    private void find(int index, int upBits, int leftBits, int rightBits, List<List<String>> results, char[] letters, int[] positions) {
        int n = letters.length;
        int usedBits = upBits | leftBits | rightBits;
        for (int i = 0; i < n; i++) {
            int availableBit = (~usedBits) & (usedBits + 1);
            if (availableBit == (1 << i)) {
                positions[index] = i;
                usedBits |= availableBit;
                if (index == n - 1) {
                    List<String> result = new ArrayList<>();
                    for (int pos : positions) {
                        letters[pos] = 'Q';
                        result.add(new String(letters));
                        letters[pos] = '.';
                    }
                    results.add(result);
                } else {
                    find(index + 1, 
                        upBits | availableBit,
                        (leftBits | availableBit) << 1,
                        (rightBits | availableBit) >> 1,
                        results,
                        letters,
                        positions);
                }
            }
        }
    }
}
```

> 复杂度分析

从每一行开始，不断向下推理，时间复杂度O(n!)

额外使用有list，空间复杂度O(n)

> 总结

Runtime: 2 ms, faster than 93.06% of Java online submissions for N-Queens.

Memory Usage: 42.5 MB, less than 10.29% of Java online submissions for N-Queens.
