### LeetCode-face-16-20

> 题目链接

[LeetCode-face-16-20](https://leetcode-cn.com/problems/t9-lcci/)

> 思路

先构建map查询表，然后遍历数组，一一比较每个字符串的字符

> 代码

```java
class Solution {
    public List<String> getValidT9Words(String num, String[] words) {
        HashMap<Character, Character> map = new HashMap<>();
        map.put('a', '2');
        map.put('b', '2');
        map.put('c', '2');
        map.put('d', '3');
        map.put('e', '3');
        map.put('f', '3');
        map.put('g', '4');
        map.put('h', '4');
        map.put('i', '4');
        map.put('j', '5');
        map.put('k', '5');
        map.put('l', '5');
        map.put('m', '6');
        map.put('n', '6');
        map.put('o', '6');
        map.put('p', '7');
        map.put('q', '7');
        map.put('r', '7');
        map.put('s', '7');
        map.put('t', '8');
        map.put('u', '8');
        map.put('v', '8');
        map.put('w', '9');
        map.put('x', '9');
        map.put('y', '9');
        map.put('z', '9');
        List<String> list = new ArrayList<>();
        char[] number = num.toCharArray();
        for(String text : words){
            if(matchWords(number, text, map)) list.add(text);
        }
        return list;
    }

    public boolean matchWords(char[] num, String text, HashMap<Character, Character> map){
        char[] stringtext = text.toCharArray();
        for(int i = 0; i < stringtext.length; i++){
            if(map.get(stringtext[i]) != num[i]) return false;
        }
        return true;
    }

}
```

> 复杂度分析

遍历数组，时间复杂度O(mn)

额外使用常量的26长度的map，空间复杂度O(1)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了86.61%的用户

内存消耗：39.6 MB, 在所有 Java 提交中击败了97.69%的用户
