### LeetCode-460-LFU-Cache

> 题目链接

[LeetCode-460-LFU-Cache](https://leetcode.com/problems/lfu-cache/)

> 思路

两个map，一个保存节点，另一个记录节点和数量的关系，同一节点进行操作时候，次数的map也需要更新

> 代码

```java
class LFUCache {
    class Node {
        int key;
        int val;
        int freq;
        Node prev, next;
        public Node(int key, int val){
            this.key = key;
            this.val = val;
            freq = 1;
        }
    }
    
    Map<Integer, Node> map;
    Map<Integer, Node> group;
    int minFreq;
    int capacity;
    
    public LFUCache(int capacity) {
        this.map   = new HashMap<>();
        this.group = new HashMap<>();
        this.capacity = capacity;
    }
    
    public int get(int key) {
        if( map.containsKey(key)){
            Node n = map.get(key);
            remove(n);
            n.freq++;
            insert(n);
            return n.val;
        } else {
            return -1;
        }
    }
    
    public void put(int key, int value) {
        if( capacity == 0) return;
        if( map.containsKey(key)){
            Node n = map.get(key);
            n.val = value;
            remove(n);
            n.freq++;
            insert(n);
        } else {
            if( map.size() == capacity){
                Node least = group.get(minFreq).prev;
                map.remove(least.key);
                remove(least);
            }
            Node newNode = new Node(key, value);
            map.put(key, newNode);
            insert(newNode);
            minFreq = 1;
        }
    }
    
    private void remove(Node n){
        n.prev.next = n.next;
        n.next.prev = n.prev;
        if( n.freq == minFreq && n.prev == n.next)
            minFreq++;
        n.prev = null;
        n.next = null;
    }
    
    private void insert(Node n){
        if( !group.containsKey(n.freq)){
            Node head = new Node(0, 0);
            head.prev = head;
            head.next = head;
            group.put(n.freq, head);
        }
        Node head = group.get(n.freq);
        n.next = head.next;
        head.next.prev = n;
        n.prev = head;
        head.next = n;
    }
}
```

> 复杂度分析

get和put，时间复杂度O(1)

额外使用map辅助，空间复杂度O(n)

> 总结

Runtime: 18 ms, faster than 74.94% of Java online submissions for LFU Cache.

Memory Usage: 57.8 MB, less than 11.50% of Java online submissions for LFU Cache.
