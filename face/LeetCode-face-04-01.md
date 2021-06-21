### LeetCode-face-04-01

> 题目链接

[LeetCode-face-04-01](https://leetcode-cn.com/problems/route-between-nodes-lcci/)

> 思路

因为数据都是有序的，所以可以利用可达分析，起点是否为true，遍历结束，看目标结点是否是true即可

> 代码

```java
class Solution {
    public boolean findWhetherExistsPath(int n, int[][] graph, int start, int target) {
        int[] num = new int[n];
        num[start] = 1;
        for(int i = 0; i < graph.length; i++){
            if(num[graph[i][0]] == 1){
                num[graph[i][1]] = 1;
            }
        }
        if(num[target] == 1) return true;
        else return false;
    }
}
```

> 复杂度分析

需要遍历数组，时间复杂度O(n) 

额外使用int数组，空间复杂度O(n)

> 总结

执行用时：3 ms, 在所有 Java 提交中击败了95.03%的用户

内存消耗：79 MB, 在所有 Java 提交中击败了69.29%的用户
