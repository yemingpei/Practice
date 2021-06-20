### LeetCode-face-03-06

> 题目链接

[LeetCode-face-03-06](https://leetcode-cn.com/problems/animal-shelter-lcci/)

> 思路

用LinkedList保存数据，然后从队列头进行检索

> 代码

```java
private List<int []> list;
    public AnimalShelf() {
        list = new LinkedList<>();
    }
    
    public void enqueue(int[] animal) {
        list.add(animal);
    }
    
    public int[] dequeueAny() {
        if(list.isEmpty())return new int[]{-1,-1};
        return list.remove(0);
    }
    
    public int[] dequeueDog() {
        for(int i = 0;i < list.size();i++){
            if(list.get(i)[1] == 1){
                return list.remove(i);
            }
        }
        return new int[]{-1,-1};
    }
    
    public int[] dequeueCat() {
        for(int i = 0;i < list.size();i++){
            if(list.get(i)[1] == 0){
                return list.remove(i);
            }
        }
        return new int[]{-1,-1};
    }
}
```

> 复杂度分析

需要遍历寻找元素，时间复杂度O(n) 

额外使用LinkedList，空间复杂度O(n)

> 总结

执行用时：95 ms, 在所有 Java 提交中击败了82.15%的用户

内存消耗：48.2 MB, 在所有 Java 提交中击败了21.78%的用户
