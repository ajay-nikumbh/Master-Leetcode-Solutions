# [42. Trapping Rain Water (Hard)](https://leetcode.com/problems/trapping-rain-water/)

<p>Given <code>n</code> non-negative integers representing an elevation map where the width of each bar is <code>1</code>, compute how much water it can trap after raining.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img src="https://assets.leetcode.com/uploads/2018/10/22/rainwatertrap.png" style="width: 412px; height: 161px;">
<pre><strong>Input:</strong> height = [0,1,0,2,1,0,1,3,2,1,2,1]
<strong>Output:</strong> 6
<strong>Explanation:</strong> The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> height = [4,2,0,3,2,5]
<strong>Output:</strong> 9
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == height.length</code></li>
	<li><code>1 &lt;= n &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>0 &lt;= height[i] &lt;= 10<sup>5</sup></code></li>
</ul>


**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Facebook](https://leetcode.com/company/facebook), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Bloomberg](https://leetcode.com/company/bloomberg), [Microsoft](https://leetcode.com/company/microsoft), [Google](https://leetcode.com/company/google), [Apple](https://leetcode.com/company/apple), [Adobe](https://leetcode.com/company/adobe), [Intel](https://leetcode.com/company/intel), [Rubrik](https://leetcode.com/company/rubrik), [Uber](https://leetcode.com/company/uber), [Citadel](https://leetcode.com/company/citadel), [Snapchat](https://leetcode.com/company/snapchat), [VMware](https://leetcode.com/company/vmware), [Qualtrics](https://leetcode.com/company/qualtrics), [Paypal](https://leetcode.com/company/paypal), [Tesla](https://leetcode.com/company/tesla), [Zoho](https://leetcode.com/company/zoho), [Intuit](https://leetcode.com/company/intuit), [Oracle](https://leetcode.com/company/oracle)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Two Pointers](https://leetcode.com/tag/two-pointers/), [Dynamic Programming](https://leetcode.com/tag/dynamic-programming/), [Stack](https://leetcode.com/tag/stack/), [Monotonic Stack](https://leetcode.com/tag/monotonic-stack/)

**Similar Questions**:
* [Container With Most Water (Medium)](https://leetcode.com/problems/container-with-most-water/)
* [Product of Array Except Self (Medium)](https://leetcode.com/problems/product-of-array-except-self/)
* [Trapping Rain Water II (Hard)](https://leetcode.com/problems/trapping-rain-water-ii/)
* [Pour Water (Medium)](https://leetcode.com/problems/pour-water/)

## Solution 1.

The water that can be held at position `i` is `max(0, min(left[i], right[i]) - A[i])` where `left[i]` is the maximum height to the left of `i` and `right[i]` is the maximum height to the right of `i`.

```cpp
// OJ: https://leetcode.com/problems/trapping-rain-water/
// Time: O(N)
// Space: O(N)

class Solution 
{
public:
    int trap(vector<int>& A) 
    {
    	// Compute the size of n and decalre the ans =0
    	int N = A.size(), ans = 0;
	
	// Make the 2 arrays for the left and right prefix max storage
        vector<int> left(N, 0), right(N, 0);
	
	// Compute the prefix left max
        for (int i = 1; i < N; ++i) left[i] = max(left[i - 1], A[i - 1]);
	
	// Compute the prefix right max
        for (int i = N - 2; i >= 0; --i) right[i] = max(right[i + 1], A[i + 1]);
	
	// Update the ans 
        for (int i = 1; i < N - 1; ++i) ans += max(0, min(left[i], right[i]) - A[i]);
	
	// Finally return the ans
        return ans;
    }
};
```

Or compute `left` on the fly.

```cpp
// OJ: https://leetcode.com/problems/trapping-rain-water/
// Time: O(N)
// Space: O(N)

class Solution 
{
public:
    int trap(vector<int>& A) 
    {
    	// Compute the size of n and decalre the variables
    	int N = A.size(), ans = 0, mx = 0, left = 0;
	
	// Decalre the vector right
        vector<int> right(N);
	
	// Compute the right
        for (int i = N - 2; i >= 0; --i) right[i] = max(right[i + 1], A[i + 1]);
	
	// Update the ans and left
        for (int i = 0; i < N; ++i)
	{
            ans += max(0, min(left, right[i]) - A[i]);
            left = max(left, A[i]);
        }
	
	// Finally return the ans
        return ans;
    }
};
```


## Solution 2. Two Pointers


```cpp
// OJ: https://leetcode.com/problems/trapping-rain-water/
// Time: O(N)
// Space: O(1)

class Solution 
{
public:
    int trap(vector<int>& height) 
    {
        // Create the 2 pointers
        int left = 0, right = height.size()-1, water =0 , left_max =0 , right_max =0;
        
        // Loop till the condition fails
        while(left <= right)
        {
            // The if will ensure  that keeping the leftmin
            if(height[left] < height[right])
            {
                // Update the left_max
                if(height[left] >= left_max) left_max= height[left];
                
                // Else add the water 
                else water = water + (left_max-height[left]);
                    
                // At last incrment the left pointer
                left++;
            }
            
            else
            {
                // Update the left_max
                if(height[right] >= right_max) right_max= height[right];
                
                // Else add the water 
                else water = water + (right_max-height[right]);
                    
                // At last decrement the right pointer
                right--;
            }
        }
        // Finally return the total water stored
        return water;
    }
};
```
