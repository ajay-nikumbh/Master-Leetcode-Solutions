# [111. Minimum Depth of Binary Tree (Easy)](https://leetcode.com/problems/minimum-depth-of-binary-tree/)

<p>Given a binary tree, find its minimum depth.</p>

<p>The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.</p>

<p><strong>Note:</strong>&nbsp;A leaf is a node with no children.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/12/ex_depth.jpg" style="width: 432px; height: 302px;">
<pre><strong>Input:</strong> root = [3,9,20,null,null,15,7]
<strong>Output:</strong> 2
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> root = [2,null,3,null,4,null,5,null,6]
<strong>Output:</strong> 5
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[0, 10<sup>5</sup>]</code>.</li>
	<li><code>-1000 &lt;= Node.val &lt;= 1000</code></li>
</ul>


**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-first Search](https://leetcode.com/tag/depth-first-search/), [Breadth-first Search](https://leetcode.com/tag/breadth-first-search/)

**Similar Questions**:
* [Binary Tree Level Order Traversal (Medium)](https://leetcode.com/problems/binary-tree-level-order-traversal/)
* [Maximum Depth of Binary Tree (Easy)](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

## Solution 1. BFS

```cpp
// OJ: https://leetcode.com/problems/minimum-depth-of-binary-tree/
// Time: O(N)
// Space: O(N)

class Solution 
{
public:
    int minDepth(TreeNode* root) 
    {
    	// Edge case
    	if (!root) return 0;
	
	// Make the queue
        queue<TreeNode*> q;
	
	// Push the root node
        q.push(root);
	
	// Make the ans =1
        int ans = 1;
	
	// Iterate till the q is not empty
        while (q.size()) 
	{
            // Compute the size of the queue
	    int cnt = q.size();
	    
	    // Iterate till the q size 
            while (cnt--) 
	    {
            	// Extract the front node
	    	auto node = q.front();
		
		// Pop the front node
                q.pop();
		
		// If it's the leaf node
                if (!node->left && !node->right) return ans;
		
		// Go the left and explore  
                if (node->left) q.push(node->left);
		
		// Go the right and explore
                if (node->right) q.push(node->right);
            }
	    
	    // Increment the ans
            ++ans;
        }
	
	// If not then return -1
        return -1;
    }
};
```

## Solution 2. DFS

```cpp
// OJ: https://leetcode.com/problems/minimum-depth-of-binary-tree/
// Time: O(N)
// Space: O(H)

class Solution 
{
public:
    int minDepth(TreeNode* root) 
    {
        // Base case checking
        if(!root) return 0;
        
        // Check if it's a leaf node
        if(!root->left and !root->right) return 1;
        
        // Iniital dept will be INT_MIN
        int d= INT_MAX;
        
        // Compute the left depth
        if(root->left) d= minDepth(root->left); 
        
        // Compute the right depth
        if(root->right) d= min(d,minDepth(root->right));
        
        // Return 1+d
        return 1+d;
        
        
    }
};
```

or

```cpp
class Solution
{
public:
     int minDepth(TreeNode* root) 
     {
        // Fast input o/p
     	ios_base::sync_with_stdio(false);
        
	// If the root is not there then return 0
	if (!root) return 0;
        
	// Go to the left and right
	int left = minDepth(root->left);
        int right = minDepth(root->right);
	
	// If it's a leaf node 
        if(!root->left || !root->right ) return !root->left ? right + 1 : left + 1;
        
	// Do the following operations
	root->left = NULL;
        root->right = NULL;
	
	// Finally return the mini of left and right +1
        return min(left, right)+1;
    }
};
```
