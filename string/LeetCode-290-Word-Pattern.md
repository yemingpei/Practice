### LeetCode-290-Word-Pattern

> 题目链接

[LeetCode-290-Word-Pattern](https://leetcode.com/problems/word-pattern/)

> 思路

寻找pattern和s的映射关系，如果关系冲突就提前结束

> 代码

```java
class Solution {
    public boolean wordPattern(String pattern, String s) {
        String[] words = s.split(" ");
        if (words.length != pattern.length())
            return false;
        Map index = new HashMap();
        for (Integer i = 0; i < words.length; ++i)
            if (index.put(pattern.charAt(i), i) != index.put(words[i], i))
                return false;
        return true;
    }
}
```

> 复杂度分析

循环遍历两个字符串，时间复杂度O(n)

额外使用Map保存结果，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 77.07% of Java online submissions for Word Pattern.

Memory Usage: 36.5 MB, less than 98.11% of Java online submissions for Word Pattern.
