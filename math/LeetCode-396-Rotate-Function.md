### LeetCode-396-Rotate-Function

> 题目链接

[LeetCode-396-Rotate-Function](https://leetcode.com/problems/rotate-function/)

> 思路

```java
数组 a  a1  a2  a3
f(0) = 0 * a + 1* a1 + 2 * a2 + 3 * a3
f(1) = 0 * a3 + 1* a + 2 * a1 + 3 * a2
f(0) + sum = 1 * a + 2* a1 + 3 * a2 + 4 * a3
f(0) + sum 和 f(1) 比较，多了4 * a3，则有f(n) = f(n - 1) + sum - n * (第length - n和元素) 
```

错位相减法，则有f(n) = f(n - 1) + sum - n * A[n - i]

> 代码

```java
class Solution {
    public int maxRotateFunction(int[] A) {
        int sum = 0;
        int P = 0;
        int n = A.length;
        for(int i = 0; i < n; i++){
            sum += A[i];
            P += i * A[i];
        }
        int max = P;
        for(int i = 1; i < n; i++){
            P = P + sum - n * A[n - i];
            max = Math.max(max, P);
        }
        return max;
    }
}
```

> 复杂度分析

需要遍历数组，时间复杂度O(n)

需要三个int值来协助保存最大值，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Rotate Function.

Memory Usage: 39.3 MB, less than 44.92% of Java online submissions for Rotate Function.
