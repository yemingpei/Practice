### LeetCode-210-Course-Schedule-II

> 题目链接

[LeetCode-210-Course-Schedule-II](https://leetcode.com/problems/course-schedule-ii/)

> 思路

深度搜索，寻找到有环，则返回失败，否则成功，倒序输出数组

> 代码

```java
class Solution {
    private int index;
    public int[] findOrder(int numCourses, int[][] prerequisites) {
        ArrayList<Integer>[] e = new ArrayList[numCourses];
        for (int[] prerequisite : prerequisites) {
            int u = prerequisite[0];
            int v = prerequisite[1];
            if (e[u] == null) {
                e[u] = new ArrayList<>();
            }
            e[u].add(v);
        }
        index = 0;
        int[] visit = new int[numCourses];
        int[] res = new int[numCourses];
        for (int i = 0; i < numCourses; i++) {
            if (visit[i] == 0 && topoSort(e, visit, res, i)) {
                return new int[0];
            }
        }
        return res;
    }

    private boolean topoSort(ArrayList<Integer>[] e, int[] visit, int[] res, int u) {
        visit[u] = 1; 
        if (e[u] != null) {
            for (int i = 0; i < e[u].size(); i++) {
                int v = e[u].get(i);
                if (visit[v] == 1) return true; // cycle
                if (visit[v] == 0 && topoSort(e, visit, res, v)) {
                    return true;
                }
            }
        }
        visit[u] = 2;
        res[index++] = u;
        return false;
    }
}
```

> 复杂度分析

n为点的个数，m为线的数量，时间复杂度O(n + m)

建立图关系额外需要的邻接表，空间复杂度O(n + m)

> 总结

Runtime: 3 ms, faster than 94.99% of Java online submissions for Course Schedule II.

Memory Usage: 45.7 MB, less than 20.34% of Java online submissions for Course Schedule II.
