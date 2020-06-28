### LeetCode-1178-Number-of-Valid-Words-for-Each-Puzzle

> 题目链接

[LeetCode-1178-Number-of-Valid-Words-for-Each-Puzzle](https://leetcode.com/problems/number-of-valid-words-for-each-puzzle/)

> 思路

使用暴力法一一比较，用位运算节省比较的时间

> 代码

```java
class Solution {
    public List<Integer> findNumOfValidWords(String[] words, String[] puzzles) {
        Map<Integer, Integer> map = new HashMap<>();
        for (String w : words) {
            int mask = 0;
            for (char ch : w.toCharArray()) {
                mask |= 1 << (ch - 'a');
            }
            map.put(mask, map.getOrDefault(mask, 0) + 1);
        }
        List<Integer> res = new LinkedList<>();
        for (String p : puzzles) {
            int mask = 0;
            for (char ch : p.toCharArray()) {
                mask |= 1 << (ch - 'a');
            }
            int first = 1 << (p.charAt(0) - 'a');
            int sub = mask;
            int count = 0;
            while(sub != 0) {
                if ((first & sub) != 0 && map.containsKey(sub)) {
                    count += map.get(sub);
                }
                sub = (sub - 1) & mask;
            }
            res.add(count);
        }
        return res;
    }
}
```

> 复杂度分析

使用暴力法，每个字串一一比较，时间复杂度O(n * m)

额外使用List<Integer>辅助完成，空间复杂度O(n)

> 总结

Runtime: 67 ms, faster than 91.67% of Java online submissions for Number of Valid Words for Each Puzzle.

Memory Usage: 56.9 MB, less than 47.50% of Java online submissions for Number of Valid Words for Each Puzzle.
