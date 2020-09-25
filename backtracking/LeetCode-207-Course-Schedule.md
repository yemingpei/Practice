### LeetCode-207-Course-Schedule

> 题目链接

[LeetCode-207-Course-Schedule](https://leetcode.com/problems/course-schedule/)

> 思路

深度搜索，寻找到有环，则返回失败，否则成功

> 代码

```java
class Solution {
    public boolean canFinish(int numCourses, int[][] prerequisites) {
        int[] flag = new int[numCourses];
        List<List<Integer>> list = new ArrayList<>();
        for(int i = 0; i < numCourses; i++)
            list.add(new ArrayList<>());
        for(int[] nums : prerequisites){
            list.get(nums[1]).add(nums[0]);
        }
        for(int i = 0; i < numCourses; i++)
            if(!dfs(list, flag, i)) return false;
        return true;
    }
    public boolean dfs(List<List<Integer>> list, int[] flag, int i){
        if(flag[i] == 1) return false;
        if(flag[i] == -1) return true;
        flag[i] = 1;
        for(Integer j : list.get(i))
            if(!dfs(list, flag, j)) return false;
        flag[i] = -1;
        return true;
    }
}
```

> 复杂度分析

n为点的个数，m为线的数量，时间复杂度O(n + m)

建立图关系额外需要的邻接表，空间复杂度O(n + m)

> 总结

Runtime: 2 ms, faster than 99.52% of Java online submissions for Course Schedule.

Memory Usage: 39.6 MB, less than 95.01% of Java online submissions for Course Schedule.
