### LeetCode-520-detect-capital

> 题目链接

[LeetCode-520-detect-capital](https://leetcode-cn.com/problems/detect-capital/)

> 思路

先比较第一第二个字符是否相等，然后比较第二个是否与后面的都一致

> 代码

```java
class Solution {
    public boolean detectCapitalUse(String word) {
        if (word.length() >= 2 && Character.isLowerCase(word.charAt(0)) && Character.isUpperCase(word.charAt(1))) {
            return false;
        }
        for (int i = 2; i < word.length(); ++i) {
            if (Character.isLowerCase(word.charAt(i)) ^ Character.isLowerCase(word.charAt(1))) {
                return false;
            }
        }
        return true;
    }
}
```

> 复杂度分析

遍历字符串，时间复杂度O(n)

无额外使用变量，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了98.19%的用户

内存消耗：36.6 MB, 在所有 Java 提交中击败了84.96%的用户
