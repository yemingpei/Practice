### LeetCode-offer-32-III

> 题目链接

[LeetCode-offer-32-III](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-iii-lcof/)

> 思路

前序遍历，然后然后交叉插入数字，完成最终的输出

> 代码

```java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        if(root != null) addNumber(result, 0, root);
        return result;
    }
    public void addNumber(List<List<Integer>> result, int position, TreeNode node){
        if(position == result.size()) result.add(new ArrayList<>());
        if((position & 1) == 1){
            result.get(position).add(0, node.val);
        }else{
            result.get(position).add(node.val);
        }
        if(node.left != null) addNumber(result, position + 1, node.left);
        if(node.right != null) addNumber(result, position + 1, node.right);
    }
}
```

> 复杂度分析

遍历树，时间复杂度O(n)

无额外使用空间，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了99.85%的用户

内存消耗：38.6 MB, 在所有 Java 提交中击败了67.45%的用户
