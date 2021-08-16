### LeetCode-face-16-21

> 题目链接

[LeetCode-face-16-21](https://leetcode-cn.com/problems/sum-swap-lcci/)

> 思路

根据sum1 - sum2 = d和sum1 -a + b =  sum2 - b + a成立得a - b = d / 2;先计算d的值，然后记录数组1，然后遍历数组2，计算差值，检查在集合中是否存在

> 代码

```java
class Solution {
    public int[] findSwapValues(int[] array1, int[] array2) {
        Set<Integer> set = new HashSet<>();
        int sum1 = 0, sum2 = 0;
        for(int i = 0; i < array1.length; i++)
            sum1 += array1[i];
        for(int i = 0; i < array2.length; i++)
            sum2 += array2[i];
        int dif = sum1 - sum2;
        if(dif % 2 != 0 || sum1 == sum2)
            return new int[]{};
        dif /= 2;
        for(int i = 0; i < array1.length; i++)
            set.add(array1[i]);
        for(int i = 0; i < array2.length; i++){
            if(set.contains(array2[i] + dif))
                return new int[]{array2[i] + dif, array2[i]};
        }
        return new int[]{};
    }
}
```

> 复杂度分析

遍历两个数组，时间复杂度O(m + n)

额外使用set集合，空间复杂度O(n)

> 总结

执行用时：6 ms, 在所有 Java 提交中击败了80.73%的用户

内存消耗：49.9 MB, 在所有 Java 提交中击败了54.33%的用户
