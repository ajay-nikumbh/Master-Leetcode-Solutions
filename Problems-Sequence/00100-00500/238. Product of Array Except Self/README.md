# [238. Product of Array Except Self (Medium)](https://leetcode.com/problems/product-of-array-except-self/)

<p>Given an integer array <code>nums</code>, return <em>an array</em> <code>answer</code> <em>such that</em> <code>answer[i]</code> <em>is equal to the product of all the elements of</em> <code>nums</code> <em>except</em> <code>nums[i]</code>.</p>

<p>The product of any prefix or suffix of <code>nums</code> is <strong>guaranteed</strong> to fit in a <strong>32-bit</strong> integer.</p>

<p>You must write an algorithm that runs in&nbsp;<code>O(n)</code>&nbsp;time and without using the division operation.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [1,2,3,4]
<strong>Output:</strong> [24,12,8,6]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [-1,1,0,-3,3]
<strong>Output:</strong> [0,0,9,0,0]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-30 &lt;= nums[i] &lt;= 30</code></li>
	<li>The product of any prefix or suffix of <code>nums</code> is <strong>guaranteed</strong> to fit in a <strong>32-bit</strong> integer.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong>&nbsp;Can you solve the problem in <code>O(1)&nbsp;</code>extra&nbsp;space complexity? (The output array <strong>does not</strong> count as extra space for space complexity analysis.)</p>


**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Amazon](https://leetcode.com/company/amazon), [Apple](https://leetcode.com/company/apple), [Microsoft](https://leetcode.com/company/microsoft), [Asana](https://leetcode.com/company/asana), [Adobe](https://leetcode.com/company/adobe), [Nutanix](https://leetcode.com/company/nutanix), [Lyft](https://leetcode.com/company/lyft), [Nvidia](https://leetcode.com/company/nvidia), [Intel](https://leetcode.com/company/intel), [VMware](https://leetcode.com/company/vmware)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/)

**Similar Questions**:
* [Trapping Rain Water (Hard)](https://leetcode.com/problems/trapping-rain-water/)
* [Maximum Product Subarray (Medium)](https://leetcode.com/problems/maximum-product-subarray/)
* [Paint House II (Hard)](https://leetcode.com/problems/paint-house-ii/)

### Video Notes

![Screenshot from 2022-09-11 15-34-45](https://user-images.githubusercontent.com/37560890/189522727-fa3cf7c7-e76b-44d5-901f-0eb9aabfe4f0.png)
![Screenshot from 2022-09-11 15-35-12](https://user-images.githubusercontent.com/37560890/189522730-c09c92cd-1c88-442a-8b60-90bad94bdcde.png)
![Screenshot from 2022-09-11 15-37-25](https://user-images.githubusercontent.com/37560890/189522734-da2d181d-362f-496b-b48d-b353d25ba4da.png)
![Screenshot from 2022-09-11 15-37-31](https://user-images.githubusercontent.com/37560890/189522736-0d205279-f000-485c-8142-c99daab3206c.png)
![Screenshot from 2022-09-11 15-37-53](https://user-images.githubusercontent.com/37560890/189522740-91c61e6b-50f1-4ea1-890e-4facdc01f1e1.png)
![Screenshot from 2022-09-11 15-40-04](https://user-images.githubusercontent.com/37560890/189522743-06f0305a-1314-44ce-9e48-49694d629874.png)
![Screenshot from 2022-09-11 15-40-18](https://user-images.githubusercontent.com/37560890/189522746-4b6b4b10-593b-4c13-a67e-eac7399f6ff8.png)
![Screenshot from 2022-09-11 15-40-27](https://user-images.githubusercontent.com/37560890/189522749-121226d1-d026-456a-ba44-a29559f146b4.png)
![Screenshot from 2022-09-11 15-41-15](https://user-images.githubusercontent.com/37560890/189522750-4b84a97f-9f79-4ca7-a216-fd0dfc9e772f.png)
![Screenshot from 2022-09-11 15-45-29](https://user-images.githubusercontent.com/37560890/189522752-139b37d7-4aea-4e99-a6bb-fdaf8dbd6ed5.png)
![Screenshot from 2022-09-11 15-46-15](https://user-images.githubusercontent.com/37560890/189522754-9d825b44-d0c9-4138-ab78-13356bc68952.png)
![Screenshot from 2022-09-11 15-46-23](https://user-images.githubusercontent.com/37560890/189522755-70cd1cf6-9815-479c-92f9-b965c2c0b743.png)


## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/product-of-array-except-self/
// https://leetcode.com/problems/product-of-array-except-self/discuss/1597959/c%2B%2B-or-discussing-all-solutions-or-explaining-in-detail-with-image-or
// https://leetcode.com/problems/product-of-array-except-self/discuss/1018111/C%2B%2B-simple-1-pass2-pass-solutions-O(n)-time-O(1)-space-faster-than-99
// https://leetcode.com/problems/product-of-array-except-self/discuss/1597994/C%2B%2BPython-4-Simple-Solutions-w-Explanation-or-Prefix-and-Suffix-product-O(1)-space-approach

// Time: O(N)
// Space: O(1)

class Solution 
{
public:
    vector<int> productExceptSelf(vector<int>& nums) 
    {
        // Compute the size of nums
        int n= nums.size();
        
        // Make the o/p vector
        vector<int> output;
        
        // Edge case checking
        if(n<1) return output;
        
        // Decalre and initialize the product variable
        int product =1;
        
        // Compute the left multiplication cumulative values
        for(int i=0;i<n;i++)
        {
            // Compute the product
            product *= nums[i];
            
            // Push the result into the o/p vector
            output.push_back(product);
        }
        
        // Agian reinitialize the product to 1
        product =1;
        
        // Travel from right and update the o/p array
        for(int i=n-1;i>0;--i)
        {
            // Compute the o/p
            output[i] = output[i-1] *product;
            
            // Update the product
            product *= nums[i];
            
        }
        
        // Oth case handling
        output[0]= product;
        
        
        // Finally return result
        return output;
        
    }
};
```

## Solution 2.

```cpp
// OJ: https://leetcode.com/problems/product-of-array-except-self/
// Time: O(N)
// Space: O(1)

class Solution 
{
public:
    vector<int> productExceptSelf(vector<int>& A) 
    {
        int N = A.size(), left = 1, right = 1;
        vector<int> ans(N, 1);
    
    	for (int i = 0, j = N - 1; i < N; ++i, --j) 
	{
            ans[i] *= left;
            left *= A[i];
            ans[j] *= right;
            right *= A[j];
        }
        return ans;
    }
};
```
