### LeetCode-284-Peeking-Iterator

> 题目链接

[LeetCode-284-Peeking-Iterator](https://leetcode.com/problems/peeking-iterator/)

> 思路

用Integer来保存peek的值，如果peek存在，则peek()直接返回，next()直接返回，并清空，否则，操作和迭代器iterator一致

> 代码

```java
class PeekingIterator implements Iterator<Integer> {
    Integer peek;
    Iterator<Integer> iterator;
    public PeekingIterator(Iterator<Integer> iterator) {
        this.iterator = iterator;
        peek = null;
    }

    public Integer peek() {
        if(peek == null)
            peek = iterator.next();
        return peek;
    }

    @Override
    public Integer next() {
        Integer result;
        if(peek != null){
            result = peek;
            peek = null;
            return result;
        }
        return iterator.next();
    }

    @Override
    public boolean hasNext() {
        return peek!= null || iterator.hasNext();
    }
}
```

> 复杂度分析

临时保存peek值，时间复杂度O(1)

额外int临时值来表示peek，空间复杂度O(1)

> 总结

Runtime: 4 ms, faster than 94.97% of Java online submissions for Peeking Iterator.

Memory Usage: 39.3 MB, less than 16.91% of Java online submissions for Peeking Iterator.
