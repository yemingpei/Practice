### LeetCode-341-Flatten-Nested-List-Iterator

> 题目链接

[LeetCode-341-Flatten-Nested-List-Iterator](https://leetcode.com/problems/flatten-nested-list-iterator/)

> 思路

递归，深度遍历组装数组，然后再实现迭代器的功能

> 代码

```java
public class NestedIterator implements Iterator<Integer> {
    private int position = 0;
    private List<Integer> list = new ArrayList<>();
    public NestedIterator(List<NestedInteger> nestedList) {
        addNestedInteger(nestedList, list);
    }
    
    private void addNestedInteger(List<NestedInteger> nestedList, List<Integer> list){
        for(NestedInteger item : nestedList){
            if(item.isInteger()) list.add(item.getInteger());
            else addNestedInteger(item.getList(), list);
        }
    }

    @Override
    public Integer next() {
        if(hasNext()){
            return list.get(position++);
        }
        else
            return null;
    }

    @Override
    public boolean hasNext() {
        return position < list.size();
    }
}
```

> 复杂度分析

递归，深度遍历，时间复杂度O(n)

额外使用list保存扁平化数组，空间复杂度O(n)

> 总结

Runtime: 2 ms, faster than 98.85% of Java online submissions for Flatten Nested List Iterator.

Memory Usage: 41.2 MB, less than 84.77% of Java online submissions for Flatten Nested List Iterator.
