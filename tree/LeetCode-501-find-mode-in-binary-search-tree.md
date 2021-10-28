### LeetCode-501-find-mode-in-binary-search-tree

> 题目链接

[LeetCode-501-find-mode-in-binary-search-tree](https://leetcode-cn.com/problems/find-mode-in-binary-search-tree/)

> 思路

中序遍历，然后开始计算相同的值，利用计数法

> 代码

```java
class Solution {
    int base, count, maxCount;
    List<Integer> answer = new ArrayList<Integer>();
    public int[] findMode(TreeNode root) {
        TreeNode cur = root, pre = null;
        while (cur != null) {
            if (cur.left == null) {
                update(cur.val);
                cur = cur.right;
                continue;
            }
            pre = cur.left;
            while (pre.right != null && pre.right != cur) {
                pre = pre.right;
            }
            if (pre.right == null) {
                pre.right = cur;
                cur = cur.left;
            } else {
                pre.right = null;
                update(cur.val);
                cur = cur.right;
            }
        }
        int[] mode = new int[answer.size()];
        for (int i = 0; i < answer.size(); ++i) {
            mode[i] = answer.get(i);
        }
        return mode;
    }

    public void update(int x) {
        if (x == base) {
            ++count;
        } else {
            count = 1;
            base = x;
        }
        if (count == maxCount) {
            answer.add(base);
        }
        if (count > maxCount) {
            maxCount = count;
            answer.clear();
            answer.add(base);
        }
    }
}
```

> 复杂度分析

遍历整个树，时间复杂度O(n)

额外使用int变量，空间复杂度O(1)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了40.59%的用户

内存消耗：38.8 MB, 在所有 Java 提交中击败了78.44%的用户
