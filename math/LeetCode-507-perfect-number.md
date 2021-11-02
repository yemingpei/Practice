### LeetCode-507-perfect-number

> 题目链接

[LeetCode-507-perfect-number](https://leetcode-cn.com/problems/perfect-number/)

> 思路

从0开始到开根，一次添加因子

> 代码

```java
class Solution {
    public boolean checkPerfectNumber(int num) {
        if(num == 1) return false;
        int number = (int)Math.sqrt(num);
        int count = 1;
        for(int i = 2; i <= number; i++){
            if(num % i == 0){
                count += i;
                count += num / i;
            }
        }
        return count == num;
    }
}
```

> 复杂度分析

遍历到n的开根次，时间复杂度O(n)

无额外使用，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了91.19%的用户

内存消耗：35 MB, 在所有 Java 提交中击败了82.56%的用户
