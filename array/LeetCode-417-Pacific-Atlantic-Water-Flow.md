### LeetCode-417-Pacific-Atlantic-Water-Flow

> 题目链接

[LeetCode-417-Pacific-Atlantic-Water-Flow](https://leetcode.com/problems/pacific-atlantic-water-flow/)

> 思路

从左和上边界开始，寻找更大的数，标记为可达，然后再从下边界和右边界开始寻找更大的数，和之前可达的，就是要添加的值

> 代码

```java
class Solution {
    public List<List<Integer>> pacificAtlantic(int[][] matrix) {
        List<List<Integer>> result = new ArrayList<>();
        int cloumn = matrix.length;
        if(cloumn == 0) return result;
        int horizontal = matrix[0].length;
        if(horizontal == 0) return result;
        boolean[][] pacific = new boolean[cloumn][horizontal];
        boolean[][] atlantic = new boolean[cloumn][horizontal];
        for(int i = 0; i < cloumn; i++)
            dfs(pacific, i, 0, matrix, cloumn - 1, horizontal - 1);
        for(int j = 0; j < horizontal; j++)
            dfs(pacific, 0, j, matrix, cloumn - 1, horizontal - 1);
        for(int i = cloumn - 1; i >= 0; i--)
            reDfs(atlantic, i, horizontal - 1, matrix, pacific, result, cloumn - 1, horizontal - 1);
        for(int j = horizontal - 1; j >= 0; j--)
            reDfs(atlantic, cloumn - 1, j, matrix, pacific, result, cloumn - 1, horizontal - 1);
        return result;
    }
    public void dfs(boolean[][] pacific, int i, int j,int[][] matrix,int cloumn, int horizontal){
        if(pacific[i][j]) return;
        pacific[i][j] = true;
        if(i < cloumn && !pacific[i + 1][j] && matrix[i + 1][j] >= matrix[i][j])
            dfs(pacific, i + 1, j, matrix, cloumn, horizontal);
        if(i > 0 && !pacific[i - 1][j] && matrix[i - 1][j] >= matrix[i][j])
            dfs(pacific, i - 1, j, matrix, cloumn, horizontal);
        if(j < horizontal && !pacific[i][j + 1] && matrix[i][j + 1] >= matrix[i][j])
            dfs(pacific, i, j + 1, matrix, cloumn, horizontal);
        if(j > 0 && !pacific[i][j - 1] && matrix[i][j - 1] >= matrix[i][j])
            dfs(pacific, i, j - 1, matrix, cloumn, horizontal);
    }
    public void reDfs(boolean[][] atlantic, int i, int j,int[][] matrix, boolean[][] pacific, List<List<Integer>> result, int cloumn, int horizontal){
        if(atlantic[i][j]) return;
        atlantic[i][j] = true;
        if(pacific[i][j]){
            List<Integer> list = new ArrayList<>();
            list.add(i);
            list.add(j);
            result.add(list);
        }
        if(i > 0 && !atlantic[i - 1][j] && matrix[i - 1][j] >= matrix[i][j])
            reDfs(atlantic, i - 1, j, matrix, pacific, result, cloumn, horizontal);
        if(i < cloumn && !atlantic[i + 1][j] && matrix[i + 1][j] >= matrix[i][j])
            reDfs(atlantic, i + 1, j, matrix, pacific, result, cloumn, horizontal);
        if(j > 0 && !atlantic[i][j - 1] && matrix[i][j - 1] >= matrix[i][j])
            reDfs(atlantic, i, j - 1, matrix, pacific, result, cloumn, horizontal);
        if(j < horizontal && !atlantic[i][j + 1] && matrix[i][j + 1] >= matrix[i][j])
            reDfs(atlantic, i, j + 1, matrix, pacific, result, cloumn, horizontal);
    }
}
```

> 复杂度分析

深度遍历，数组都需要检测，时间复杂度O(n ^ 2)

额外boolean数组，空间复杂度O(n ^ 2)。

> 总结

Runtime: 2 ms, faster than 100.00% of Java online submissions for Pacific Atlantic Water Flow.

Memory Usage: 40.1 MB, less than 84.75% of Java online submissions for Pacific Atlantic Water Flow.
