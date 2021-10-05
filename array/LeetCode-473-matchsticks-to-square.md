### LeetCode-473-matchsticks-to-square

> 题目链接

[LeetCode-473-matchsticks-to-square](https://leetcode-cn.com/problems/matchsticks-to-square/)

> 思路

先计算边长，然后深度搜索是否存在这样的边

> 代码

```java
class Solution {
    int sum = 0, cur = 0;
    int[] size = new int[4];
    public boolean makesquare(int[] matchsticks) {
        cur = matchsticks.length - 1;
        for (int num:matchsticks) sum += num;
        if (sum % 4 != 0 || sum == 0) return false;
        Arrays.sort(matchsticks);
        return dfs(matchsticks, cur);
    }
    public boolean dfs(int[] nums, int cur) {
        if (cur < 0) {
            if (size[0] == size[1] && size[1] == size[2] && size[2] == size[3]) return true;
            return false;
        }
        for (int i = 0; i < size.length; i++) {
            if (size[i] + nums[cur] > sum / 4 || (i > 0 && size[i] == size[i - 1])) continue;
            else {
                size[i] += nums[cur];
                if (dfs(nums, cur - 1)) return true;
                size[i] -= nums[cur];
            }
        }
        return false;
    }
}
```

> 复杂度分析

排序，时间复杂度O(n*2^n)

递归长度小于数组长度，空间复杂度O(n)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了99.58%的用户

内存消耗：35.9 MB, 在所有 Java 提交中击败了65.27%的用户
