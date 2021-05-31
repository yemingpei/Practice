### LeetCode-face-01-01

> 题目链接

[LeetCode-face-01-01](https://leetcode-cn.com/problems/is-unique-lcci/)

> 思路

用位运算保存字符是否出现过，如果出现过就直接返回false

> 代码

```java
class Solution {
    public boolean isUnique(String astr) {
        int flag = 0;
        for(int c : astr.toCharArray()){
            int mask = 1 << (c - 'a');
            if((mask & flag) == mask) return false;
            flag |= mask;
        }
        return true;
    }
}
```

> 复杂度分析

遍历了27个字符，时间复杂度O(1)

额外使用一个int值，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：36.2 MB, 在所有 Java 提交中击败了49.79%的用户
