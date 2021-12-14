### LeetCode-564-find-the-closest-palindrome

> 题目链接

[LeetCode-564-find-the-closest-palindrome](https://leetcode-cn.com/problems/find-the-closest-palindrome/)

> 思路

先计算一个最大和最小的数先保存，然后利用前半部分拼接的方式，来保证

> 代码

```java
class Solution {
    public String nearestPalindromic(String n) {
        int len = n.length();
        Set<Long> set = new HashSet<>();
        set.add((long)Math.pow(10, len - 1) - 1);
        set.add((long)Math.pow(10, len) + 1);
        long m = Long.parseLong(n.substring(0, (len + 1) / 2));
        for(long i = m - 1; i <= m + 1; i++){
            String a = Long.toString(i);
            String b = new StringBuilder(Long.toString(i)).reverse().toString();
            if (len % 2 == 1){
                String rb = b.substring(1, b.length());
                set.add(Long.parseLong(a + rb));
            }else{
                set.add(Long.parseLong((a + b)));
            }
        }
        long curNum = Long.parseLong(n);
        if (set.contains(curNum)) set.remove(curNum);
        long res = (long) 2e18;
        for (long x : set) {
            if (Math.abs(x - curNum) < Math.abs(res - curNum))
                res = x;  
            else if (Math.abs(x - curNum) == Math.abs(res - curNum))
                res = Math.min(res, x);
        }
        return String.valueOf(res);
    }
}
```

> 复杂度分析

利用回文拼接的方式，时间复杂度O(n)

额外使用set，空间复杂度O(n)

> 总结

执行用时：3 ms, 在所有 Java 提交中击败了79.67%的用户

内存消耗：36.6 MB, 在所有 Java 提交中击败了96.75%的用户
