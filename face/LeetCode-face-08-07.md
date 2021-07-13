### LeetCode-face-08-07

> 题目链接

[LeetCode-face-08-07](https://leetcode-cn.com/problems/permutation-i-lcci/)

> 思路

锁定前面的值，后面的不断交换，完成全部组合的选择

> 代码

```java
class Solution {
    public String[] permutation(String S) {
        char[] text = S.toCharArray();
        List<String> list = new ArrayList<>();
        work(text, list, 0);
        String[] result = new String[list.size()];
        list.toArray(result);
        return result;
    }

    public void work(char[] text, List<String> list, int start){
        if(start == text.length - 1) list.add(new String(text));
        else{
            for(int i = start; i < text.length; i++){
                swap(text, start, i);
                work(text, list, start + 1);
                swap(text, start, i);
            }
        }
    }

    public void swap(char[] text, int i, int j){
        if(i == j) return;
        char c = text[i];
        text[i] = text[j];
        text[j] = c;
    }

}
```

> 复杂度分析

共有n!个组合，时间复杂度O(n!) 

额外使用List，空间复杂度O(n)

> 总结

执行用时：3 ms, 在所有 Java 提交中击败了99.91%的用户

内存消耗：46 MB, 在所有 Java 提交中击败了75.37%的用户
