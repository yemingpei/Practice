### LeetCode-715-Range-Module

> 题目链接

[LeetCode-715-Range-Module](https://leetcode.com/problems/range-module/)

> 思路

思路同[LeetCode-352-Data-Stream-as-Disjoint-Intervals](https://leetcode.com/problems/data-stream-as-disjoint-intervals/)

> 代码

```java
class RangeModule {

  public RangeModule() {

  }

  private ArrayList<int[]> intvs = new ArrayList();

	public int searchInsert(ArrayList<int[]> list, int target,
    int position) {
    int low = 0;
    int hight = list.size() - 1;
    while (hight >= low) {
      int mid = low + ((hight - low) >> 1);
      if (list.get(mid)[position] >= target) {
        if ((mid == 0) || list.get(mid - 1)[position] < target)
          return mid;
        else
          hight = mid - 1;
      } else
        low = mid + 1;
    }
    return list.size();
	}

	public void remove(int l, int r) {
		int start = Math.min(r, intvs.size() - 1);
		for (int j = start; j > l; j--)
			intvs.remove(j);
	}

	public void addRange(int left, int right) {
		int[] mergedIntv = { left, right };
		if (intvs.isEmpty())
			intvs.add(mergedIntv);
		else {
			int leftStart = searchInsert(intvs, left, 0);
			int rightStart = searchInsert(intvs, right, 0);
			int leftEnd = searchInsert(intvs, left, 1);
			int rightEnd = searchInsert(intvs, right, 1);
			boolean leftMerge = leftStart != leftEnd;
			boolean rightMerge = rightStart != rightEnd;
			if (!leftMerge && !rightMerge) {
				if (leftEnd == rightEnd)
					intvs.add(rightStart, mergedIntv);
				else {
					if (rightEnd < intvs.size()&& right == intvs.get(rightEnd)[0]) {
						intvs.get(leftEnd)[0] = left;
						intvs.get(leftEnd)[1] = intvs.get(rightEnd)[1];
						remove(leftEnd, rightEnd);
					} else {
						intvs.get(leftEnd)[0] = left;
						intvs.get(leftEnd)[1] = right;
						remove(leftEnd, rightEnd - 1);
					}
				}
			} else if (rightMerge) {
				int max = Math.max(right, intvs.get(rightEnd)[1]);
				int min = Math.min(left, intvs.get(leftEnd)[0]);
				intvs.get(leftEnd)[0] = min;
				intvs.get(leftEnd)[1] = max;
				if (leftEnd != rightEnd)
					remove(leftEnd, rightEnd);
			} else if(rightEnd < intvs.size()&& right == intvs.get(rightEnd)[0]){
				intvs.get(leftEnd)[1] = intvs.get(rightEnd)[1];
				remove(leftEnd, rightEnd);
			}
			else{
				intvs.get(leftEnd)[1] = right;
				remove(leftEnd, rightEnd - 1);
			}
		}
	}

	public boolean queryRange(int left, int right) {
		int leftStart = searchInsert(intvs, left, 0);
		int leftEnd = searchInsert(intvs, left, 1);
		int rightEnd = searchInsert(intvs, right, 1);
		boolean leftSame = leftStart == leftEnd;
		boolean positionSame = leftEnd == rightEnd;
		if (positionSame && leftSame && leftEnd < intvs.size()
				&& left == intvs.get(leftEnd)[0])
			return true;
		if (positionSame && !leftSame)
			return true;
		return false;
	}

	public void removeRange(int left, int right) {
		int leftStart = searchInsert(intvs, left, 0);
		int rightStart = searchInsert(intvs, right, 0);
		int leftEnd = searchInsert(intvs, left, 1);
		int rightEnd = searchInsert(intvs, right, 1);
		boolean leftRemove = leftStart != leftEnd;
		boolean rightRemove = rightStart != rightEnd;
		if (leftRemove && rightRemove) {
			if (leftEnd == rightEnd) {
				if (right == intvs.get(leftEnd)[1])
					intvs.get(leftEnd)[1] = left;
				else {
					int[] newInt = { intvs.get(leftEnd)[0], left };
					intvs.get(leftEnd)[0] = right;
					intvs.add(leftEnd, newInt);
				}
			} else {
				intvs.get(leftEnd)[1] = left;
				if (intvs.get(rightEnd)[1] == right) {
					remove(leftEnd, rightEnd);
				} else {
					intvs.get(rightEnd)[0] = right;
					remove(leftEnd, rightEnd - 1);
				}
			}
		} else if (leftRemove) {
			intvs.get(leftEnd)[1] = left;
			remove(leftEnd, rightEnd - 1);
		} else if (rightRemove) {
			if (intvs.get(rightEnd)[1] == right) {
				remove(leftEnd - 1, rightEnd);
			} else {
				intvs.get(rightEnd)[0] = right;
				remove(leftEnd - 1, rightEnd - 1);
			}
		} else {
			remove(leftEnd - 1, rightEnd - 1);
		}
	}
}
```

> 复杂度分析

如果有remove和add操作，时间复杂度为n，queryRange操作，那时间复杂度为logn，均摊时间复杂度O(n)

额外使用了List,空间复杂度O(n)

> 总结

Runtime: 46 ms, faster than 66.36% of Java online submissions for Range Module.

Memory Usage: 47.8 MB, less than 100.00% of Java online submissions for Range Module.
