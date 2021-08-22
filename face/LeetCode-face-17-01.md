### LeetCode-face-17-01

> 题目链接

[LeetCode-face-17-01](https://leetcode-cn.com/problems/add-without-plus-lcci/)

> 思路

a ^ b为两数之和（不包括进位），(a & b) << 1 为进位的数据

> 代码

```java
class Solution {
    public int add(int a, int b) {
        while(b != 0){
            int c = a;
            a = a ^ b;
            b = (c & b) << 1; 
        }
        return a;
    }
}
```

> 复杂度分析

不超过32次进位，时间复杂度O(1)

额外使用int变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：35.1 MB, 在所有 Java 提交中击败了72.61%的用户
