### LeetCode-face-16-25

> 题目链接

[LeetCode-face-16-25](https://leetcode-cn.com/problems/lru-cache-lcci/)

> 思路

Lru的实现，其实就是LinkedHashMap的源码的了解，使用双向链表（控制顺序）和hashMap（快速查找）来实现

> 代码

```java
class LRUCache {
    class Node{
        int key;
        int value;
        Node prev;
        Node next;
        public Node(){}
        public Node(int key,int value){
            this.key = key;
            this.value = value;
        }
    }
    private HashMap<Integer,Node> hashmap = new HashMap<Integer,Node>();
    private int capacity;
    private int size;
    Node head,tail;
    public LRUCache(int capacity) {
        this.capacity = capacity;
        this.size = 0;
        head = new Node();
        tail = new Node();
        head.next = tail;
        tail.prev = head;
    }
    
    public int get(int key) {
        Node node = hashmap.get(key);
        if(node==null) return -1;
        movetotail(node);
        return node.value;
    }
    
    public void put(int key, int value) {
       Node node = hashmap.get(key);
       if(node!=null){ 
           node.value = value;
           movetotail(node);
       }else{
           Node newnode = new Node(key,value);
           hashmap.put(key,newnode);
           addtotail(newnode);
           size++;
           if(size>capacity){
               Node head=removehead();
               hashmap.remove(head.key);
               size--;
           }
       }
    }
    private void movetotail(Node node){
        removenode(node);
        addtotail(node);
    }
    private void removenode(Node node){
        node.prev.next = node.next;
        node.next.prev = node.prev;
    }
    private void addtotail(Node node){
        node.next = tail;
        node.prev = tail.prev;
        tail.prev.next = node;
        tail.prev = node;
    }
    private Node removehead(){
        Node realnode = head.next;
        removenode(realnode);
        return realnode;
    }
}
```

> 复杂度分析

双向链表移除和插入操作，时间复杂度O(1)

额外使用map保存，空间复杂度O(n)

> 总结

执行用时：26 ms, 在所有 Java 提交中击败了89.90%的用户

内存消耗：46.3 MB, 在所有 Java 提交中击败了72.65%的用户
