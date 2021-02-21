### LeetCode-440-K-th-Smallest-in-Lexicographical-Order

> 题目链接

[LeetCode-440-K-th-Smallest-in-Lexicographical-Order](https://leetcode.com/problems/k-th-smallest-in-lexicographical-order/)

> 思路

字典序排列，然后检索到第k个，输出

> 代码

```java
class Solution {
    public int findKthNumber(int n, int k) {
        int prefix = 1;
        int count = 1;
        while(count < k) {
            int curCount = countNode(prefix, n);
            if(curCount + count > k) {
                prefix *= 10;
                count++;
            } else {
                prefix++;
                count += curCount;
            }
        }
        return prefix;
    }
    private int countNode(int prefix, int n) {
        int count = 0;
        int nextPrefix = prefix + 1;
        while(prefix <= n) {
            count += Math.min(n + 1, nextPrefix) - prefix;
            if(prefix <= n / 10) {
                prefix *= 10;
                nextPrefix *= 10;
            } else {
                break;
            }
        }
        return count;
    }
}
```

> 复杂度分析

根据字典序来计算数字，时间复杂度O(n)

额外使用常数个int，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for K-th Smallest in Lexicographical Order.

Memory Usage: 37.5 MB, less than 12.44% of Java online submissions for K-th Smallest in Lexicographical Order.
