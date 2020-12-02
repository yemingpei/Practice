### LeetCode-855-Exam-Room

> 题目链接

[LeetCode-855-Exam-Room](https://leetcode.com/problems/exam-room/)

> 思路

遍历一遍list，找到最大的距离的位置，和插入的位置，不断地维护list，暴力法求解

> 代码

```java
class ExamRoom {
    int size;
    ArrayList<Integer> list = new ArrayList();
    
    public ExamRoom(int N) {
        size = N;
    }
    
    public int seat() {
        if (list.isEmpty()) {
          list.add(0);
          return 0;
        }
        int position = 0;
            int pos = 0;
        int num = list.get(0);
        int pre = num;
        for (int j = 1; j < list.size(); j++) {
          int d = (list.get(j) - pre) / 2;
          if (d > num) {
            num = d;
            position = pre + d;
                    pos = j;
          }
          pre = list.get(j);
        }
        if (size - 1 - pre > num){
                position = size - 1;
                list.add(position);
            }else{
                list.add(pos,position);
            }

        return position;
    }
    
    public void leave(int p) {
        list.remove((Integer)p);
    }
}
```

> 复杂度分析

每次都遍历一遍list，list的长度最大为n，时间复杂度O(n)

额外使用了list，大小最大应该为n，空间复杂度O(n)

> 总结

Runtime: 13 ms, faster than 80.42% of Java online submissions for Exam Room.

Memory Usage: 39.6 MB, less than 52.94% of Java online submissions for Exam Room.
