### LeetCode-380-Insert-Delete-GetRandom-O

> 题目链接

[LeetCode-380-Insert-Delete-GetRandom-O](https://leetcode.com/problems/insert-delete-getrandom-o1/)

> 思路

先保存数组的数，建立hash表，然后开始遍历，和数组，移除的时候要避免list移动，要进行移位操作

> 代码

```java
class RandomizedSet {
  Map<Integer, Integer> dict;
  List<Integer> list;
  Random rand = new Random();
    
  public RandomizedSet() {
    dict = new HashMap();
    list = new ArrayList();
  }
    
  public boolean insert(int val) {
    if (dict.containsKey(val)) return false;
    dict.put(val, list.size());
    list.add(list.size(), val);
    return true;
  }

  public boolean remove(int val) {
    if (!dict.containsKey(val)) return false;
    int lastElement = list.get(list.size() - 1);
    int idx = dict.get(val);
    list.set(idx, lastElement);
    dict.put(lastElement, idx);
    list.remove(list.size() - 1);
    dict.remove(val);
    return true;
  }

  public int getRandom() {
    return list.get(rand.nextInt(list.size()));
  }
}
```

> 复杂度分析

insert有扩容操作，时间复杂度O(n)，remove和getRandom,时间复杂度为O(1)

额外使用map和list来保存数据，空间复杂度O(n)

> 总结

Runtime: 7 ms, faster than 99.92% of Java online submissions for Insert Delete GetRandom O(1).

Memory Usage: 44.4 MB, less than 24.57% of Java online submissions for Insert Delete GetRandom O(1).
