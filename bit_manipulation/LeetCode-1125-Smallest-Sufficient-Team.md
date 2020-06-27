### LeetCode-1125-Smallest-Sufficient-Team

> 题目链接

[LeetCode-1125-Smallest-Sufficient-Team](https://leetcode.com/problems/smallest-sufficient-team/)

> 思路

使用动态规划寻找最优解，利用位运算压缩比较的时间

> 代码

```java
class Solution {
    public int[] smallestSufficientTeam(String[] req_skills, List<List<String>> people) {
        int n=req_skills.length;
        int m=people.size();
        HashMap<String, Integer> map=new HashMap<>();
        int target=0;
        for(int i=0;i<n;i++){
            map.put(req_skills[i],i);
            target|=(1<<i);
        }
        HashMap<Integer,List<Integer>> memo=new HashMap<>();
        memo.put(0,new ArrayList<>());
        int[] pp=new int[m];
        for(int i=0;i<m;i++){           
            for(String str:people.get(i)){
                if(map.containsKey(str)){
                    pp[i]|=(1<<map.get(str));
                }
            }       
        }
        HashMap<Integer,List<Integer>> next=new HashMap<>();
        while(true){
            next=new HashMap<>();
            for(int code:memo.keySet()){
                int index=0;
                while(((code>>index)&1)==1)index++;
                for(int i=0;i<m;i++){
                    if(pp[i]!=0&&((pp[i]>>index)&1)==1){
                        int temp=code|pp[i];
                        if(!next.containsKey(temp)&&!memo.containsKey(temp)){
                            List<Integer> list=new ArrayList<>(memo.get(code));
                            list.add(i);
                            if(temp==target){
                                int[] res=new int[list.size()];
                                Arrays.setAll(res, list::get);
                                return res;
                            }
                            next.put(temp, list);
                        }
                    }
                }
            }
            memo=next;
        }
    }
}
```

> 复杂度分析

使用动态规划，时间复杂度O(n * m)

额外使用HashMap<Integer,List<Integer>>，空间复杂度O(n * m)

> 总结

Runtime: 6 ms, faster than 98.66% of Java online submissions for Smallest Sufficient Team.

Memory Usage: 39.7 MB, less than 67.38% of Java online submissions for Smallest Sufficient Team.
