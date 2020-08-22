### LeetCode-149-Max-Points-on-a-Line

> 题目链接

[LeetCode-149-Max-Points-on-a-Line](https://leetcode.com/problems/max-points-on-a-line/)

> 思路

每次选取一根线，然后通过比较通过该点的线的斜率来记录线上点的个数，最后再比较

> 代码

```java
class Solution {
    public int maxPoints(int[][] points) {
       if (points.length < 3) return points.length;
        int max = 0;
        for (int i = 0; i < points.length; i++) {
            int dup = 1;
            int localMax = 0;
            HashMap<String, Integer> map = new HashMap<>();
            for (int j = i + 1; j < points.length; j++) {
                int dx = points[j][0] - points[i][0], dy = points[j][1] - points[i][1];
                if (dx == 0 && dy == 0) dup++;
                else {
                    int gcd = gcd(dx, dy);
                    String slope = (dy / gcd) + "/" + (dx / gcd);
                    map.put(slope, map.getOrDefault(slope, 0) + 1);
                    localMax = Math.max(localMax, map.get(slope));
                }               
            }
            max = Math.max(max, dup + localMax);
        }
        return max;
    }
    private int gcd(int a, int b) {
        if (b == 0) return a;
        else return gcd(b, a % b);
    }
}
```

> 复杂度分析

遍历了n-1,n-2·····根线，时间复杂度O(n ^ 2)

额外使用了HashMap<String, Integer>来保存线,空间复杂度O(n ^ 2)

> 总结

Runtime: 15 ms, faster than 88.69% of Java online submissions for Max Points on a Line.

Memory Usage: 43.1 MB, less than 20.80% of Java online submissions for Max Points on a Line.
