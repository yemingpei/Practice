### LeetCode-60

> 题目链接

[LeetCode-60(https://leetcode.com/problems/sqrtx/)

> 思路

利用k和n!的关系来推算每个位置的数字

> 代码

```java
class Solution {
    public String getPermutation(int n, int k) {
        StringBuilder sb = new StringBuilder();
        List<Integer> candidates = new ArrayList<>();
        int[] factorials = new int[n+1];
        factorials[0] = 1;
        int fact = 1;
        for(int i = 1; i <= n; ++i) {
            candidates.add(i);
            fact *= i;
            factorials[i] = fact;
        }
        k -= 1;
        for(int i = n-1; i >= 0; --i) {
            int index = k / factorials[i];
            sb.append(candidates.remove(index));
            k -= index*factorials[i];
        }
        return sb.toString();
    }
}
```

> 复杂度分析

利用k和n!的关系推算，时间复杂度O( n ^ 2)

额外使用长度为n的数组辅助，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 100% of Java online submissions for Sqrt(x).

Memory Usage: 36.8 MB, less than 51.81% of Java online submissions for Sqrt(x).
