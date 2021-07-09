### LeetCode-face-08-02

> 题目链接

[LeetCode-face-08-02](https://leetcode-cn.com/problems/robot-in-a-grid-lcci/)

> 思路

回溯法，利用深度搜索，利用返回值实现剪枝

> 代码

```java
class Solution {
    public List<List<Integer>> pathWithObstacles(int[][] obstacleGrid) {
        List<List<Integer>> result = new ArrayList<>();
        if(obstacleGrid.length == 0) return result;
        if(obstacleGrid[0].length == 0) return result;
        if(obstacleGrid[0][0] == 1) return result;
        if(obstacleGrid[obstacleGrid.length - 1][obstacleGrid[0].length - 1] == 1) return result;
        findPath(result, 0, 0, obstacleGrid.length - 1, obstacleGrid[0].length - 1, obstacleGrid);
        return result;
    }

    public int findPath(List<List<Integer>> reuslt, int i, int j, int iMax, int jMax, int[][] obstacleGrid){
        List<Integer> list = new ArrayList<>();
        list.add(i);
        list.add(j);
        reuslt.add(list);
        if(i == iMax && j == jMax) return 0;
        if(j < jMax && obstacleGrid[i][j + 1] == 0 && findPath(reuslt, i, j + 1, iMax, jMax, obstacleGrid) == 0) return 0;
        if(i < iMax && obstacleGrid[i + 1][j] == 0 && findPath(reuslt, i + 1, j, iMax, jMax, obstacleGrid) == 0) return 0;
        obstacleGrid[i][j] = 1;
        reuslt.remove(reuslt.size() - 1);
        return -1;
    }

}
```

> 复杂度分析

走迷宫，时间复杂度O(mn) 

使用了递归，空间复杂度O(m + n)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了99.84%的用户

内存消耗：39 MB, 在所有 Java 提交中击败了84.65%的用户
