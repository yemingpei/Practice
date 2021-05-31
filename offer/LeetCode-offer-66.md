### LeetCode-offer-66

> 题目链接

[LeetCode-offer-66](https://leetcode-cn.com/problems/gou-jian-cheng-ji-shu-zu-lcof/)

> 思路

先倒叙保存位置右边的乘积，然后再顺序相乘，获得不包括当前的数字的乘积

> 代码

```java
class Solution {
    public int[] constructArr(int[] a) {
        int[] result = new int[a.length];
        for(int i = 0; i < result.length; i++){
            result[i] = 1;
        }
        for(int j = result.length - 2; j >=0; j--){
            result[j] = a[j + 1] * result[j + 1];
        }
        int number = 1;
        for(int i = 1; i < result.length; i++){
            number *= a[i - 1];
            result[i] *= number; 
        }
        return result;
    }
}
```

> 复杂度分析

遍历了三次数组，时间复杂度O(n)

额外使用一个int来辅助，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：50.7 MB, 在所有 Java 提交中击败了94.77%的用户
