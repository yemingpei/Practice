### LeetCode-381-Insert-Delete-GetRandom-O(1)-Duplicates-allowed

> 题目链接

[LeetCode-381-Insert-Delete-GetRandom-O(1)-Duplicates-allowed](https://leetcode.com/problems/insert-delete-getrandom-o1-duplicates-allowed/)

> 思路

用map加list来保存对应的数据，便于快速查找和随机生成索引

> 代码

```java
class RandomizedCollection {
    List<Integer> list;
    Map<Integer, List<Integer>> map;
    Random random = new Random();
    
    public RandomizedCollection() {
        list = new ArrayList<>();
        map = new HashMap<>();
    }
    
    public boolean insert(int val) {
        if(!map.containsKey(val)) map.put(val, new ArrayList<>());
        map.get(val).add(list.size());
        list.add(val);
        
        return map.get(val).size() == 1;
    }
    
    public boolean remove(int val) {
        if(!map.containsKey(val) || map.get(val).size() == 0) return false;
        
        int idxarr_size = map.get(val).size();
        int remove_idx = map.get(val).get(0);
        map.get(val).remove(0); // remove by idx
        int last_val = list.get(list.size()-1);
        list.set(remove_idx, last_val);
        map.get(last_val).add(remove_idx);
        map.get(last_val).remove(new Integer(list.size()-1));
        
        list.remove(list.size()-1);
        return true;
        
    }
    
    public int getRandom() {
        return list.get(random.nextInt(list.size()));
    }
}
```

> 复杂度分析

哈希表查询，时间复杂度O(1)

额外使用Map来保存数据，空间复杂度O(n)

> 总结

Runtime: 10 ms, faster than 93.67% of Java online submissions for Insert Delete GetRandom O(1) - Duplicates allowed.

Memory Usage: 44.1 MB, less than 90.47% of Java online submissions for Insert Delete GetRandom O(1) - Duplicates allowed.
