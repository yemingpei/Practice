### LeetCode-face-16-18

> 题目链接

[LeetCode-face-16-18](https://leetcode-cn.com/problems/pattern-matching-lcci/)

> 思路

先计算ab的数量，计算可能出现的ab的个数的解，然后再一一匹配

> 代码

```java
class Solution {
    public boolean patternMatching(String pattern, String value) {
        if(pattern.length() == 0) return value.length() == 0;
        int[] count = new int[2];
        for(char c : pattern.toCharArray()) count[c - 'a']++;
        if(value.length() == 0) return count[0] == 0 || count[1] == 0;
        if(count[0] == 0) return helper(value, count[1]);
        else if(count[1] == 0) return helper(value, count[0]);
        if(helper(value,count[0]) || helper(value,count[1])) return true;
        for(int aLen = 1; aLen < value.length() / count[0]; aLen++){
            if((value.length() - aLen * count[0]) % count[1] != 0) continue;
            int bLen = (value.length() - (count[0] * aLen)) / count[1];
            if(check(pattern, value, aLen, bLen)) return true;
        }
        return false;
    }
    private boolean helper(String value, int count){
        int vlen = value.length();
        if(vlen % count != 0) return false;
        int len = vlen / count;
        for(int i = len; i < vlen; i += len){
            if(!value.substring(0, len).equals(value.substring(i, i + len))) return false;
        }
        return true;
    }
    private boolean check(String pattern,String value,int aLen,int bLen){
        String[] st = {"",""};
        for(int i = 0, j = 0; i < pattern.length(); i++){
            if(pattern.charAt(i) == 'a'){
                if(st[0].equals("")) st[0] = value.substring(j, j + aLen);
                else if(!value.substring(j, j + aLen).equals(st[0])) return false;
                j += aLen;
            }else if(pattern.charAt(i) == 'b'){
                if(st[1].equals("")) st[1]=value.substring(j,j + bLen);
                else if(!value.substring(j, j + bLen).equals(st[1])) return false;
                j += bLen;
            }
        }
        if(st[0].equals(st[1])) return false;
        return true;
    }
}
```

> 复杂度分析

遍历数组，时间复杂度O(mn)

额外使用常数的变量，空间复杂度O(1)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：36.4 MB, 在所有 Java 提交中击败了66.09%的用户
