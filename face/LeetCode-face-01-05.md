### LeetCode-face-01-05

> 题目链接

[LeetCode-face-01-05](https://leetcode-cn.com/problems/one-away-lcci/)

> 思路

如果长度相同，就检索不同的字符是否小于等于1，如果长度相差1就寻找是否缺了一个字符，否则直接返回失败

> 代码

```java
class Solution {
    public boolean oneEditAway(String first, String second) {
        int length = Math.abs(first.length() - second.length());
        if(length > 1) return false;
        if(length == 0){
            int count = 0;
            for(int i = 0; i < first.length(); i++){
                if(first.charAt(i) != second.charAt(i)){
                    count++;
                    if(count > 1) return false;
                }
            }
            return true;
        }else{
            if(first.length() > second.length()) return addOneChar(second, first);
            else return addOneChar(first, second);
        }
    }

    public boolean addOneChar(String low, String high){
        boolean flag = true;
        int lowPosition = low.length() - 1;
        int highPosition = high.length() - 1;
        while(lowPosition >= 0 && highPosition >= 0){
            if(low.charAt(lowPosition) != high.charAt(highPosition)){
                highPosition--;
                if(flag) flag = false;
                else return false;
            }else{
                lowPosition--;
                highPosition--;
            }
        }
        return true;
    }
}
```

> 复杂度分析

遍历字符串，时间复杂度O(n)

额外使用常量来辅助，空间复杂度O(1)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了97.61%的用户

内存消耗：38.7 MB, 在所有 Java 提交中击败了14.22%的用户
