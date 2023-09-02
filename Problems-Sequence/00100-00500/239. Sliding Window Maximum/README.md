# [239. Sliding Window Maximum (Hard)](https://leetcode.com/problems/sliding-window-maximum/)

<p>You are given an array of integers&nbsp;<code>nums</code>, there is a sliding window of size <code>k</code> which is moving from the very left of the array to the very right. You can only see the <code>k</code> numbers in the window. Each time the sliding window moves right by one position.</p>

<p>Return <em>the max sliding window</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [1,3,-1,-3,5,3,6,7], k = 3
<strong>Output:</strong> [3,3,5,5,6,7]
<strong>Explanation:</strong> 
Window position                Max
---------------               -----
[1  3  -1] -3  5  3  6  7       <strong>3</strong>
 1 [3  -1  -3] 5  3  6  7       <strong>3</strong>
 1  3 [-1  -3  5] 3  6  7      <strong> 5</strong>
 1  3  -1 [-3  5  3] 6  7       <strong>5</strong>
 1  3  -1  -3 [5  3  6] 7       <strong>6</strong>
 1  3  -1  -3  5 [3  6  7]      <strong>7</strong>
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [1], k = 1
<strong>Output:</strong> [1]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> nums = [1,-1], k = 1
<strong>Output:</strong> [1,-1]
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> nums = [9,11], k = 2
<strong>Output:</strong> [11]
</pre>

<p><strong>Example 5:</strong></p>

<pre><strong>Input:</strong> nums = [4,-2], k = 2
<strong>Output:</strong> [4]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= k &lt;= nums.length</code></li>
</ul>


**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Facebook](https://leetcode.com/company/facebook), [ByteDance](https://leetcode.com/company/bytedance), [Bloomberg](https://leetcode.com/company/bloomberg), [Microsoft](https://leetcode.com/company/microsoft), [Citadel](https://leetcode.com/company/citadel), [Twitter](https://leetcode.com/company/twitter), [Akuna Capital](https://leetcode.com/company/akuna-capital)

**Related Topics**:  
[Heap](https://leetcode.com/tag/heap/), [Sliding Window](https://leetcode.com/tag/sliding-window/), [Dequeue](https://leetcode.com/tag/dequeue/)

**Similar Questions**:
* [Minimum Window Substring (Hard)](https://leetcode.com/problems/minimum-window-substring/)
* [Min Stack (Easy)](https://leetcode.com/problems/min-stack/)
* [Longest Substring with At Most Two Distinct Characters (Medium)](https://leetcode.com/problems/longest-substring-with-at-most-two-distinct-characters/)
* [Paint House II (Hard)](https://leetcode.com/problems/paint-house-ii/)
* [Jump Game VI (Medium)](https://leetcode.com/problems/jump-game-vi/)

## Solution 1. Mono-Deque

Assume the array is `[3, 1, 2, ...]` and `k = 3`, popping `3` out of the window will result in max value update, but popping `1` won't. This means that we can just keep track of `[3, 2]`, i.e. a monotonically decreasing sequence of values.

Here we store the `index` of the monotonoically decreasing sequence. When a new value `A[i]` is added to the window, we pop the trailing index in the deque which are pointing to values that are smaller or equal to `A[i]`. Then we can push `i` into the deque.

We need to pop the index which falls out of the window from the deque as well.

```cpp
// OJ: https://leetcode.com/problems/sliding-window-maximum/
// Time: O(N)
// Space: O(N)

class Solution 
{
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k) 
    {
        // Create the deque
        deque<int> dq;
        
        // Create the vector ans
        vector<int> ans;
        
        // Iterate on the nums array
        for(int i=0;i<nums.size();i++)
        {
            // Remove the out of bound elements
            if(!dq.empty() and dq.front() == i-k) dq.pop_front();
            
            // Now remove all the element that are samller than nums[i]
            while(!dq.empty() and nums[dq.back()] <= nums[i]) dq.pop_back();
            
            // Once done with that take the current index into the deque
            dq.push_back(i);
            
            // Now take the maxium and store into the ans
            if(i>=k-1) ans.push_back(nums[dq.front()]);
        }
        
        // Finally return the ans
        return ans;
    }
};
```
