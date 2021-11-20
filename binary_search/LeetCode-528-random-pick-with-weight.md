### LeetCode-528-random-pick-with-weight

> 题目链接

[LeetCode-528-random-pick-with-weight](https://leetcode-cn.com/problems/random-pick-with-weight/)

> 思路

利用二分查找，逆向寻找目标

> 代码

```java
class Solution {
    int[] data;
    int max;
    public Solution(int[] w) {
        int len = w.length;
        data = new int[len];
        data[0] = 0;
        for(int i = 1; i < len; i++) {
            data[i] = data[i-1] + w[i-1];
        }
        max = data[len - 1] + w[len - 1];
    }
    public int pickIndex() {
        int target = ThreadLocalRandom.current().nextInt(0, max);
        int l = 0, r = data.length - 1;
        while (l < r) {
            int mid = (l + r + 1) >> 1;
            if(data[mid] <= target) l = mid;
            else r = mid - 1;
        }
        return l;
    }
}
```

> 复杂度分析

初始化，时间复杂度O(n)，pickIndex，时间复杂度O(logn)

额外使用数组，空间复杂度O(n)

> 总结

执行用时：23 ms, 在所有 Java 提交中击败了97.68%的用户

内存消耗：43.5 MB, 在所有 Java 提交中击败了32.68%的用户
