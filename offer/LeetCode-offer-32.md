### LeetCode-offer-32

> 题目链接

[LeetCode-offer-32](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-lcof/)

> 思路

循环遍历树，然后不断检测前面的节点，插到队尾，以此类推到遍历完成

> 代码

```java
class Solution {
    public int[] levelOrder(TreeNode root) {
        if (root == null) return new int[0];
        List<TreeNode> list = new ArrayList<>();
        list.add(root);
        int index = 0;
        int len = 1;
        TreeNode temp;
        while (index < len) {
            temp = list.get(index);
            if (temp.left != null) {
                list.add(temp.left);
                len++;
            }
            if (temp.right != null) {
                list.add(temp.right);
                len++;
            }
            index++;
        }
        int[] result = new int[len];
        for(int i = 0; i < len; i++){
            result[i] = list.get(i).val;
        }
        return result;
    }
}
```

> 复杂度分析

遍历树结构，时间复杂度O(n)

额外使用list保存数据，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.6 MB, 在所有 Java 提交中击败了54.74%的用户
