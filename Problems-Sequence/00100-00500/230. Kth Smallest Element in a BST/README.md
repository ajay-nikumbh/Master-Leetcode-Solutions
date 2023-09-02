# [230. Kth Smallest Element in a BST (Medium)](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)

<p>Given the <code>root</code> of a binary search tree, and an integer <code>k</code>, return <em>the</em> <code>k<sup>th</sup></code> <em>smallest value (<strong>1-indexed</strong>) of all the values of the nodes in the tree</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/01/28/kthtree1.jpg" style="width: 212px; height: 301px;">
<pre><strong>Input:</strong> root = [3,1,4,null,2], k = 1
<strong>Output:</strong> 1
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/01/28/kthtree2.jpg" style="width: 382px; height: 302px;">
<pre><strong>Input:</strong> root = [5,3,6,2,4,null,null,1], k = 3
<strong>Output:</strong> 3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is <code>n</code>.</li>
	<li><code>1 &lt;= k &lt;= n &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= Node.val &lt;= 10<sup>4</sup></code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> If the BST is modified often (i.e., we can do insert and delete operations) and you need to find the kth smallest frequently, how would you optimize?</p>


**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Uber](https://leetcode.com/company/uber), [Facebook](https://leetcode.com/company/facebook)

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Binary Search Tree](https://leetcode.com/tag/binary-search-tree/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

**Similar Questions**:
* [Binary Tree Inorder Traversal (Easy)](https://leetcode.com/problems/binary-tree-inorder-traversal/)
* [Second Minimum Node In a Binary Tree (Easy)](https://leetcode.com/problems/second-minimum-node-in-a-binary-tree/)

## Solution 0. Inorder traversal 

// OJ: https://leetcode.com/problems/kth-smallest-element-in-a-bst/
// Time: O(N)
// Space: O(H)


```cpp

class Solution 
{
public:
    // Decalre the vector
    vector<int> a;
    
    // Calling the kth samllest function
    int kthSmallest(TreeNode* root, int k)
    {
    	// Calling the inorder functions
    	inorder(root);
	
	// Return the k-1 as an answer
        int ans = a[k-1];
	
	// Finally return the ans
        return ans;
    }
    
    // Inorder helper method
    void inorder(TreeNode* root)
    {
    	// Base case handling
        if(!root) return;
	
	// Calling the left 
        inorder(root->left);
	
	// Push the value
        a.push_back(root->val);
	
	// Calling the right
        inorder(root->right);
    }
};
```



## Solution 1. In-order traversal (Recursive)

```cpp
// OJ: https://leetcode.com/problems/kth-smallest-element-in-a-bst/
// Time: O(N)
// Space: O(H)

class Solution 
{
public:
    
    int solve(TreeNode *root, int &k)
    {
        // Edge case handling
        if(!root) return 0;
        
        // Go to the left
        int left= solve(root->left, k);
        
        // If the left has value 1 that means we got our value and so return it
        if(left) return left;
        
        // Else do the further processing
        // Decrement the k value
        k -= 1;
        
        // Check if the k ==0
        if(k==0) return root->val;
        
        // Go and explore the right subtree
        int right= solve(root->right, k);
        
        // If the right has found the required kth smallest value then return it else 0 
        return right;
        
    }
    
    int kthSmallest(TreeNode* root, int k) 
    {
        // Return the solve function
        return solve(root, k);
    }
};
```

## Solution 2. In-order traversal (Iterative)

```cpp
// OJ: https://leetcode.com/problems/kth-smallest-element-in-a-bst/
// Time: O(N)
// Space: O(H)

class Solution
{
public:
    int kthSmallest(TreeNode* root, int k) 
    {
    	// Decalre the stack of type TreeNode
    	stack<TreeNode*> s;
	
	// Loop till the condition fails
        while (root || s.size()) 
	{
            // Go to the left 
	    while (root) 
	    {
	    	// Push the root node and go to the left node
                s.push(root);
                root = root->left;
            }
	    
	    // Extract the topmost node
            root = s.top();
	    
	    // Pop the top node
            s.pop();
	    
	    // If the k ==0 then return the root->val
            if (--k == 0) return root->val;
	    
	    // If k != 0 then go to the right side
            root = root->right;
	    
        }
	
	// Finally if no value return then return -1
        return -1;
    }
};
```
