# [493. Reverse Pairs (Hard)](https://leetcode.com/problems/reverse-pairs/)

<p>Given an integer array <code>nums</code>, return <em>the number of <strong>reverse pairs</strong> in the array</em>.</p>

<p>A reverse pair is a pair <code>(i, j)</code> where <code>0 &lt;= i &lt; j &lt; nums.length</code> and <code>nums[i] &gt; 2 * nums[j]</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [1,3,2,3,1]
<strong>Output:</strong> 2
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [2,4,3,5,1]
<strong>Output:</strong> 3
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>-2<sup>31</sup> &lt;= nums[i] &lt;= 2<sup>31</sup> - 1</code></li>
</ul>


**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Microsoft](https://leetcode.com/company/microsoft), [Bloomberg](https://leetcode.com/company/bloomberg)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Binary Search](https://leetcode.com/tag/binary-search/), [Divide and Conquer](https://leetcode.com/tag/divide-and-conquer/), [Binary Indexed Tree](https://leetcode.com/tag/binary-indexed-tree/), [Segment Tree](https://leetcode.com/tag/segment-tree/), [Merge Sort](https://leetcode.com/tag/merge-sort/), [Ordered Set](https://leetcode.com/tag/ordered-set/)

**Similar Questions**:
* [Count of Smaller Numbers After Self (Hard)](https://leetcode.com/problems/count-of-smaller-numbers-after-self/)
* [Count of Range Sum (Hard)](https://leetcode.com/problems/count-of-range-sum/)

## Solution 1. Divide and Conquer (Merge Sort)

```cpp
// OJ: https://leetcode.com/problems/reverse-pairs/
// Author: github.com/lzl124631x
// Time: O(NlogN)
// Space: O(N)
class Solution {
public:
    int reversePairs(vector<int>& A) {
        int N = A.size(), ans = 0;
        vector<int> tmp(N);
        function<void(int, int)> merge = [&](int start, int end) {
            if (end == start + 1) return;
            int mid = (start + end) / 2;
            merge(start, mid);
            merge(mid, end);
            for (int i = start, j = mid, k = start, t = start; k < end; ++k) {
                if (j == end || (i < mid && A[i] <= A[j])) tmp[k] = A[i++];
                else {
                    while (t < mid && A[t] <= (long)A[j] * 2) ++t;
                    ans += mid - t;
                    tmp[k] = A[j++];
                }
            }
            for (int i = start; i < end; ++i) A[i] = tmp[i];
        };
        merge(0, N);
        return ans;
    }
};
```