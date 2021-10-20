### LeetCode-492-construct-the-rectangle

> 题目链接

[LeetCode-492-construct-the-rectangle](https://leetcode-cn.com/problems/construct-the-rectangle/)

> 思路

遍历开根号的数字，检查是否有更接近开根号的数

> 代码

```java
class Solution {
    public int[] constructRectangle(int area) {
        int mid = (int) Math.sqrt(area);
        int width = 1;
        for(int i = 2; i <= mid; i++){
            if(area % i == 0) width = i;
        }
        return new int[]{area / width, width};
    }
}
```

> 复杂度分析

n的开方次，时间复杂度O(√n)

额外使用int变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.9 MB, 在所有 Java 提交中击败了42.62%的用户
