### LeetCode-96-Unique-Binary-Search-Trees

> 题目链接

[LeetCode-96-Unique-Binary-Search-Trees](https://leetcode.com/problems/unique-binary-search-trees/)

> 思路

由卡塔兰数公式求解，f(n) = f(n - 1) * 2 * (2 * n + 1) / (i + 2)

> 代码

```java
class Solution {
    public int numTrees(int n) {
        long result = 1;
        for (int i = 0; i < n; ++i) {
          result = result * 2 * (2 * i + 1) / (i + 2);
        }
        return (int) result;
    }
}
```

> 复杂度分析

循环遍历，计算公式，时间复杂度O(n)

无使用额外空间，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Unique Binary Search Trees.

Memory Usage: 36.5 MB, less than 5.55% of Java online submissions for Unique Binary Search Trees.
