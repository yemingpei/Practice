### LeetCode-398-Random-Pick-Index

> 题目链接

[LeetCode-398-Random-Pick-Index](https://leetcode.com/problems/random-pick-index/)

> 思路

随机抽，使每个数出现的概率都是1/n

> 代码

```java
class Solution {
    private int[] nums;
    public Solution(int[] nums) {
       this.nums = nums;
    }
    
    public int pick(int target) {
        Random r = new Random();
        int n = 0;
        int index = 0;
        for(int i = 0;i < nums.length;i++)
            if(nums[i] == target){
                n++;
                if(r.nextInt() % n == 0) index = i;
            }
        return index;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(n)

无额外使用变量，空间复杂度O(1)

> 总结

Runtime: 60 ms, faster than 58.47% of Java online submissions for Random Pick Index.

Memory Usage: 46.8 MB, less than 99.44% of Java online submissions for Random Pick Index.
