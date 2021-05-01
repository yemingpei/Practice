### LeetCode-offer-48

> 题目链接

[LeetCode-offer-48](https://leetcode-cn.com/problems/zui-chang-bu-han-zhong-fu-zi-fu-de-zi-zi-fu-chuan-lcof/)

> 思路

记录每个字符的位置，然后不断更变左边界，算出最大的子串的长度

> 代码

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        Map<Character, Integer> dic = new HashMap<>(343);
        int i = -1, res = 0;
        for(int j = 0; j < s.length(); j++) {
            if(dic.containsKey(s.charAt(j)))
                i = Math.max(i, dic.get(s.charAt(j)));
            dic.put(s.charAt(j), j);
            res = Math.max(res, j - i);
        }
        return res;
    }
}
```

> 复杂度分析

遍历字符串，时间复杂度O(n)

额外使用map来记录位置，空间复杂度O(n)

> 总结

执行用时：6 ms, 在所有 Java 提交中击败了89.04%的用户

内存消耗：38.8 MB, 在所有 Java 提交中击败了15.01%的用户
