### LeetCode-508-most-frequent-subtree-sum

> 题目链接

[LeetCode-508-most-frequent-subtree-sum](https://leetcode-cn.com/problems/most-frequent-subtree-sum/)

> 思路

利用map记录次数，然后list记录出现最多的结果，后序遍历，计算整个树的和

> 代码

```java
class Solution {
    int max = 0;
    List<Integer> list = new ArrayList<>();
    Map<Integer, Integer> map = new HashMap<>();
    public int[] findFrequentTreeSum(TreeNode root) {
        calculate(root);
        int[] result = new int[list.size()];
        for(int i = 0; i < list.size(); i++){
            result[i] = list.get(i);
        }
        return result;
    }
    public int calculate(TreeNode root){
        if(root == null) return 0;
        int left = calculate(root.left);
        int right = calculate(root.right);
        int sum = left + right + root.val;
        int result = map.getOrDefault(sum, 0) + 1;
        if(result == max) list.add(sum);
        else if(result > max){
            list.clear();
            list.add(sum);
            max = result;
        }
        map.put(sum, result);
        return sum;
    }
}
```

> 复杂度分析

遍历整个树，时间复杂度O(n)

额外使用map和list，空间复杂度O(n)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.8 MB, 在所有 Java 提交中击败了54.65%的用户
