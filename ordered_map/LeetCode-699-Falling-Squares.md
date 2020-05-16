### LeetCode-699-Falling-Squares

> 题目链接

[LeetCode-699-Falling-Squares](https://leetcode.com/problems/falling-squares/)

> 思路

双重for循环，模拟俄罗斯方块掉下的情景

> 代码

```java
class Solution {
    public List<Integer> fallingSquares(int[][] positions) {
        List<Integer> result = new ArrayList();
        int max = 0;
        int[] height = new int[positions.length];
        for (int i = 0; i < positions.length; i++) {
          int left = positions[i][0];
          int size = positions[i][1];
          int right = left + size;
          height[i] += size;
          for (int j = i + 1; j < positions.length; j++) {
            int left2 = positions[j][0];
            int size2 = positions[j][1];
            int right2 = left2 + size2;
            if (left2 < right && left < right2) {
              height[j] = Math.max(height[j], height[i]);
            }
          }
          max = Math.max(max, height[i]);
          result.add(max);
        }
        return result;
    }
}
```

> 复杂度分析

双重for循环遍历，时间复杂度O(n^2)

额外使用了height的辅助数组，空间复杂度O(n)

> 总结

Runtime: 21 ms, faster than 70.65% of Java online submissions for Falling Squares.

Memory Usage: 39.9 MB, less than 100.00% of Java online submissions for Falling Squares.
