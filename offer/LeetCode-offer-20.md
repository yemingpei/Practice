### LeetCode-offer-20

> 题目链接

[LeetCode-offer-20](https://leetcode-cn.com/problems/biao-shi-shu-zhi-de-zi-fu-chuan-lcof/)

> 思路

标记是都有小数点，是否有e，然后每个情况判断

> 代码

```java
class Solution {
    public boolean isNumber(String s) {
        int index = 0;
        boolean dot = false, hase = false, num = false;
        String str = s.trim();
        char[] c = str.toCharArray();
        if(c.length == 0) return false;
        if(c[0] == '+' || c[0] == '-') index = 1;
        for(int i = index; i < c.length; i++){
            if(c[i] >= '0' && c[i] <= '9') {
                num = true;
                continue;
            }
            else if(c[i] == '.'){
                if(!hase && !dot) dot=true;
                else return false;
            }
            else if(c[i] == 'e' || c[i] == 'E'){
                if(!hase && num){
                    hase = true;
                    num = false;
                }
                else return false;
            }
            else if(c[i] == '+' || c[i] == '-'){
                if(c[i-1] == 'e' || c[i-1] == 'E') continue;
                else return false;
            }else return false;
        }
        return num;
    }
}
```

> 复杂度分析

遍历字符串，时间复杂度O(n)

额外使用char数组，空间复杂度O(n)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.6 MB, 在所有 Java 提交中击败了47.95%的用户
