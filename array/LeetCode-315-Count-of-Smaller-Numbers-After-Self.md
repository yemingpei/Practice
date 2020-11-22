### LeetCode-315-Count-of-Smaller-Numbers-After-Self

> 题目链接

[LeetCode-315-Count-of-Smaller-Numbers-After-Self](https://leetcode.com/problems/count-of-smaller-numbers-after-self/)

> 思路

从右到左，每个数字插入树中，插入后就返回比该数字小的数字个数

> 代码

```java
class Solution {
    private static class Node{
         int val;
         int count;
         int leftCount;
         Node left, right;
         public Node(int val){
             this.val = val;
             this.count = 1;
         }
     }
     public List<Integer> countSmaller(int[] nums) {
         LinkedList<Integer> result = new LinkedList<>();
         if(nums == null || nums.length == 0) return result;
         Node root = new Node(nums[nums.length - 1]);
         result.add(0);
         for(int i = nums.length - 2; i >= 0; i--){
             result.addFirst(insert(root, nums[i]));
         }
         return result;
     }
     private int insert(Node node, int val){        
         if(val == node.val){
             node.count ++;
             return node.leftCount;
         }else if(val < node.val){
             node.leftCount++;
             if(node.left == null){
                 node.left = new Node(val);
                 return 0;
             }else{
                 return insert(node.left, val);
             }
         }else{
             if(node.right == null){
                 node.right = new Node(val);
                 return node.count + node.leftCount;
             }else return node.count + node.leftCount + insert(node.right, val);
         }
     }
}
```

> 复杂度分析

遍历数组每个数组里面二分查找树，找到插入的位置，时间复杂度O(nlgn)

构建树来保存数据，空间复杂度O(n)

> 总结

Runtime: 3 ms, faster than 99.48% of Java online submissions for Count of Smaller Numbers After Self.

Memory Usage: 41.6 MB, less than 16.92% of Java online submissions for Count of Smaller Numbers After Self.
