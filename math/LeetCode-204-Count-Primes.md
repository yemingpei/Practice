### LeetCode-204-Count-Primes

> 题目链接

[LeetCode-204-Count-Primes](https://leetcode.com/problems/count-primes/)

> 思路

根据厄拉多塞筛法，而且必须是单数，2除外，每次检查i * 2；最多检查两遍奇数

> 代码

```java
class Solution {
    public int countPrimes(int n) {
        if(n <= 2) return 0;
        int count = 1;
        boolean[] flag = new boolean[n];
        for(int i = 3; i < n; i+=2){
            if(!flag[i]){
                count++;
                for(int gap = i * 2, j = i + gap; j < n; j+=gap)
                    flag[j] = true;
            }
        }
        return count;
    }
}
```

> 复杂度分析

遍历n次，时间复杂度O(n)

使用boolean[]辅助变量，空间复杂度O(n)

> 总结

Runtime: 7 ms, faster than 98.18% of Java online submissions for Count Primes.

Memory Usage: 37.8 MB, less than 73.26% of Java online submissions for Count Primes.
