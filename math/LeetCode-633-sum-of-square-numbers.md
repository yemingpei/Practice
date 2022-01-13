### LeetCode-633-sum-of-square-numbers

> 题目链接

[LeetCode-633-sum-of-square-numbers](https://leetcode-cn.com/problems/sum-of-square-numbers/)

> 思路

从0到c的开根，利用滑动窗口，来寻找是否有合适的值

> 代码

```java
class Solution {
    public boolean judgeSquareSum(int c) {
        int left = 0, right = (int)Math.sqrt(c);
        while (left <= right){
            int number = right * right - c + left * left;
            if(number > 0) right --;
            else if(number == 0) return true;
            else left ++;
        }
        return false;
    }
}
```

> 复杂度分析

遍历0到n的开根，时间复杂度O(√n)

额外使用左右边界，空间复杂度O(1)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了98.21%的用户

内存消耗：35.3 MB, 在所有 Java 提交中击败了36.91%的用户
