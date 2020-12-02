### LeetCode-313-Super-Ugly-Number

> 题目链接

[LeetCode-313-Super-Ugly-Number](https://leetcode.com/problems/super-ugly-number/)

> 思路

不断用因子相乘，然后比较小的就先排列上，不断循环，直到找到第n个数字

> 代码

```java
class Solution {
    
    int min(int numbers[]) {
        int min = numbers[0];
        for(int i = 0 ; i < numbers.length; i++) {
            if(min > numbers[i]) min = numbers[i];
        }
        return min;
    }
    
    public int nthSuperUglyNumber(int n, int[] primes) {
        int[] ugly = new int[n];
        ugly[0] = 1;
        int indexes[] = new int[primes.length];
        for (int i = 0; i < indexes.length; i++)
            indexes[i] = 0;
        int next_min_values[] = new int[indexes.length];
        for (int i = 0 ; i < primes.length ; i++) 
            next_min_values[i] = ugly[indexes[i]] * primes[i];
        for (int i = 1;i < n; i++) {
            ugly[i] = min(next_min_values);
            for (int j = 0 ; j < next_min_values.length ; j++) {
                if (next_min_values[j] == ugly[i]) {
                    indexes[j]++;
                    next_min_values[j] = ugly[indexes[j]] * primes[j];
                }
            }
        }
        return ugly[n-1];
    }
}
```

> 复杂度分析

双循环遍历对应的next_min_values和primes，时间复杂度O(mn)

额外使用数组来辅助,保存计算好的值，空间复杂度O(n)

> 总结

Runtime: 12 ms, faster than 90.26% of Java online submissions for Super Ugly Number.

Memory Usage: 36.9 MB, less than 72.08% of Java online submissions for Super Ugly Number.
