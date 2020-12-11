### LeetCode-331-Verify-Preorder-Serialization-of-a-Binary-Tree

> 题目链接

[LeetCode-331-Verify-Preorder-Serialization-of-a-Binary-Tree](https://leetcode.com/problems/verify-preorder-serialization-of-a-binary-tree/)

> 思路

先切割字符串，然后遍历字符串，通过计算每个节点鸭油两个叶节点的规律，计算，是否符合树的规则

> 代码

```java
class Solution {
    public boolean isValidSerialization(String preorder) {
        String[] vals = preorder.split(",");
        int toRead = 1;
        int children = 0;
        for (String val : vals) {
            if (!val.equals("#")) children += 2;
            if (--toRead == 0) {
                toRead = children;
                children = 0;
            }
        }
        return toRead == 0;
    }
}
```

> 复杂度分析

遍历数组统计，时间复杂度O(n)

额外使用数组切割结果，空间复杂度O(n)

> 总结

Runtime: 3 ms, faster than 91.20% of Java online submissions for Verify Preorder Serialization of a Binary Tree.

Memory Usage: 39.4 MB, less than 12.81% of Java online submissions for Verify Preorder Serialization of a Binary Tree.
