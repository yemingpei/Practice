### LeetCode-519-random-flip-matrix

> 题目链接

[LeetCode-519-random-flip-matrix](https://leetcode-cn.com/problems/random-flip-matrix/)

> 思路

二维数组转变成一维数组，然后把随机的数字，置换到最后，记录置换的位置

> 代码

```java
class Solution {

    Map<Integer, Integer> V = new HashMap<>();
    int nr, nc, rem;
    Random rand = new Random();

    public Solution(int n_rows, int n_cols) {
        nr = n_rows;
        nc = n_cols;
        rem = nr * nc;
    }

    public int[] flip() {
        int r = rand.nextInt(rem--);
        int x = V.getOrDefault(r, r);
        V.put(r, V.getOrDefault(rem, rem));
        return new int[]{x / nc, x % nc};
    }

    public void reset() {
        V.clear();
        rem = nr * nc;
    }
}
```

> 复杂度分析

随机获取一个长度，时间复杂度O(1)

额外使用map，空间复杂度O(n)

> 总结

执行用时：28 ms, 在所有 Java 提交中击败了92.93%的用户

内存消耗：39 MB, 在所有 Java 提交中击败了89.90%的用户
