### LeetCode-face-08-08

> 题目链接

[LeetCode-face-08-08](https://leetcode-cn.com/problems/permutation-ii-lcci/)

> 思路

锁定前面的值，后面的不断交换，完成全部组合的选择，需要记录交换过的值，避免出现重复的值

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
            boolean[] flag = new boolean[128];
            for(int i = start; i < text.length; i++){
                if(flag[text[i]]) continue;
                swap(text, start, i);
                work(text, list, start + 1);
                swap(text, start, i);
                flag[text[i]] = true;
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

检索次数为组合数，n!个组合，时间复杂度O(n!) 

额外使用List，空间复杂度O(n)

> 总结

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户

内存消耗：38.1 MB, 在所有 Java 提交中击败了88.77%的用户
