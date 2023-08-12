# [33. Search in Rotated Sorted Array (Medium)](https://leetcode.com/problems/search-in-rotated-sorted-array/)

<p>Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.</p>

<p>(i.e., <code>[0,1,2,4,5,6,7]</code> might become <code>[4,5,6,7,0,1,2]</code>).</p>

<p>You are given a target value to search. If found in the array return its index, otherwise return <code>-1</code>.</p>

<p>You may assume no duplicate exists in the array.</p>

<p>Your algorithm's runtime complexity must be in the order of&nbsp;<em>O</em>(log&nbsp;<em>n</em>).</p>

<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [<code>4,5,6,7,0,1,2]</code>, target = 0
<strong>Output:</strong> 4
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [<code>4,5,6,7,0,1,2]</code>, target = 3
<strong>Output:</strong> -1</pre>


**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Binary Search](https://leetcode.com/tag/binary-search/)

**Similar Questions**:
* [Search in Rotated Sorted Array II (Medium)](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)
* [Find Minimum in Rotated Sorted Array (Medium)](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

## Solution 1.

Use the solution to [153. Find Minimum in Rotated Sorted Array (Medium)](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/).

We first find the pivot point, then we can do a normal binary search on `[0, pivot - 1]` or `[pivot, N - 1]`.

```cpp
// OJ: https://leetcode.com/problems/search-in-rotated-sorted-array/
// Time: O(logN)
// Space: O(1)

class Solution 
{
public:
    int search(vector<int>& nums, int target) 
    {
        // Create the 2 pointer's
        int low= 0, high= nums.size()-1;
        
        // Loop till the condition fails
        while(low<=high)
        {
            // Compute the mid
            int mid= (low+high) >>1;
            
            // Check if the nums[mid] == target
            if(nums[mid] == target) return mid;
            
            // If the left side is sorted
            if(nums[low] <= nums[mid])
            {
                // Shrink the space if it's on left side 
                if(target>=nums[low] and target<=nums[mid]) high= mid-1;
                
                // Else move to the right side
                else low= mid+1;
            }
            
            // If the right side is sorted
            else
            {
                // Shrink the space if it's on right side 
                if(target>=nums[mid] and target<=nums[high]) low=mid+1;
                
                // Else move to the left side
                else high= mid-1;
            }
        }
        
        // If the target is not found then return -1;
        return -1;
    }
};
```
