### LeetCode-84-Largest-Rectangle-in-Histogram

> 题目链接

[LeetCode-84-Largest-Rectangle-in-Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/)

> 思路

计算出每个位置的左边最小，右边最小，然后再遍历，计算面积

> 代码

```java
class Solution {
    public int largestRectangleArea(int[] heights) {
        if(heights == null || heights.length == 0){
            return 0;
        }
        int[] leftLess = new int[heights.length];
        int[] rightLess = new int[heights.length];
        leftLess[0] = -1;
        rightLess[heights.length - 1] = heights.length;
        for(int i = 1; i < leftLess.length; i++){
            int j = i - 1;
            while(j >= 0 && heights[j] >= heights[i]){
                j = leftLess[j];
            }
            leftLess[i] = j;
        }
        for(int i = heights.length - 2; i >= 0; i--){
            int j = i + 1;
            while(j < heights.length && heights[j] >= heights[i]){
                j = rightLess[j];
            }
            rightLess[i] = j;
        }
        int max = 0;
        for(int i = 0; i < heights.length; i++){
            int area = (rightLess[i] - leftLess[i] - 1) * heights[i];
            max = Math.max(max,area);
        }
        return max;
    }
}
```

> 复杂度分析

for循环遍历了三遍数组，时间复杂度O(n)

额外使用了左右两个数组，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 99.77% of Java online submissions for Largest Rectangle in Histogram.

Memory Usage: 41 MB, less than 38.41% of Java online submissions for Largest Rectangle in Histogram.
