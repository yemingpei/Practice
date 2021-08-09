### LeetCode-face-16-11

> 题目链接

[LeetCode-face-16-11](https://leetcode-cn.com/problems/bisect-squares-lcci/)

> 思路

只有两个选择，不断更换不同比值，达到全部组合的效果

> 代码

```java
class Solution {
    public int[] divingBoard(int shorter, int longer, int k) {
        if(k == 0) return new int[0];
        int sum = shorter * k;
        if(longer == shorter) return new int[]{ sum };
        int[] result = new int[k + 1];
        int change = longer - shorter;
        for(int i = 0; i <= k; i++){
            result[i] = sum;
            sum += change;
        }
        return result;
    }
}
```

> 复杂度分析

需要遍历k + 1次，时间复杂度O(k)

额外使用int变量，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：46.3 MB, 在所有 Java 提交中击败了29.45%的用户
