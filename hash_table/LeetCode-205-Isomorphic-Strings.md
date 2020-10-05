### LeetCode-205-Isomorphic-Strings

> 题目链接

[LeetCode-205-Isomorphic-Strings](https://leetcode.com/problems/isomorphic-strings/)

> 思路

先保存数组的数，建立hash表，然后开始遍历，通过比较map的关系，是否有重复，来校验是否能转换

> 代码

```java
class Solution {
    public boolean isIsomorphic(String s, String t) {
        HashMap<Character, Character> map = new HashMap<>();
        for (int i = 0; i < s.length(); i++) {
            char ch1 = s.charAt(i);
            char ch2 = t.charAt(i);
            if (map.containsKey(ch1)) {
                if (map.get(ch1) != ch2) {
                    return false;
                }
            }
            else {
                if (map.containsValue(ch2)) { 
                    return false;
                } else {
                    map.put(ch1, ch2);
                }
            }
        }
        return true;  
    }
}
```

> 复杂度分析

遍历两个等长度的序列，时间复杂度O(n)

额外使用hashMap来保存数据，空间复杂度O(n)

> 总结

Runtime: 6 ms, faster than 77.27% of Java online submissions for Isomorphic Strings.

Memory Usage: 39.2 MB, less than 89.68% of Java online submissions for Isomorphic Strings.
