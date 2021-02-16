### LeetCode-459-Repeated-Substring-Pattern

> 题目链接

[LeetCode-459-Repeated-Substring-Pattern](https://leetcode.com/problems/repeated-substring-pattern/)

> 思路

质数只能由1来截取是否相同，其他因数则依次截取，验证

> 代码

```java
class Solution {
    public boolean repeatedSubstringPattern(String s) {
        return prime(s);
    }
    public boolean checkString(int prime, String s){
        int length = s.length();
        int start = 0;
        for(int i = prime; i < length; i++){
            if(s.charAt(start) != s.charAt(i)) return false;
            start++;
        }
        return true;
    }
    public boolean prime(String s){
        int n = s.length();
        if(n == 1) return false;
        if(n == 2) return checkString(1, s);
        if(n <= 3) return checkString(1, s);
        int k = (int)Math.sqrt(n);
        for(int i = 2; i <= k; i++){
           if(n % i == 0 && (checkString(i, s) || checkString(n / i, s))) return true;
        }
        return checkString(1, s);
   }
}
```

> 复杂度分析

一个数的因数的有限的，时间复杂度O(nlgn)

额外使用空间常数个变量，空间复杂度O(1)

> 总结

Runtime: 8 ms, faster than 75.81% of Java online submissions for Repeated Substring Pattern.

Memory Usage: 39.5 MB, less than 51.21% of Java online submissions for Repeated Substring Pattern.
