### LeetCode-174-Dungeon-Game

> 题目链接

[LeetCode-174-Dungeon-Game](https://leetcode.com/problems/dungeon-game/)

> 思路

典型的动态规划，求起始地血量，就是求坐标（0，0）的值，那（n-1,m-1）的值最小为1，如果（n-1,m-1）为负数，则需要 1- dungeon[n-1,m-1]，动态规划推导公式
为 knight[i,j] = max(min( knight[i,j+1], knight[i+1,j])-dungeon[i,j],1),寻找右边和下面的最小值，减去原数组位置的值，如果为负数，则证明此格子为加血
重置为0


> 代码

```java
class Solution {
    public int calculateMinimumHP(int[][] dungeon) {
        int row = dungeon.length;
        int column = dungeon[0].length;
        int[][] knight = new int[row][column];
        knight[row - 1][column - 1] = Math.max(1 - dungeon[row - 1][column - 1], 1);
        for (int i = column - 2; i >= 0; i--) {
            knight[row - 1][i] = Math.max(knight[row - 1][i + 1] - dungeon[row - 1][i], 1);
        }
        for (int i = row - 2; i >= 0; i--) {
            knight[i][column - 1] = Math.max(knight[i + 1][column - 1] - dungeon[i][column - 1], 1);
        }
        for (int i = row - 2; i >= 0; i--)
            for (int j = column - 2; j >= 0; j--) {
                knight[i][j] = Math.max(Math.min(knight[i][j + 1], knight[i + 1][j]) - dungeon[i][j], 1);
            }
        return knight[0][0];
    }
}
```

> 复杂度分析

动态规划，由最后的位置，推断出（0，0）的位置，时间复杂度O(mn)

额外使用了n * m的数组，空间复杂度O(mn)

> 总结

Runtime: 1 ms, faster than 93.39% of Java online submissions for Dungeon Game.

Memory Usage: 39 MB, less than 88.24% of Java online submissions for Dungeon Game.
