### LeetCode-42-Trapping-Rain-Water

> 题目链接

[LeetCode-42-Trapping-Rain-Water](https://leetcode.com/problems/trapping-rain-water/)

> 思路

```java
//例子1 [2,0,0,0,0,0,1]
//例子2 [0,0,3,0,4,0,0]
//例子3 [2,0,3,0,4,0,1]
```
先看例子1：左边高度2，右边高度1，以高度为1的挡板为最小高度装水
再看例子2：左边的0，和右边的0都无法装水，只有3和4之间可以装水，以3为高装的水
最后看例子3，把例子2的3，4两个挡板插在1之间就变成例子3，装水区域就分成2和3；3和4；4和1三个区域都是以低的挡板为水的高度
综上所述，就是左右两个指针往中间移动，哪个小就移动哪一个，记录左右最大值，读取到数值比最大值小，就计算水，比最大值大，就更新最大值

> 代码

```java
class Solution {
    public int trap(int[] height) {
        if (height.length < 3) return 0;
        int left = 0;
        int right = height.length - 1;
        int leftMax = height[left];
        int rightMax = height[right];
        int sum = 0;
        while (left < right) {
          if (height[left] > height[right]) {
            if (height[right] < rightMax) {
              sum += rightMax - height[right];
            } else {
              rightMax = height[right];
            }
            right--;
          } else {
            if (height[left] < leftMax) {
              sum += leftMax - height[left];
            } else {
              leftMax = height[left];
            }
            left++;
          }
        }
        return sum;
    }
}
```

> 复杂度分析

for循环遍历了一遍数组，时间复杂度O(n)

额外使用了5个变量，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 93.26% of Java online submissions for Trapping Rain Water.
Memory Usage: 39.8 MB, less than 19.87% of Java online submissions for Trapping Rain Water.
