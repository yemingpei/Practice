### LeetCode-face-05-08

> 题目链接

[LeetCode-face-05-08](https://leetcode-cn.com/problems/draw-line-lcci/)

> 思路

看题目没有看懂，附上别人的说明 https://leetcode-cn.com/problems/draw-line-lcci/solution/javawei-yun-suan-by-loser-11/

> 代码

```java
class Solution {
    public int[] drawLine(int length, int w, int x1, int x2, int y) {
        int[] ans = new int[length];
        int low = (y * w + x1) / 32;
        int high = (y * w + x2) / 32;
        for(int i = low; i <= high; i++){
            ans[i] = -1;
        }
        ans[low] = ans[low] >>> x1 % 32;
        ans[high] = ans[high] & Integer.MIN_VALUE >> x2 % 32;
        return ans;
    }
}
```

> 复杂度分析

遍历n次，时间复杂度O(n) 

额外使用int数组，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.8 MB, 在所有 Java 提交中击败了78.09%的用户
