### LeetCode-575-distribute-candies

> 题目链接

[LeetCode-575-distribute-candies](https://leetcode-cn.com/problems/distribute-candies/)

> 思路

遍历数组，记录糖果的种类，和length/2比较，输出较小值

> 代码

```java
class Solution {
    public int distributeCandies(int[] candyType) {
        int[] type = new int[200001];
        int count = 0;
        for(int n : candyType){
            int m = n + 100000;
            if(type[m] == 0){
                count++;
                type[m]++;
            }
        }
        return Math.min(count, candyType.length / 2);
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

额外使用固定长度的数组，空间复杂度O(1)

> 总结

执行用时：10 ms, 在所有 Java 提交中击败了94.27%的用户

内存消耗：40.3 MB, 在所有 Java 提交中击败了54.02%的用户
