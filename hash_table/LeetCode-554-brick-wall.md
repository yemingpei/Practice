### LeetCode-554-brick-wall

> 题目链接

[LeetCode-554-brick-wall](https://leetcode-cn.com/problems/brick-wall/)

> 思路

遍历二维数组，记录每个map从列的墙的和，最后比较map的值

> 代码

```java
class Solution {
    public int leastBricks(List<List<Integer>> wall) {
        Map<Integer,Integer> map = new HashMap<>();
        for (int i1 = 0; i1 < wall.size(); i1++) {
            List<Integer> list = wall.get(i1);
            int sum = 0;
            for (int i = 0; i < list.size() - 1; i++) {
                Integer value = list.get(i);
                sum += value;
                if (map.containsKey(sum)) {
                    map.put(sum, map.get(sum) + 1);
                } else {
                    map.put(sum, 1);
                }
            }

        }
        int maxValue=0;
        for (Integer value : map.values()) {
            if(value>maxValue){
                maxValue=value;
            }
        }
        return wall.size()-maxValue;
    }
}
```

> 复杂度分析

遍历二维数组，时间复杂度O(mn)

额外使用Map，空间复杂度O(mn)

> 总结

执行用时：12 ms, 在所有 Java 提交中击败了80.87%的用户

内存消耗：41.5 MB, 在所有 Java 提交中击败了51.22%的用户
