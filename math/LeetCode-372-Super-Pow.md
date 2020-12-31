### LeetCode-372-Super-Pow

> 题目链接

[LeetCode-372-Super-Pow](https://leetcode.com/problems/super-pow/)

> 思路

根据中国余数定理，1337可以拆分为191和7，则可以快速找到简化的余数，避免a过大，产生大数

> 代码

```java
class Solution {
    int divisor = 1337;
    public int superPow(int a, int[] b) {
        a = a % divisor;
        int period = findPeriod(a);
        int B = 0;
        for (int i = 0; i < b.length; i++) {
            B = (B * 10 + b[i]) % period;
        }
        int res = 1;
        int base = a;
        while (B != 0) {
           res = (res * (power(base, B % 10))) % divisor;
           B = B / 10;
           base = power(base, 10);
        }
        return res;
  }
    
  private int power(int base, int exponent) {
      int power = 1;
      for (int i = 0; i < exponent; i++) {
          power = (power * base) % divisor;
      }
      return power;
  }
    
  private int findPeriod(int a) {
      if ((a % 191) == 0) return 6;
      if ((a % 7) == 0) return 190;
      return 570;
  }
}
```

> 复杂度分析

遍历幂数组，时间复杂度O(n)

额外使用四个int类型的变量，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Super Pow.

Memory Usage: 38.9 MB, less than 94.53% of Java online submissions for Super Pow.
