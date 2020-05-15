### LeetCode-352-Data-Stream-as-Disjoint-Intervals

> 题目链接

[LeetCode-352-Data-Stream-as-Disjoint-Intervals](https://leetcode.com/problems/data-stream-as-disjoint-intervals/)

> 思路

利用题目[LeetCode-35-Search-Insert-Position](https://leetcode.com/problems/search-insert-position/)的解作为二分查找的函数，寻找要插入的值的位置，
然后和前一个，以及后一个对比，能合并则合并，分为四种情况，第一前后都不能合并，则直接插入，如果只有前面合并或者只有后面，则直接合并，如果前后都合并，则需要
合并两个数组，并移除后面的那个

> 代码

```java
class SummaryRanges {

  public SummaryRanges() {
      intvs = new ArrayList();
  }

  private ArrayList<int[]> intvs;

	public int searchInsert(ArrayList<int[]> list, int target) {
		int low = 0;
		int hight = list.size() - 1;
		while (hight >= low) {
			int mid = low + ((hight - low) >> 1);
			if (list.get(mid)[0] >= target) {
				if ((mid == 0) || list.get(mid - 1)[0] < target)
					return mid;
				else
					hight = mid - 1;
			} else
				low = mid + 1;
		}
		return list.size();
	}

	public void addNum(int val) {
		int[] mergedIntv = { val, val };
		if (intvs.isEmpty())
			intvs.add(mergedIntv);
		else {
			int position = searchInsert(intvs, val);
			boolean rightMerge = false;
			boolean leftMerge = false;
			if (position < intvs.size()) {
				if (intvs.get(position)[0] - 1 == val) {
					rightMerge = true;
					intvs.get(position)[0] = val;
				} else if (intvs.get(position)[0] == val) {
					return;
				}
			}
			if (position != 0) {
				if (intvs.get(position - 1)[1] + 1 == val) {
					leftMerge = true;
					intvs.get(position - 1)[1] = val;
				} else if (intvs.get(position - 1)[1] >= val) {
					return;
				}
			}
			if (!rightMerge && !leftMerge) {
				intvs.add(position, mergedIntv);
			} else if (rightMerge && leftMerge) {
				intvs.get(position - 1)[1] = intvs.get(position)[1];
				intvs.remove(position);
			}
		}

	}

	public int[][] getIntervals() {
		return intvs.toArray(new int[intvs.size()][]);
	}
}
```

> 复杂度分析

如果有remove和add操作，时间复杂度为n，如果没有remove和add操作，那时间复杂度为logn，intvs.toArray，转换时间为n，均摊时间复杂度O(n)

额外使用了List,空间复杂度O(n)

> 总结

Runtime: 58 ms, faster than 100.00% of Java online submissions for Data Stream as Disjoint Intervals.

Memory Usage: 44.7 MB, less than 100.00% of Java online submissions for Data Stream as Disjoint Intervals.
