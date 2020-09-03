### LeetCode-146-LRU-Cache

> 题目链接

[LeetCode-146-LRU-Cache](https://leetcode.com/problems/lru-cache/)

> 思路

使用LinkedHashMap来保存处理，hash表和双向链表（保存顺序）

> 代码

```java
class LRUCache {
    private LinkedHashMap<Integer, Integer> map;
    private int capacity;
    public LRUCache(int capacity) {
        this.capacity = capacity;
        map = new LinkedHashMap<Integer, Integer>(capacity, 0.75f, true){
            protected boolean removeEldestEntry(Map.Entry eldest) {
                return size() > capacity;
            }
        };
    }
    
    public int get(int key) {
        return map.getOrDefault(key, -1);
    }
    
    public void put(int key, int value) {
        map.put(key, value);
    }
}
```

> 复杂度分析

get和put，时间复杂度O(1)

额外使用LinkedHashMap来保存数据，空间复杂度O(n)

> 总结

Runtime: 12 ms, faster than 97.27% of Java online submissions for LRU Cache.

Memory Usage: 47.5 MB, less than 83.61% of Java online submissions for LRU Cache.
