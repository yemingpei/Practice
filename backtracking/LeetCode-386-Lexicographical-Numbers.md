### LeetCode-386-Lexicographical-Numbers

> 题目链接

[LeetCode-386-Lexicographical-Numbers](https://leetcode.com/problems/lexicographical-numbers/)

> 思路

回溯法，用小到大字母序添加，比如1，10，100，1000，10000，到比n大的时候开始回溯

> 代码

```java
class Solution {
    public List<Integer> lexicalOrder(int n) {
        List<Integer> result = new ArrayList<>();
        for(int i = 1; i < 10; i++){
            if(i <= n){
                result.add(i);
                addNumber(i, n, result);
            }else
                break;
        }
        return result;
    }
    
    public void addNumber(int number, int target, List<Integer> list){
        int num = number * 10;
        for(int i = 0; i < 10; i++){
            int cal = num + i;
            if(cal <= target){
                list.add(cal);
                addNumber(cal, target, list);
            }else
                break;
        }
    }
}
```

> 复杂度分析

每个数都要添加到list，时间复杂度O(n)

额外无额外使用变量，n不超过7位数，空间复杂度O(1)

> 总结

Runtime: 1 ms, faster than 100.00% of Java online submissions for Lexicographical Numbers.

Memory Usage: 44.7 MB, less than 65.91% of Java online submissions for Lexicographical Numbers.
