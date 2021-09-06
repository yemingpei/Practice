### LeetCode-face-17-18

> 题目链接

[LeetCode-face-17-18](https://leetcode-cn.com/problems/shortest-supersequence-lcci/)

> 思路

滑动窗口，首先右指针左移动，寻找全部数字，然后左指针缩小范围，依次不断交替移动

> 代码

```java
class Solution {
    public int[] shortestSeq(int[] big, int[] small) {
        int minWindow = big.length + 1;
        int[] smallCount = new int[small.length];
        Map<Integer, Integer> smallMap = new HashMap<>();
        for (int i = 0; i < small.length; i++) {
            smallMap.put(small[i], i);
        }
        int[] res = new int[2];
        int start = 0;
        int end = 0;
        int find = 0;
        while (end < big.length) {
            Integer integer = smallMap.get(big[end]);
            if (integer != null) {
                if (smallCount[integer] == 0) {
                    find++;
                }
                smallCount[integer]++;
            }
            while (find == small.length) {
                if (end - start < minWindow) {
                    minWindow = end - start;
                    res[0] = start;
                    res[1] = end;
                }
                Integer startIndx = smallMap.get(big[start]);
                if (startIndx != null) {
                    smallCount[startIndx]--;
                    if (smallCount[startIndx] == 0) {
                        find--;
                    }
                }
                start++;
            }
            end++;
        }
        return minWindow < big.length + 1 ? res : new int[0];
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用map，空间复杂度O(m)

> 总结

执行用时：18 ms, 在所有 Java 提交中击败了99.76%的用户

内存消耗：48.1 MB, 在所有 Java 提交中击败了91.77%的用户
