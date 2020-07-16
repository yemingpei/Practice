### LeetCode-60-Permutation-Sequence

> 题目链接

[LeetCode-60-Permutation-Sequence](https://leetcode.com/problems/permutation-sequence/)

> 思路

利用k和n!的关系来推算每个位置的数字

> 代码

```java
class Solution {
    public String getPermutation(int n, int k) {
        int[] position = new int[n];
        int sum = 1;
        for(int i = 2; i <= n; i++)
            sum *= i;
        StringBuilder result = new StringBuilder();
        for(int j = n; j > 0; j--){
            sum /= j;
            int quotient = k / sum;
            int remainder = k % sum;
            result.append(getNumber(position, remainder == 0? quotient: quotient + 1));
            k = remainder == 0? sum : remainder;
        }
        return result.toString();
    }
    public int getNumber(int[] number, int position){
        for(int i = 0; i < number.length; i++){
            if(number[i] == 1) continue;
            position--;
            if(position == 0){
                number[i] = 1;
                return i + 1;
            }
        }
        return -1;
    }
}
```

> 复杂度分析

利用k和n!的关系推算，时间复杂度O(n ^ 2)

额外使用长度为n的数组辅助，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 98.54% of Java online submissions for Permutation Sequence.

Memory Usage: 39 MB, less than 17.17% of Java online submissions for Permutation Sequence.
