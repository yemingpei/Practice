### LeetCode-face-16-24

> 题目链接

[LeetCode-face-16-24](https://leetcode-cn.com/problems/pairs-with-sum-lcci/)

> 思路

先保存数字，然后找到另一个数，是否在map存在，注意维护map数字的个数

> 代码

```java
class Solution {
    public List<List<Integer>> pairSums(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        List<List<Integer>> result = new ArrayList<>();
        for(int i : nums){
            map.put(i, map.getOrDefault(i, 0) + 1);
        }
        for(int i = 0; i < nums.length; i++){
            if(map.get(nums[i]) <= 0) continue;
            int number = target - nums[i];
            if(number == nums[i] && map.get(nums[i]) < 2) continue;
            if(map.getOrDefault(number, 0) > 0){
                map.put(nums[i], map.get(nums[i]) - 1);
                map.put(number, map.get(number) - 1);
                List<Integer> list = new ArrayList<>();
                list.add(nums[i]);
                list.add(number);
                result.add(list);
            }
        }
        return result;
    }
}

```

> 复杂度分析

遍历两遍数组，时间复杂度O(n)

额外使用map保存，空间复杂度O(n)

> 总结

执行用时：24 ms, 在所有 Java 提交中击败了96.00%的用户

内存消耗：58.4 MB, 在所有 Java 提交中击败了10.54%的用户
