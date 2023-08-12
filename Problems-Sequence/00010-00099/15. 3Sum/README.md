# [15. 3Sum (Medium)](https://leetcode.com/problems/3sum/)

<p>Given an integer array nums, return all the triplets <code>[nums[i], nums[j], nums[k]]</code> such that <code>i != j</code>, <code>i != k</code>, and <code>j != k</code>, and <code>nums[i] + nums[j] + nums[k] == 0</code>.</p>

<p>Notice that the solution set must not contain duplicate triplets.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [-1,0,1,2,-1,-4]
<strong>Output:</strong> [[-1,-1,2],[-1,0,1]]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = []
<strong>Output:</strong> []
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> nums = [0]
<strong>Output:</strong> []
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= nums.length &lt;= 3000</code></li>
	<li><code>-10<sup>5</sup> &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>


**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Facebook](https://leetcode.com/company/facebook), [Microsoft](https://leetcode.com/company/microsoft), [Apple](https://leetcode.com/company/apple), [Bloomberg](https://leetcode.com/company/bloomberg), [Uber](https://leetcode.com/company/uber), [Google](https://leetcode.com/company/google), [Yahoo](https://leetcode.com/company/yahoo), [VMware](https://leetcode.com/company/vmware), [Walmart Labs](https://leetcode.com/company/walmart-labs), [Cisco](https://leetcode.com/company/cisco), [Rubrik](https://leetcode.com/company/rubrik), [Salesforce](https://leetcode.com/company/salesforce), [eBay](https://leetcode.com/company/ebay), [Adobe](https://leetcode.com/company/adobe)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Two Pointers](https://leetcode.com/tag/two-pointers/)

**Similar Questions**:
* [Two Sum (Easy)](https://leetcode.com/problems/two-sum/)
* [3Sum Closest (Medium)](https://leetcode.com/problems/3sum-closest/)
* [4Sum (Medium)](https://leetcode.com/problems/4sum/)
* [3Sum Smaller (Medium)](https://leetcode.com/problems/3sum-smaller/)

## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/3sum/
// Time: O(N^2)
// Space: O(1)

class Solution 
{
public:
    vector<vector<int>> threeSum(vector<int>& nums) 
    {
        // Make the vector for storing the o/p
        vector<vector<int>> result;
        
        // Sort the array
        sort(nums.begin(), nums.end());
        
        // Iterate on the nums array
        for(int i=0;i<nums.size();i++)
        {
            // b+c = -a
            int target = -nums[i];
            
            // Make the front pointer
            int front= i+1;
            
            // Make the back pointer
            int back = nums.size()-1;
            
            // Start the binary search 
            while(front<back)
            {
                // Compute the sum
                int sum = nums[front] + nums[back];
                
                // Check sum is less or greater
                if(sum < target) front++;
                
                // If the sum is greater then decrement the back
                else if(sum>target) back--;
                
                // Else if match the target
                else
                {
                    // Make the vector 
                    vector<int> triplets ={nums[i],nums[front],nums[back]};
                    
                    // Push the 3riplet
                    result.push_back(triplets);
                    
                    // By pass front duplicates
                    while(front<back and nums[front] == triplets[1] ) front++;
                    
                    // By pass back duplicates
                    while(front<back and nums[back] == triplets[2] ) back--;
                }
            }
            
            // By pass the ith elements
            while(i+1<nums.size() and nums[i+1] == nums[i]) i++;
        }
        
	// Return result
        return result;
    }
};
```
