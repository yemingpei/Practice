### LeetCode-187-Repeated-DNA-Sequences

> 题目链接

[LeetCode-187-Repeated-DNA-Sequences](https://leetcode.com/problems/repeated-dna-sequences/)

> 思路

用map存储数组，到达2就输出，其他情况跳过

> 代码

```java
class Solution {
    public List<String> findRepeatedDnaSequences(String s) {
        List<String> result = new ArrayList<>();
        Map<String, Integer> map = new HashMap<>();
        if (s.length() < 11) return result;
        for (int i = 10; i <= s.length(); i++) {
          String word = s.substring(i - 10, i);
          Integer k = map.get(word);
          if (k == null) { map.put(word, 1);
          } else if (k == 1) {
            result.add(word);
            map.put(word, 2);
          }
        }
        return result;
    }
}
```

> 复杂度分析

for循环遍历了一遍数组，时间复杂度O(n)

额外使用了HashMap，空间复杂度O(n)

> 总结

Runtime: 10 ms, faster than 92.85% of Java online submissions for Repeated DNA Sequences.

Memory Usage: 40 MB, less than 100.00% of Java online submissions for Repeated DNA Sequences.
