### LeetCode-offer-38

> 题目链接

[LeetCode-offer-38](https://leetcode-cn.com/problems/zi-fu-chuan-de-pai-lie-lcof/)

> 思路

回溯法，利用固定前面位置，后面位置交换的方式来完成序列的输出，用标记为来记录是否交换过

> 代码

```java
class Solution {
    public ArrayList<String> list=new ArrayList<>();
    public void swap(char[] arr,int i,int j){
        char temp=arr[i];
        arr[i]=arr[j];
        arr[j]=temp;
    }
    public void dfs( char[] chars, int index){
        if(index == chars.length-1) {
            list.add(new String(chars));
            return;
        }
        boolean[] flag=new boolean[26];
        for (int i = index; i < chars.length; i++) {
            if(flag[chars[i]-'a']==false) {
                flag[chars[i]-'a']=true;
                swap(chars,index,i);
                dfs(chars,index+1);
                swap(chars,i,index);
            }
        }
    }
    public String[] permutation(String s) {
        char[] chars=s.toCharArray();
        dfs(chars,0);
        String[] output=list.toArray(new String[0]);
        return output;
    }
}
```

> 复杂度分析

有n!个排列，时间复杂度O(n!)

额外使用list来辅助，空间复杂度O(n)

> 总结

执行用时：5 ms, 在所有 Java 提交中击败了99.58%的用户

内存消耗：42.7 MB, 在所有 Java 提交中击败了80.51%的用户
