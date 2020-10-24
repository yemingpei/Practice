### LeetCode-241-Different-Ways-to-Add-Parentheses

> 题目链接

[LeetCode-241-Different-Ways-to-Add-Parentheses](https://leetcode.com/problems/different-ways-to-add-parentheses/)

> 思路

记忆递归，寻找运算符，然后就基于运算符，左边和右边分别递归

> 代码

```java
class Solution {
    public Map<String, List<Integer>> map = new HashMap<>();
    
    public List<Integer> diffWaysToCompute(String input) {
        if(map.containsKey(input)) return map.get(input);
        List<Integer> list = new ArrayList<>();
        int len = input.length();
        for(int i = 0; i < len; i++) {
            char c = input.charAt(i);
            if(c == '+' || c == '-' || c == '*') {  
                List<Integer> left = diffWaysToCompute(input.substring(0, i));
                List<Integer> right = diffWaysToCompute(input.substring(i+1, input.length()));
                for(int l : left) {
                    for(int r : right) {
                        switch(c) {
                            case '+':
                                list.add(l + r);
                                break;
                            case '-':
                                list.add(l - r);
                                break;
                            case '*':
                                list.add(l * r);
                                break;
                        }
                    }
                }
            }
        }
        if(list.size() == 0) list.add(Integer.valueOf(input));
        map.put(input, list);
        return list;
    }
}
```

> 复杂度分析

记忆递归法，时间复杂度O(n ^ 2)

额外map保存计算过的结果，空间复杂度O(n ^ 2)

> 总结

Runtime: 1 ms, faster than 99.21% of Java online submissions for Different Ways to Add Parentheses.

Memory Usage: 37.3 MB, less than 5.22% of Java online submissions for Different Ways to Add Parentheses.
