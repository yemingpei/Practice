### LeetCode-412-Fizz-Buzz

> 题目链接

[LeetCode-412-Fizz-Buzz](https://leetcode.com/problems/fizz-buzz/)

> 思路

暴力法，循环遍历n组装需要组合的数字

> 代码

```java
class Solution {
    public List<String> fizzBuzz(int n) {
        List<String> ans = new ArrayList<String>();
        for (int num = 1; num <= n; num++) {
            boolean divisibleBy3 = (num % 3 == 0);
            boolean divisibleBy5 = (num % 5 == 0);
            StringBuilder numAnsStr = new StringBuilder();
            if(divisibleBy3) {
                numAnsStr.append("Fizz");
            }
            if(divisibleBy5) {
              numAnsStr.append("Buzz");
            }
            if(!divisibleBy3 && !divisibleBy5) {
              numAnsStr.append(num);
            }
            ans.add(numAnsStr.toString());
         }
         return ans;
    }
}
```

> 复杂度分析

循环遍历1到n，时间复杂度O(n)

额外使用StringBuilder保存结果，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 89.24% of Java online submissions for Fizz Buzz.

Memory Usage: 46 MB, less than 5.87% of Java online submissions for Fizz Buzz.
