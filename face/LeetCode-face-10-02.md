### LeetCode-face-10-02

> 题目链接

[LeetCode-face-10-02](https://leetcode-cn.com/problems/group-anagrams-lcci/)

> 思路

对字符重排，用map保存字典保存对应的数据，最后再转换成list

> 代码

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<String, List<String>>();
        for(String str : strs){
            char[] arr = str.toCharArray();
            Arrays.sort(arr);
            String key = new String(arr);
            List<String> list = map.getOrDefault(key, new ArrayList<String>());
            list.add(str);
            map.put(key, list);
        }
        return new ArrayList<List<String>> (map.values());
    }
}
```

> 复杂度分析

只有一层for循环，里面有一重排队，时间复杂度O(lognn ^ 2) 

额外使用map加list，空间复杂度O(n ^ 2)

> 总结

执行用时：6 ms, 在所有 Java 提交中击败了98.68%的用户

内存消耗：40.9 MB, 在所有 Java 提交中击败了98.90%的用户
