### LeetCode-229-Majority-Element-II

> 题目链接

[LeetCode-229-Majority-Element-II](https://leetcode.com/problems/majority-element-ii/)

> 思路

摩尔投票法，利用前后投票票数相同则添加，为0则替换投票人，到最后剩下的，在筛选是否超过3分之1

> 代码

```java
class Solution {
    public List<Integer> majorityElement(int[] nums) {
        int m1 = 0, m2 = 0, c1 = 0, c2 = 0;
        for(int i = 0; i < nums.length; i++){
            if(nums[i] == m1){
                c1++;
            }else if(nums[i] == m2){
                c2++;
            }else if(c1 == 0){
                m1 = nums[i];
                c1++;
            }else if(c2 == 0){
                m2 = nums[i];
                c2++;
            }else{
                c1--;
                c2--;
            }
        }
        c1 = 0;
        c2 = 0; 
        for(int i = 0; i < nums.length; i++){
            if(nums[i] == m1){
                c1++;
            }else if(nums[i] == m2){
                c2++;
            }
        }
        List<Integer> res = new ArrayList<>();
        if(c1 > nums.length/3){
            res.add(m1);
        }
        if(c2 > nums.length/3){
            res.add(m2);
        }
        
        return res;
    }
}
```

> 复杂度分析

需要遍历两遍数组，时间复杂度O(n)

额外记录两个投票人的票数，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 99.94% of Java online submissions for Majority Element II.

Memory Usage: 43.1 MB, less than 8.27% of Java online submissions for Majority Element II.
