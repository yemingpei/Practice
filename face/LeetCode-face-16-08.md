### LeetCode-face-16-08

> 题目链接

[LeetCode-face-16-08](https://leetcode-cn.com/problems/english-int-lcci/)

> 思路

当一个比后一个字母小的时候，表示的是相减，从后面开始遍历，是[LeetCode-13-Roman-to-Integer](https://github.com/yemingpei/Practice/blob/master/string/LeetCode-13-Roman-to-Integer.md)的晋级版

> 代码

```java
class Solution {
    String[] belowTen = new String[] {"", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine"};
    String[] belowTwenty = new String[] {"Ten", "Eleven", "Twelve", "Thirteen", "Fourteen", "Fifteen", "Sixteen", "Seventeen", "Eighteen", "Nineteen"};
    String[] belowHundred = new String[] {"", "", "Twenty", "Thirty", "Forty", "Fifty", "Sixty", "Seventy", "Eighty", "Ninety"};
    
    public String numberToWords(int num) {
        if (num == 0){
            return "Zero";
        }
        
        return helper(num);
    }
    
    public String helper(int num){
        StringBuilder res = new StringBuilder();
        
        if (num >= 1000000000){
            res.append(helper(num / 1000000000)).append(" Billion ").append(helper(num % 1000000000));
        } else if (num >= 1000000) {
            res.append(helper(num / 1000000)).append(" Million ").append(helper(num % 1000000));
        } else if (num >= 1000){
            res.append(helper(num / 1000)).append(" Thousand ").append(helper(num % 1000));
        } else if (num >= 100){
            res.append(helper(num / 100)).append(" Hundred ").append(helper(num % 100));
        } else if (num >= 20){
            res.append(belowHundred[num / 10]).append(" ").append(belowTen[num % 10]);
        } else if (num >= 10){
            res.append(belowTwenty[num % 10]);
        } else { // num < 10
            res.append(belowTen[num]);
        }
        
        return res.toString().trim();
    }
}
```

> 复杂度分析

遍历字符串，时间复杂度O(n)

额外使用String记录，空间复杂度O(1)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：37.6 MB, 在所有 Java 提交中击败了66.67%的用户
