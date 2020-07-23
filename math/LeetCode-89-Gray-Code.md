### LeetCode-89-Gray-Code

> 题目链接

[LeetCode-89-Gray-Code](https://leetcode.com/problems/gray-code/)

> 思路

根据公式 k = i ^ (i >> 1),i的范围是[0, 2 ^ n]

> 代码

```java
class Solution {
    public List<Integer> grayCode(int n) {
        List<Integer> result = new ArrayList<>();
        if(n == 0){
            result.add(0);
        }else{
            int k = 1 << n;
            for(int i = 0; i < k; i++)
                result.add(i ^ (i >> 1));
        }
        return result;
    }
}
```

> 复杂度分析

遍历2 ^ n次，时间复杂度O(2 ^ n)

无额外使用辅助变量，空间复杂度O(1)

> 总结

Runtime: 0 ms, faster than 100.00% of Java online submissions for Gray Code.

Memory Usage: 37 MB, less than 93.27% of Java online submissions for Gray Code.
