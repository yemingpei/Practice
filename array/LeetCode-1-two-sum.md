### LeetCode-1-two-sum

> 题目链接

[LeetCode-1-two-sum](https://leetcode.com/problems/two-sum/)

> 思路

遍历一遍数组，数值用HashMap保存起来，如果找到target - 对应位置差值的数，则输出位置

> 代码

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer,Integer> m=new HashMap<Integer,Integer>();
        for(int i=0;i<nums.length;i++){
            if(m.containsKey(target-nums[i])){
                return new int[]{i,m.get(target-nums[i])};
            }
              m.put(nums[i],i);
        }
        return new int[]{0,0};
    }
}
```

> 复杂度分析

for循环遍历了一遍数组，HashMap查找的时间复杂度为1，整体用时应该是2n，时间复杂度O(n)

额外使用了HashMap,一般扩容2n足够使用，空间复杂度O(n)

> 总结

Runtime: 1 ms, faster than 99.89% of Java online submissions for Two Sum.

Memory Usage: 40.2 MB, less than 5.65% of Java online submissions for Two Sum.

典型的空间换时间
