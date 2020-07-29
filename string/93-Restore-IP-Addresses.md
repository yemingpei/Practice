### 93-Restore-IP-Addresses

> 题目链接

[93-Restore-IP-Addresses](https://leetcode.com/problems/restore-ip-addresses/)

> 思路

不断地截取1到3个字符，进行校验，不符合就先退出。最多组合的情况为8个字符长度的字串

> 代码

```java
class Solution {
    public List<String> restoreIpAddresses(String s) {
       List<String> res=new ArrayList<>();
        ipHelper(s, new StringBuilder(), res, 4);
        return res;
    }
    
    public void ipHelper(String s, StringBuilder sb,List<String> res, int count){
        if(count * 3 < s.length()) return;
        if(count == 0){
            res.add(sb.toString().substring(0,sb.length()-1));
            return;
        }
        for(int i = 1; i <= 3; i++){
            if(i > s.length()) return;
            String sub = s.substring(0, i);
            if(sub.length() > 1 && sub.startsWith("0")) return;
            if(sub.length() == 3 && Integer.valueOf(sub) >= 256) return;
            int len = sb.length();
            ipHelper(s.substring(i), sb.append(sub).append("."), res, count-1);
            sb.setLength(len);
        }
    }
}
```

> 复杂度分析

最多匹配27个 ，时间复杂度O(1)

最多不超过19个字符串，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 99.67% of Java online submissions for Restore IP Addresses.

Memory Usage: 39.9 MB, less than 20.20% of Java online submissions for Restore IP Addresses.
