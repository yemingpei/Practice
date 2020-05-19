### LeetCode-202-Happy-Number

> 题目链接

[LeetCode-202-Happy-Number](https://leetcode.com/problems/happy-number/)

> 思路

计算并保存数据，如果出现相同，则表示有循环，退出

> 代码

```java
class Solution {
    public boolean isHappy(int n) {
        Set<Integer> seen = new HashSet<Integer>();
        while (n != 1) {
          if (seen.contains(n)) return false;
          seen.add(n);
          int sum = 0;
          while (n != 0) {
            int reminder = n % 10;
            n = n / 10;
            sum += reminder * reminder;
          }
          n = sum;  
        }
        return true;
    }
}
```

> 复杂度分析

for循环遍历了整数计算，时间复杂度O(n)

额外使用了HashSet,空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 84.19% of Java online submissions for Happy Number.

Memory Usage: 36.4 MB, less than 6.06% of Java online submissions for Happy Number.
