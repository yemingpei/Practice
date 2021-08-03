### LeetCode-face-16-06

> 题目链接

[LeetCode-face-16-06](https://leetcode-cn.com/problems/smallest-difference-lcci/)

> 思路

先排序，然后从开头开始比较，小的一方，先增加，往右移

> 代码

```java
class Solution {
    public int smallestDifference(int[] a, int[] b) {
        int n = a.length;
        int m = b.length;
        Arrays.sort(a);
        Arrays.sort(b);
        int i = 0, j = 0;
        long result = Long.MAX_VALUE;
        while(i < n && j < m){
            result = Math.min(result, Math.abs((long)a[i] - b[j]));
            if(a[i] > b[j]) j++;
            else i++;
        }
        return (int)result;
    }
}
```

> 复杂度分析

排序用时nlogn，时间复杂度O(nlogn)

额外使用int值，空间复杂度O(1)

> 总结

执行用时：20 ms, 在所有 Java 提交中击败了94.88%的用户

内存消耗：46.5 MB, 在所有 Java 提交中击败了19.73%的用户
