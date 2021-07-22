### LeetCode-face-10-01

> 题目链接

[LeetCode-face-10-01](https://leetcode-cn.com/problems/sorted-merge-lcci/)

> 思路

从尾部开始排，从大到小，大的排在最后面

> 代码

```java
class Solution {
    public void merge(int[] A, int m, int[] B, int n) {
        int flag = m + n - 1;
        int a = m - 1;
        int b = n - 1;
        while(flag >= 0){
            if(a < 0) A[flag] = B[b--];
            else if(b < 0) A[flag] = A[a--];
            else if(A[a] > B[b]) A[flag] = A[a--];
            else A[flag] = B[b--];
            flag--;
        }
    }
}
```

> 复杂度分析

需要处理m + n个元素，时间复杂度O(m + n) 

额外使用三个int值，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.6 MB, 在所有 Java 提交中击败了25.19%的用户
