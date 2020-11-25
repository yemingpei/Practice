### LeetCode-310-Minimum-Height-Trees

> 题目链接

[LeetCode-310-Minimum-Height-Trees](https://leetcode.com/problems/minimum-height-trees/)

> 思路

记录每个点的入度，然后最小入度的先进入队列，然后一次清空队列中入度最小的，当某个点的入度削减为最小时也进入队列，直到最后队列为空

> 代码

```java
class Solution {
    public List<Integer> findMinHeightTrees(int n, int[][] edges) {
        List<Integer> res = new ArrayList<>();
        if (n == 1) {
            res.add(0);
            return res;
        }
        int[] degree = new int[n];
        List<List<Integer>> map = new ArrayList<>();
        for (int i = 0; i < n; i++) {
            map.add(new ArrayList<>());
        }
        for (int[] edge : edges) {
            degree[edge[0]]++;
            degree[edge[1]]++;
            map.get(edge[0]).add(edge[1]);
            map.get(edge[1]).add(edge[0]);
        }
        Queue<Integer> queue = new LinkedList<>();
        for (int i = 0; i < n; i++) {
            if (degree[i] == 1) queue.offer(i);
        }
        while (!queue.isEmpty()) {
            res = new ArrayList<>();
            int size = queue.size();
            for (int i = 0; i < size; i++) {
                int cur = queue.poll();
                res.add(cur);
                List<Integer> neighbors = map.get(cur);
                for (int neighbor : neighbors) {
                    degree[neighbor]--;
                    if (degree[neighbor] == 1) {
                        queue.offer(neighbor);
                    }
                }
            }
        }
        return res;
    }
}
```

> 复杂度分析

广度遍历，组装数据时间复杂度O(n ^ 2)

额外使用二维数组来保存图的关系，空间复杂度O(n ^ 2)

> 总结

Runtime: 10 ms, faster than 85.69% of Java online submissions for Minimum Height Trees.

Memory Usage: 42.6 MB, less than 53.20% of Java online submissions for Minimum Height Trees.
