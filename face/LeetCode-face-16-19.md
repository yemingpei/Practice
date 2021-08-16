### LeetCode-face-16-19

> 题目链接

[LeetCode-face-16-19](https://leetcode-cn.com/problems/pond-sizes-lcci/)

> 思路

dfs深度检索，统计之后，修改0为-1，避免无限循环

> 代码

```java
class Solution {
    public int[] pondSizes(int[][] land) {
        List<Integer> list = new ArrayList<>();
        int row = land.length;
        int column = land[0].length;
        for(int i = 0; i < row; i++)
            for(int j = 0; j < column; j++){
                if(land[i][j] == 0) list.add(getLand(i, j, row - 1, column - 1, land));
            }
        int[] result = new int[list.size()];
        for(int i = 0; i < list.size(); i++) result[i] = list.get(i);
        Arrays.sort(result);
        return result;
    }
    public int getLand(int i, int j, int xMax, int yMax, int[][] land){
        int number = 1;
        land[i][j] = -1;
        if(i > 0 && land[i - 1][j] == 0) number += getLand(i - 1, j, xMax, yMax, land);
        if(j > 0 && land[i][j - 1] == 0) number += getLand(i, j - 1, xMax, yMax, land);
        if(j > 0 && i > 0 && land[i - 1][j - 1] == 0) number += getLand(i - 1, j - 1, xMax, yMax, land);
        if(i < xMax && land[i + 1][j] == 0) number += getLand(i + 1, j, xMax, yMax, land);
        if(j < yMax && land[i][j + 1] == 0) number += getLand(i, j + 1, xMax, yMax, land);
        if(i < xMax && j < yMax && land[i + 1][j + 1] == 0) number += getLand(i + 1, j + 1, xMax, yMax, land);
        if(i < xMax && j > 0 && land[i + 1][j - 1] == 0) number += getLand(i + 1, j - 1, xMax, yMax, land);
        if(i > 0 && j < yMax && land[i - 1][j + 1] == 0) number += getLand(i - 1, j + 1, xMax, yMax, land);
        return number;
    }
}
```

> 复杂度分析

遍历二维数组，时间复杂度O(mn)

额外使用list的变量，空间复杂度O(n)

> 总结

执行用时：6 ms, 在所有 Java 提交中击败了99.86%的用户

内存消耗：62.7 MB, 在所有 Java 提交中击败了67.15%的用户
