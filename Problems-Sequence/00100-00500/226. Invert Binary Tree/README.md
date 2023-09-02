# [226. Invert Binary Tree (Easy)](https://leetcode.com/problems/invert-binary-tree/)

<p>Given the <code>root</code> of a binary tree, invert the tree, and return <em>its root</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/14/invert1-tree.jpg" style="width: 500px; height: 165px;">
<pre><strong>Input:</strong> root = [4,2,7,1,3,6,9]
<strong>Output:</strong> [4,7,2,9,6,3,1]
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/14/invert2-tree.jpg" style="width: 500px; height: 120px;">
<pre><strong>Input:</strong> root = [2,1,3]
<strong>Output:</strong> [2,3,1]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> root = []
<strong>Output:</strong> []
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[0, 100]</code>.</li>
	<li><code>-100 &lt;= Node.val &lt;= 100</code></li>
</ul>


**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Adobe](https://leetcode.com/company/adobe), [Facebook](https://leetcode.com/company/facebook), [LinkedIn](https://leetcode.com/company/linkedin), [Apple](https://leetcode.com/company/apple), [VMware](https://leetcode.com/company/vmware)

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/invert-binary-tree/
// Time: O(N)
// Space: O(H)

class Solution 
{
public:
    TreeNode* invertTree(TreeNode* root) 
    {
        // Edge case handling
        if(!root) return NULL;
        
        // Swap the left and right pointers
        swap(root->left , root->right);
        
        // Calling the 2 recursive functions
        invertTree(root->left);
        invertTree(root->right);
        
        // Finallly return the root
        return root;
    }
};

```

or 

```cpp

class Solution
{
public:
    TreeNode* invertTree(TreeNode* root) 
    {
        // Make the stack 
        stack<TreeNode*> s;
        
        // Push the root node into the stack
        s.push(root);
        
        // Iterate on the stack till the stack is not empty
        while (!s.empty()) 
        {
            // Extract the topmost node
            TreeNode* curr = s.top();
            
            // Pop the topmost node
            s.pop();
            
            // Edge case checking
            if (!curr) continue;
            
            // Make the 2 recursive calls
            s.push(curr->left);
            s.push(curr->right);
            
            // Swap the root->left and root->right
            swap(curr->left, curr->right);
        }
        
        // Finally return root
        return root;
    }
};
```
