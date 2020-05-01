### LeetCode-347-Top-K-Frequent-Elements

> 题目链接

[LeetCode-347-Top-K-Frequent-Elements](https://leetcode.com/problems/top-k-frequent-elements/)

> 思路

遍历一遍数组，计算出现的次数，然后让次数作为下标，进行构建桶，倒序遍历通，输出n个元素

> 代码

```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        int[] result = new int[k];
        List<Integer>[] bucket = new List[nums.length + 1];
        HashMap<Integer, Integer> hash = new HashMap<Integer, Integer>();
        for (int i : nums) {
          hash.put(i, hash.getOrDefault(i, 0) + 1);
        }
        for (int n : hash.keySet()) {
          int count = hash.get(n);
          if (bucket[count] == null)
            bucket[count] = new ArrayList();
          bucket[count].add(n);
        }
        int j = 0;
        for (int i = nums.length; i > 0; i--) {
          if (bucket[i] != null) {
            for (int z : bucket[i]) {
              result[j] = z;
              j++;
              if (j == k)
                return result;
            }
          }
        }
        return result;
    }
}
```

> 复杂度分析

变了一遍数组，计算次数，T（n）,再构建桶，T(n)遍历桶T(n)，时间复杂度O(n)

使用了桶，空间复杂度O(n^2)

> 总结

Runtime: 7 ms, faster than 99.38% of Java online submissions for Top K Frequent Elements.
Memory Usage: 41.9 MB, less than 11.20% of Java online submissions for Top K Frequent Elements.
