# [108. Convert Sorted Array to Binary Search Tree (Easy)](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)

<p>Given an integer array <code>nums</code> where the elements are sorted in <strong>ascending order</strong>, convert <em>it to a <strong>height-balanced</strong> binary search tree</em>.</p>

<p>A <strong>height-balanced</strong> binary tree is a binary tree in which the depth of the two subtrees of every node never differs by more than one.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/02/18/btree1.jpg" style="width: 302px; height: 222px;">
<pre><strong>Input:</strong> nums = [-10,-3,0,5,9]
<strong>Output:</strong> [0,-3,9,-10,null,5]
<strong>Explanation:</strong> [0,-10,5,null,-3,null,9] is also accepted:
<img alt="" src="https://assets.leetcode.com/uploads/2021/02/18/btree2.jpg" style="width: 302px; height: 222px;">
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/02/18/btree.jpg" style="width: 342px; height: 142px;">
<pre><strong>Input:</strong> nums = [1,3]
<strong>Output:</strong> [3,1]
<strong>Explanation:</strong> [1,3] and [3,1] are both a height-balanced BSTs.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
	<li><code>nums</code> is sorted in a <strong>strictly increasing</strong> order.</li>
</ul>


**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Facebook](https://leetcode.com/company/facebook), [Google](https://leetcode.com/company/google), [Apple](https://leetcode.com/company/apple)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Divide and Conquer](https://leetcode.com/tag/divide-and-conquer/), [Tree](https://leetcode.com/tag/tree/), [Binary Search Tree](https://leetcode.com/tag/binary-search-tree/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

**Similar Questions**:
* [Convert Sorted List to Binary Search Tree (Medium)](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/)

## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/
// Time: O(N)
// Space: O(logN)


class Solution 
{
public:
    
    TreeNode *helper(vector<int>&nums,int left, int right)
    {
        // Base case checking
        if(left>right) return NULL;
        
        // Compute the middle of the node
        int mid= left+ (left+right)/2;
        
        // Make the new node 
        TreeNode *temp = new TreeNode(nums[mid]);
        
        // Left part from the middle will be left subtree
        temp->left= helper(nums,left,mid-1);
        
        // From mid+1 till right will be its right subtree
        temp->right= helper(nums,mid+1,right);
        
        // Finally return the temp
        return temp;
    }
    
    TreeNode* sortedArrayToBST(vector<int>& nums) 
    {
        // Finally retrun the ans
        return helper(nums,0,nums.size()-1);
    }
};
```
