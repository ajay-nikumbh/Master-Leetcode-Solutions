# [169. Majority Element (Easy)](https://leetcode.com/problems/majority-element/)

<p>Given an array <code>nums</code> of size <code>n</code>, return <em>the majority element</em>.</p>

<p>The majority element is the element that appears more than <code>⌊n / 2⌋</code> times. You may assume that the majority element always exists in the array.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [3,2,3]
<strong>Output:</strong> 3
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [2,2,1,1,1,2,2]
<strong>Output:</strong> 2
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == nums.length</code></li>
	<li><code>1 &lt;= n &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>-2<sup>31</sup> &lt;= nums[i] &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

<p>&nbsp;</p>
<strong>Follow-up:</strong> Could you solve the problem in linear time and in <code>O(1)</code> space?

**Companies**:  
[Microsoft](https://leetcode.com/company/microsoft), [Apple](https://leetcode.com/company/apple), [Facebook](https://leetcode.com/company/facebook), [Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Adobe](https://leetcode.com/company/adobe), [Rubrik](https://leetcode.com/company/rubrik)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [Divide and Conquer](https://leetcode.com/tag/divide-and-conquer/), [Sorting](https://leetcode.com/tag/sorting/), [Counting](https://leetcode.com/tag/counting/)

**Similar Questions**:
* [Majority Element II (Medium)](https://leetcode.com/problems/majority-element-ii/)
* [Check If a Number Is Majority Element in a Sorted Array (Easy)](https://leetcode.com/problems/check-if-a-number-is-majority-element-in-a-sorted-array/)

## Video Notes

![Screenshot from 2022-07-31 16-33-41](https://user-images.githubusercontent.com/37560890/183296078-06f078ac-fbb0-4605-bd67-92fdd58ff8a7.png)
![Screenshot from 2022-07-31 16-34-19](https://user-images.githubusercontent.com/37560890/183296080-39c8edc2-73d8-49c7-ac0c-8ad25d8cfb23.png)
![Screenshot from 2022-07-31 16-34-33](https://user-images.githubusercontent.com/37560890/183296082-8dcfcf1e-dffc-4716-ac44-4b39a9f02760.png)
![Screenshot from 2022-07-31 16-35-24](https://user-images.githubusercontent.com/37560890/183296084-76c847be-04b0-481b-bbd7-221fdbd44644.png)
![Screenshot from 2022-07-31 16-35-32](https://user-images.githubusercontent.com/37560890/183296085-74f44773-5bc2-4e0c-a84f-563b405fa1e7.png)
![Screenshot from 2022-07-31 16-35-43](https://user-images.githubusercontent.com/37560890/183296086-e0923bee-1e0f-407e-8cd9-b78b72255c2d.png)
![Screenshot from 2022-07-31 16-37-05](https://user-images.githubusercontent.com/37560890/183296090-e339e43a-26bb-4734-aa5a-4123f11dafd0.png)
![Screenshot from 2022-07-31 16-38-07](https://user-images.githubusercontent.com/37560890/183296093-20b8355e-0844-4975-b297-32d0a82b09be.png)
![Screenshot from 2022-07-31 16-38-12](https://user-images.githubusercontent.com/37560890/183296095-10ac0fdf-9016-4389-af92-6cd9b9427121.png)
![Screenshot from 2022-07-31 16-38-35](https://user-images.githubusercontent.com/37560890/183296097-4324dbf4-e916-43a9-ab7f-8908a0445b15.png)
![Screenshot from 2022-07-31 16-38-41](https://user-images.githubusercontent.com/37560890/183296100-b5ea7cc0-12e2-453c-a342-b1c35b7aac13.png)


## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/majority-element/
// Time: O(N)
// Space: O(1)

class Solution
{
public:
    int majorityElement(vector<int>& nums) 
    {
        // Assign the 2 variables
        int count =0;
        int candidate =0;
        
        // Linearly iterate on array nums
        for(auto num: nums)
        {
            // If the count == 0 then assign the candidate =num
            if(count ==0) candidate = num;
            
            // If the num == candidate then increase the count
            if(num == candidate)    count++;
            
            // Else decrease the count
            else count--;  
        }
        
        // Finally return the candidate
        return candidate;
    }
};


```
