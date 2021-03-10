### LeetCode-447-Number-of-Boomerangs

> 题目链接

[LeetCode-447-Number-of-Boomerangs](https://leetcode.com/problems/number-of-boomerangs/)

> 思路

用map来记录计算过的距离，避免重复计算，单方向，然后最后* 2，为两个方向交换是另一组解

> 代码

```java
class Solution {
    public int numberOfBoomerangs(int[][] points) {
        int ret = 0;
        Map<Integer,Integer> dist2point = new HashMap<Integer,Integer>();
        for(int i=0;i<points.length;i++){
            for(int j=0;j<points.length;j++){
                if(i == j) continue;
                int numOfPoints = dist2point.merge((points[i][0] - points[j][0]) * (points[i][0] - points[j][0]) + (points[i][1] - points[j][1]) * (points[i][1] - points[j][1]), 1, Integer::sum);
                ret += (numOfPoints-1);                                                     
             }
             dist2point.clear();
         }
         return ret * 2;
    }
}
```

> 复杂度分析

双重遍历点，时间复杂度O(n ^ 2)

额外使用Map来辅助，空间复杂度O(n)

> 总结

Runtime: 53 ms, faster than 98.58% of Java online submissions for Number of Boomerangs.

Memory Usage: 38.6 MB, less than 89.01% of Java online submissions for Number of Boomerangs.
