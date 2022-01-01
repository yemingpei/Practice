### LeetCode-599-minimum-index-sum-of-two-lists

> 题目链接

[LeetCode-599-minimum-index-sum-of-two-lists](https://leetcode-cn.com/problems/minimum-index-sum-of-two-lists/)

> 思路

先遍历一个数组，记录到map表里面，然后再检索这个map表

> 代码

```java
class Solution {
    public String[] findRestaurant(String[] list1, String[] list2) {
       if(list1.length > list2.length) return findRestaurant(list2, list1);
       Map<String,Integer> map = new HashMap<>();
       int index = 0;
       for(String rest : list1){
           map.put(rest,index++);
       }
       List<String> li = new ArrayList<>();
       int minIndex = Integer.MAX_VALUE;
       for(int i = 0;i<list2.length && i<=minIndex;i++){
           if(map.containsKey(list2[i])){
               int sumIndex = map.get(list2[i]) + i;
               if(sumIndex == minIndex){
                    li.add(list2[i]);
               }else if(sumIndex < minIndex){
                    li.clear();
                    li.add(list2[i]);
                    minIndex = sumIndex;
               }
           }
       }
       return li.toArray(new String[li.size()]);
    }
}
```

> 复杂度分析

遍历两个数组，时间复杂度O(m + n)

额外使用map，空间复杂度O(n)

> 总结

执行用时：6 ms, 在所有 Java 提交中击败了97.86%的用户

内存消耗：39 MB, 在所有 Java 提交中击败了41.02%的用户
