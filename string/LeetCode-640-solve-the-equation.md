### LeetCode-640-solve-the-equation

> 题目链接

[LeetCode-640-solve-the-equation](https://leetcode-cn.com/problems/solve-the-equation/)

> 思路

分别记录x的参数和常数，然后进行约分计算。

> 代码

```java
class Solution {
    public int index = 0;
    public String solveEquation(String equation) {
        StringBuilder sb = StrBuilder(0, equation, new StringBuilder());
        List<String> list = appendString(sb, new ArrayList<>());

        int sumNum = 0;
        int sum = 0;
        for (String re : list) {
            if (re.contains("x")){
                sumNum += xNum(re);
            } else {
                sum += Integer.parseInt(re);
            }
        }

        StringBuilder builder = StrBuilder(index + 1, equation, new StringBuilder());
        List<String> list2 = appendString(builder, new ArrayList<>());

        int sumNum1 = 0;
        int sum1 = 0;
        for (String re : list2) {
            if (re.contains("x")){
                sumNum1 += xNum(re);
            } else {
                sum1 += Integer.parseInt(re);
            }
        }

        int sumNum0 = sumNum1 - sumNum;
        int sum0 = sum - sum1;

        int gcd = Math.abs(gcd(sumNum0, sum0));
        StringBuilder sssss = new StringBuilder();
        if (sumNum0 == 0 && sum0 == 0){
            return "Infinite solutions";
        } else if (sumNum0 == 0 && sum0 != 0){
            return "No solution";
        }

        return sssss.append("x=").append(sum0 / sumNum0).toString();
    }

    public int xNum(String s) {
        if (s.length() == 1){
            return 1;
        }

        StringBuilder sb = new StringBuilder();
        if (s.length() == 2 && (s.charAt(s.length() - 2) == '+' || s.charAt(s.length() - 2) == '-')){
            sb.append(s.charAt(s.length() - 2)).append("1");
            return Integer.parseInt(sb.toString());
        }

        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) != 'x'){
                sb.append(s.charAt(i));
            } else {
                break;
            }
        }

        return Integer.parseInt(sb.toString());
    }

    public int gcd(int x, int y) {
        if (y == 0)
            return x;
        else
            return gcd(y, x % y);
    }

    public List<String> appendString(StringBuilder sb, List<String> res) {
        StringBuilder sb1 = new StringBuilder();
        for (int i = 0; i < sb.toString().length(); i++) {
            if (i + 1 < sb.toString().length() && (sb.toString().charAt(i + 1) == '+' || sb.toString().charAt(i + 1) == '-')) {
                sb1.append(sb.toString().charAt(i));
                res.add(sb1.toString());
                sb1 = new StringBuilder();
            } else {
                sb1.append(sb.toString().charAt(i));
            }
        }

        res.add(sb1.toString());
        return res;
    }

    public StringBuilder StrBuilder(int arrNum, String equation, StringBuilder sb) {
        for (int i = arrNum; i < equation.length(); i++) {
            if (equation.charAt(i) == '='){
                index = i;
                break;
            } else if (equation.charAt(i) != '+' || equation.charAt(i) != '-'){
                sb.append(equation.charAt(i));
            }   else {
                sb = new StringBuilder();
            }
        }

        return sb;
    }
}
```

> 复杂度分析

遍历字符串，时间复杂度O(n)

额外使用List辅助，空间复杂度O(n)

> 总结

执行用时：1 ms, 在所有 Java 提交中击败了95.32%的用户

内存消耗：36.4 MB, 在所有 Java 提交中击败了89.36%的用户
