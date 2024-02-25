# [1. Two Sum (Easy)](https://leetcode.com/problems/two-sum/)

<p>Given an array of integers <code>nums</code>&nbsp;and an integer <code>target</code>, return <em>indices of the two numbers such that they add up to <code>target</code></em>.</p>

<p>You may assume that each input would have <strong><em>exactly</em> one solution</strong>, and you may not use the <em>same</em> element twice.</p>

<p>You can return the answer in any order.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [2,7,11,15], target = 9
<strong>Output:</strong> [0,1]
<strong>Output:</strong> Because nums[0] + nums[1] == 9, we return [0, 1].
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [3,2,4], target = 6
<strong>Output:</strong> [1,2]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> nums = [3,3], target = 6
<strong>Output:</strong> [0,1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= target &lt;= 10<sup>9</sup></code></li>
	<li><strong>Only one valid answer exists.</strong></li>
</ul>

<p>&nbsp;</p>
<strong>Follow-up:&nbsp;</strong>Can you come up with an algorithm that is less than&nbsp;<code>O(n<sup>2</sup>)&nbsp;</code>time complexity?

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Adobe](https://leetcode.com/company/adobe), [Google](https://leetcode.com/company/google), [Apple](https://leetcode.com/company/apple), [Microsoft](https://leetcode.com/company/microsoft), [Facebook](https://leetcode.com/company/facebook), [Bloomberg](https://leetcode.com/company/bloomberg), [Uber](https://leetcode.com/company/uber), [SAP](https://leetcode.com/company/sap), [Cisco](https://leetcode.com/company/cisco), [Paypal](https://leetcode.com/company/paypal), [tcs](https://leetcode.com/company/tcs), [Yahoo](https://leetcode.com/company/yahoo), [Oracle](https://leetcode.com/company/oracle), [Expedia](https://leetcode.com/company/expedia), [Walmart Labs](https://leetcode.com/company/walmart-labs), [VMware](https://leetcode.com/company/vmware), [Intel](https://leetcode.com/company/intel), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [Morgan Stanley](https://leetcode.com/company/morgan-stanley)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/)

**Similar Questions**:
* [3Sum (Medium)](https://leetcode.com/problems/3sum/)
* [4Sum (Medium)](https://leetcode.com/problems/4sum/)
* [Two Sum II - Input array is sorted (Easy)](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)
* [Two Sum III - Data structure design (Easy)](https://leetcode.com/problems/two-sum-iii-data-structure-design/)
* [Subarray Sum Equals K (Medium)](https://leetcode.com/problems/subarray-sum-equals-k/)
* [Two Sum IV - Input is a BST (Easy)](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/)
* [Two Sum Less Than K (Easy)](https://leetcode.com/problems/two-sum-less-than-k/)
* [Max Number of K-Sum Pairs (Medium)](https://leetcode.com/problems/max-number-of-k-sum-pairs/)
* [Count Good Meals (Medium)](https://leetcode.com/problems/count-good-meals/)

## Video Notes

![Screenshot from 2022-07-29 09-03-14](https://user-images.githubusercontent.com/109052326/183296804-21c498ba-5986-4a60-ac62-e90d8afac6f4.png)
![Screenshot from 2022-07-29 09-04-21](https://user-images.githubusercontent.com/109052326/183296809-887c5eca-b82f-4641-8998-b860445af9f1.png)
![Screenshot from 2022-07-29 09-04-35](https://user-images.githubusercontent.com/109052326/183296812-1ab4b6be-6014-4555-963b-ede48c8764b6.png)
![Screenshot from 2022-07-29 09-07-29](https://user-images.githubusercontent.com/109052326/183296814-d6e92a76-5595-411a-8b22-5cbcdd1ba108.png)
![Screenshot from 2022-07-29 09-07-43](https://user-images.githubusercontent.com/109052326/183296816-e5e0a3e7-59e3-44b4-b462-0aef8412f98b.png)
![Screenshot from 2022-07-29 09-07-59](https://user-images.githubusercontent.com/109052326/183296817-6037719d-e664-4791-bdef-fdff90caba50.png)
![Screenshot from 2022-07-29 09-08-09](https://user-images.githubusercontent.com/109052326/183296818-eef2d5aa-ffe2-40b2-9ef8-48c80d51d9c5.png)




## My personal notes

```cpp

Algorithm

1. Declare the unordered map.
2. Iterate on the nums size.
3. Reduce the target from the current number t= target-a[i].
4. If you find the t in the map then return the map[t th element] and ith element.
5. Else if not found then add the element into the map.
6. Finally return null if not found.

```


## Solution 1 - Python

```py
# OJ: https://leetcode.com/problems/two-sum/
# Time: O(N)
# Space: O(N)

class Solution:
    
    # Define the method
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        
        # Print the incoming nums
        print("Incoming numbers : {} and Respective target : {}".format(nums,target))
        
        # Define the previous_map
        previous_map={}
        
        # Iterate on the nums array
        for index, value in enumerate(nums):
            
            # Compute the difference
            difference = target -value 
            
            # If the difference exists in the previous_map then return the required ans
            if difference in previous_map:
                
                # Return the ans
                return [previous_map[difference],index]
            
            # Else add the element with the index to the previous_map
            previous_map[value] = index
            
        # Else return the empty array
        return {}
```


## Solution 1 - C++

```cpp
// OJ: https://leetcode.com/problems/two-sum/
// Time: O(NlogN)
// Space: O(N)

class Solution 
{
public:
    vector<int> twoSum(vector<int>& nums, int target) 
    {
        // For storing the result
        vector<int> ans;
        
        // Create a hashtable / Map for mapping entries
        unordered_map<int,int> um;
        
        // Iterate on the nums array
        for(int i=0;i<nums.size();i++)
        {
            // If the ans found in the hashtable then do the following
            if(um.find(target-nums[i]) != um.end())
            {
                ans.push_back(um[target-nums[i]]);
                ans.push_back(i);
            }
            
            // If no ans found then
            um[nums[i]] = i;
        }
        
        // Finally return the ans
        return ans;
        
    }
};

```

