### LeetCode-558-logical-or-of-two-binary-grids-represented-as-quad-trees

> 题目链接

[LeetCode-558-logical-or-of-two-binary-grids-represented-as-quad-trees](https://leetcode-cn.com/problems/logical-or-of-two-binary-grids-represented-as-quad-trees/)

> 思路

利用递归换算每个节点的值，最后再输出父亲节点的值

> 代码

```java
class Solution {
    public Node intersect(Node quadTree1, Node quadTree2) {
        return Order(quadTree1,quadTree2);
    }

    public Node Order(Node quadTree1 ,  Node quadTree2){
        if(quadTree1.isLeaf){
            if(quadTree1.val) return quadTree1;
            return quadTree2;
        }else if(quadTree2.isLeaf){
            if(quadTree2.val) return quadTree2;
            return quadTree1;
        }
        Node topLeft = Order(quadTree1.topLeft, quadTree2.topLeft);
        Node topRight = Order(quadTree1.topRight, quadTree2.topRight);
        Node bottomLeft = Order(quadTree1.bottomLeft, quadTree2.bottomLeft);
        Node bottomRight = Order(quadTree1.bottomRight, quadTree2.bottomRight);
        if(topLeft.isLeaf && topRight.isLeaf && bottomLeft.isLeaf && bottomRight.isLeaf && topLeft.val == topRight.val && topLeft.val == bottomLeft.val && topLeft.val == bottomRight.val) return new Node(topLeft.val,true,null,null,null,null);
        return new Node(false, false, topLeft, topRight, bottomLeft, bottomRight);
    }
}
```

> 复杂度分析

遍历树的每一个节点，时间复杂度O(n)

额外使用函数栈，空间复杂度O(h)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.2 MB, 在所有 Java 提交中击败了100.00%的用户
