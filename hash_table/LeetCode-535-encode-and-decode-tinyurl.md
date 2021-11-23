### LeetCode-535-encode-and-decode-tinyurl

> 题目链接

[LeetCode-535-encode-and-decode-tinyurl](https://leetcode-cn.com/problems/encode-and-decode-tinyurl/)

> 思路

简化url，保存在hashMap里面，然后通过查表还原

> 代码

```java
public class Codec {
    long idx = 0;
    HashMap<String, String> map = new HashMap<>();
    public String encode(String longUrl) {
        String str = "http://tinyurl.com/" + Long.toString(idx++);
        map.put(str, longUrl);
        return str;
    }
    public String decode(String shortUrl) {
        return map.get(shortUrl);
    }
}
```

> 复杂度分析

使用hashMap查询，时间复杂度O(1)

额外使用map，空间复杂度O(n)

> 总结

执行用时：3 ms, 在所有 Java 提交中击败了73.92%的用户

内存消耗：38.4 MB, 在所有 Java 提交中击败了80.60%的用户
