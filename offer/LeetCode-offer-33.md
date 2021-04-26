### LeetCode-offer-33

> 题目链接

[LeetCode-offer-33](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-hou-xu-bian-li-xu-lie-lcof/)

> 思路

通过根节点，来分左右子树，然后满足判断条件左子树都小于根节点，右子树都大于根节点

> 代码

```java
class Solution {
    public boolean verifyPostorder(int[] postorder) {
        return isPostorder(postorder, 0, postorder.length - 1);
    }
    public boolean isPostorder(int[] postorder, int start, int end){
        if(start >= end) return true;
        int num = postorder[end];
        int rightEdge = end - 1;
        while(rightEdge > -1 && postorder[rightEdge] > num) rightEdge--;
        for(int i = start; i < rightEdge; i++)
            if(postorder[i] > num) return false;
        return isPostorder(postorder, start, rightEdge) && isPostorder(postorder, rightEdge + 1, end - 1);
    }
}
```

> 复杂度分析

不断比较最后一个数和前面的值，时间复杂度O(n ^ 2)

额外使用三个int值，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.8 MB, 在所有 Java 提交中击败了83.34%的用户
