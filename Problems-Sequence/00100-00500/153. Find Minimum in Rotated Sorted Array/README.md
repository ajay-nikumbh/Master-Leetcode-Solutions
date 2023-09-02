# [153. Find Minimum in Rotated Sorted Array (Medium)](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

<p>Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.</p>

<p>(i.e., &nbsp;<code>[0,1,2,4,5,6,7]</code>&nbsp;might become &nbsp;<code>[4,5,6,7,0,1,2]</code>).</p>

<p>Find the minimum element.</p>

<p>You may assume no duplicate exists in the array.</p>

<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> [3,4,5,1,2] 
<strong>Output:</strong> 1
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> [4,5,6,7,0,1,2]
<strong>Output:</strong> 0
</pre>


**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Binary Search](https://leetcode.com/tag/binary-search/)

**Similar Questions**:
* [Search in Rotated Sorted Array (Medium)](https://leetcode.com/problems/search-in-rotated-sorted-array/)
* [Find Minimum in Rotated Sorted Array II (Hard)](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/)

## Solution 1.

Use two pointers `L` and `R` to define the search range. Initially `L = 0`, `R = N - 1`.

If there is only one element, then we don't need to search. So the while condition should be `L < R` instead of `L <= R`.

Let `M = (L + R) / 2`. Since `M` might `= L`, we compare `A[M]` with `A[R]`.

If `A[M] > A[R]`, the min point must be to the right of `A[M]`, so we let `L = M + 1`.

Otherwise, the min point must be to the left of `A[M]` including `A[M]`, so we let `R = M`.

```cpp
// OJ: https://leetcode.com/problems/find-minimum-in-rotated-sorted-array
// Time: O(logN)
// Space: O(1)

class Solution
{
public:
    int findMin(vector<int>& nums) 
    {
        // Make the 2 pointers and initialize it
        int low =0, high= nums.size()-1;
        
        // Loop till the condition fails
        while(low < high)
        {
            // Case 1: The leftmost value is less than the rightmost value in the list
            //         This means that the list is not rotated.
            if(nums[low] < nums[high]) return nums[low];
            
            // Case 2: The value in the middle of the list is greater than the leftmost 
            //         and rightmost values in the list.
            // Compute the mid 
            int mid= low+(high-low)/2;
            
            // Here the ans will always lie in the right half
            if(nums[mid] > nums[high]) low= mid+1;
            
            // Case 3: The value in the middle of the list is less than the leftmost 
            //         and rightmost values in the list.
            else high = mid;
            
        }
        
        // Finally return 
        return nums[low];
    }
};
```
