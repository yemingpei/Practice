### LeetCode-638-shopping-offers

> 题目链接

[LeetCode-638-shopping-offers](https://leetcode-cn.com/problems/shopping-offers/)

> 思路

先计算不用礼包的价格，然后用礼包匹配是否有更优解

> 代码

```java
class Solution {
    private List<List<Integer>> special;
    private List<Integer> prices ;
    private int ans =0;
    public int shoppingOffers(List<Integer> prices, List<List<Integer>> special, List<Integer> needs) {
        this.special = special;
        this.prices = prices;
        for (int i = 0; i < needs.size(); i++) {
            ans+= (needs.get(i) * prices.get(i));
        }
        dfs(0,needs,0);
        return ans;
    }
    private void  dfs(int d,List<Integer> needs,int price){
        for (int i = d; i < special.size(); i++) {
            List<Integer> sp = special.get(i);
            boolean check = check(needs,sp);
            Integer total = sp.get(needs.size());
            if(!check || ans < total) continue;
            for (int j = 0; j < needs.size(); j++) {
                needs.set(j,needs.get(j)-sp.get(j));
            }
            dfs(i,needs,price + total);
            for (int j = 0; j < needs.size(); j++) {
                needs.set(j,needs.get(j)+sp.get(j));
            }
        }
        for (int i = 0; i < needs.size(); i++) {
            price +=(needs.get(i) * prices.get(i));
        }
        ans = Math.min(price,ans);
    }
    private boolean check(List<Integer> needs,List<Integer> special){
        for (int i = 0; i < needs.size(); i++) {
            if(needs.get(i) < special.get(i)) return false;
        }
        return true;
    }
}
```

> 复杂度分析

深度遍历，时间复杂度O(nm)

额外使用List，空间复杂度O(nm)

> 总结

执行用时：2 ms, 在所有 Java 提交中击败了96.95%的用户

内存消耗：37.5 MB, 在所有 Java 提交中击败了93.26%的用户
