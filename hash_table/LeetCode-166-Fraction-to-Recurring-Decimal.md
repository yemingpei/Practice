### LeetCode-166-Fraction-to-Recurring-Decimal

> 题目链接

[LeetCode-166-Fraction-to-Recurring-Decimal](https://leetcode.com/problems/fraction-to-recurring-decimal/)

> 思路

用map来记录余数的位置，得到重复的position，循环到余数为0，或者余数重复

> 代码

```java
class Solution {
    public String fractionToDecimal(int numerator, int denominator) {
          long a = numerator, b = denominator;
          if(b == 0) return "NULL";
          if(a == 0) return "0";
          StringBuilder rs = new StringBuilder();
          HashMap<Long, Integer> pos = new HashMap<>();
          if(a < 0 && b > 0 || a > 0 && b < 0) rs.append("-");
          a = Math.abs(a); b = Math.abs(b);
          rs.append(a/b);
          long rem = a % b;
          if(rem == 0) return rs.toString();
          rs.append(".");
          pos.put(rem, rs.length());
          while(rem > 0) {
            rem *= 10;
            rs.append(rem/b);
            rem = rem%b;
            if(pos.containsKey(rem)) {
              rs.insert(pos.get(rem), "(");
              rs.append(")");
              break;
            } else pos.put(rem, rs.length());
          }
          return rs.toString();
    }
}
```

> 复杂度分析

循环到余数为0，或者余数重复，时间复杂度O(m)

额外使用hashMap来保存数据，空间复杂度O(m),m是除数

> 总结

Runtime: 1 ms, faster than 99.92% of Java online submissions for Fraction to Recurring Decimal.

Memory Usage: 36.5 MB, less than 96.53% of Java online submissions for Fraction to Recurring Decimal.
