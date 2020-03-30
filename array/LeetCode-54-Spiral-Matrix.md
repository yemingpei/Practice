### LeetCode-54-Spiral-Matrix

> 题目链接

[LeetCode-54-Spiral-Matrix](https://leetcode.com/problems/spiral-matrix/)

> 思路

先找出左边界，右边界，上边界和下边界，遍历的顺序为先左到右，调整上边界，然后上到下，调整右边界，然后右到左，调整下边界，最后下到上，调整左边界，当边界大小关系不正确则循环结束

> 代码

```java
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> ans = new ArrayList<Integer>();
        int vertical = matrix.length;
        if(vertical==0) return ans;
		int horizontal = matrix[0].length;
		int bottom = vertical - 1;
		int right = horizontal - 1;
		int left = 0;
		int top = 0;

		int circle = (Math.min(horizontal, vertical) + 1) / 2;
		for (int j = 0; j < circle; j++) {
			for (int i = left; i <= right; i++) {
				ans.add(matrix[top][i]);
			}
			top++;
			if (top > bottom) break;
			for (int i = top; i <= bottom; i++) {
				ans.add(matrix[i][right]);
			}
			right--;
			if (left > right) break;
			for (int i = right; i >= left; i--) {
				ans.add(matrix[bottom][i]);
			}
			bottom--;
			if (top > bottom) break;
			for (int i = bottom; i >= top; i--) {
				ans.add(matrix[i][left]);
			}
			left++;
		}
		return ans;
    }
}
```

> 复杂度分析

for循环遍历了一遍二维数组，时间复杂度O(n^2)

额外使用了int类型的几个变量，空间复杂度为O(1)

> 总结

Runtime: 0 ms
Memory Usage: 37.7 MB
