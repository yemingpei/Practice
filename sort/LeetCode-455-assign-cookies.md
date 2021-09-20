### LeetCode-455-assign-cookies

> 题目链接

[LeetCode-455-assign-cookies](https://leetcode-cn.com/problems/assign-cookies/)

> 思路

先排序，然后根据贪心算法从需求高的孩子开始满足

> 代码

```java
class Solution {
    public int findContentChildren(int[] g, int[] s) {
        Arrays.sort(g);
        Arrays.sort(s);
        int count = 0;
        int right = s.length - 1;
        int left = g.length - 1;
        while(left >= 0 && right >= 0){
            if(g[left] <= s[right]){
                right--;
                count++;
            }
            left--;
        }
        return count;
    }
}
```

> 复杂度分析

遍历两个数组，时间复杂度O(m + n)

额外使用int，空间复杂度O(1)

> 总结

执行用时：7 ms, 在所有 Java 提交中击败了99.73%的用户

内存消耗：39 MB, 在所有 Java 提交中击败了77.25%的用户
