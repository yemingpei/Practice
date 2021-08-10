### LeetCode-face-16-14

> 题目链接

[LeetCode-face-16-14](https://leetcode-cn.com/problems/best-line-lcci/)

> 思路

选取点，然后计算其他点和这个点的链接，是否斜率相同

> 代码

```java
class Solution {
    public int[] bestLine(int[][] points) {
        int max = 0;
        Map<Double, int[]> map = new HashMap<>(points.length);
        int[] res = new int[]{0,1};
        for(int i = 0; i < points.length; i++) {
            map.clear();
            for(int j = i + 1; j < points.length; j++) {
                double dx = points[j][0] - points[i][0];
                double dy = (points[j][1] - points[i][1]);
                double k = 0;
                if(dx == 0) k = Double.MAX_VALUE;
                else if(dy == 0) k = 0;
                else k = dy / dx; 
                int[] cur = map.get(k);
                if(cur == null) {
                    cur = new int[]{j, 1};
                    map.put(k, cur);
                }else {
                    cur[1]++;
                    if(cur[1] > max) {
                        max = cur[1];
                        res[0] = i;
                        res[1] = cur[0];
                    }
                }
            }
        }
        return res;
    }
}
```

> 复杂度分析

需要双重遍历数组，时间复杂度O(n ^ 2)

额外使用map辅助，空间复杂度O(n)

> 总结

执行用时：19 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：39 MB, 在所有 Java 提交中击败了42.95%的用户
