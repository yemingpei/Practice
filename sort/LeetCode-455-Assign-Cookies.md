### LeetCode-455-Assign-Cookies

> 题目链接

[LeetCode-455-Assign-Cookies](https://leetcode.com/problems/assign-cookies/)

> 思路

先排序，然后利用贪心算法，尽可能喂饱前面的小朋友，胃小的

> 代码

```java
class Solution {
    public int findContentChildren(int[] g, int[] s) {
        int gLength = g.length;
        int sLength = s.length;
        Arrays.sort(g);
        Arrays.sort(s);
        int gStart = 0;
        int sStart = 0;
        int count = 0;
        while(gStart < gLength && sStart < sLength){
            if(g[gStart] <= s[sStart]){
                count++;
                gStart++;
                sStart++;
            }else sStart++;
        }
        return count;
    }
}
```

> 复杂度分析

系统排序，时间复杂度O(nlgn)

额外使用空间常数个变量，空间复杂度O(1)

> 总结

Runtime: 6 ms, faster than 98.83% of Java online submissions for Assign Cookies.

Memory Usage: 40 MB, less than 37.20% of Java online submissions for Assign Cookies.
