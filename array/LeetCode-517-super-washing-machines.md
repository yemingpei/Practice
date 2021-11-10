### LeetCode-517-super-washing-machines

> 题目链接

[LeetCode-517-super-washing-machines](https://leetcode-cn.com/problems/super-washing-machines/)

> 思路

因为每一轮值可以移动一件衣服，且每个点都动，单独的洗衣机可以借出去的数量，还有一个是连续的洗衣机需要借的数量，利用贪心算法

> 代码

```java
class Solution {
    public int findMinMoves(int[] machines) {
        int tot = Arrays.stream(machines).sum();
        int n = machines.length;
        if (tot % n != 0) {
            return -1;
        }
        int avg = tot / n;
        int ans = 0, sum = 0;
        for (int num : machines) {
            num -= avg;
            sum += num;
            ans = Math.max(ans, Math.max(Math.abs(sum), num));
        }
        return ans;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

无额外使用变量，空间复杂度O(1)

> 总结

执行用时：3 ms, 在所有 Java 提交中击败了46.54%的用户

内存消耗：39 MB, 在所有 Java 提交中击败了83.08%的用户
