### LeetCode-432-All-O-one-Data-Structure

> 题目链接

[LeetCode-432-All-O-one-Data-Structure](https://leetcode.com/problems/all-oone-data-structure/)

> 思路

用map来快速检索，取最大最小值则需要遍历获得

> 代码

```java
class AllOne {

    Map<String,Integer> map;
    public AllOne() {
        map = new HashMap<>();
    }
    
    public void inc(String key) {
        map.put(key,map.getOrDefault(key,0)+1);
    }
    
    public void dec(String key) {
        if(map.isEmpty() || !map.containsKey(key)) return;
        if(map.get(key) == 1 )
            map.remove(key);
        else 
            map.put(key,map.getOrDefault(key,0)-1);
    }
    
    public String getMaxKey() {
        if(map.isEmpty()) return "";
        int value = Integer.MIN_VALUE;
        String result = "" ;
        for(var item:map.keySet()){
            if(value < map.get(item)){
                result = item;
                value = map.get(item);
            }
        }  
        return result;
    }
    
    public String getMinKey() {
        if(map.isEmpty()) return "";
        int value = Integer.MAX_VALUE;
        String result ="" ;
        for(var item : map.keySet()){
            if(value > map.get(item)){
                result = item;
                value = map.get(item);
            }
        }
        return result;
    }
}
```

> 复杂度分析

getMaxKey和getMinKey，时间复杂度O(n)，其他都是O(1)

额外map保存数组，空间复杂度O(n)。

> 总结

Runtime: 13 ms, faster than 100.00% of Java online submissions for All O`one Data Structure.

Memory Usage: 45.1 MB, less than 44.43% of Java online submissions for All O`one Data Structure.
