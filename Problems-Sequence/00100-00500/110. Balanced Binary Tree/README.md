# [110. Balanced Binary Tree (Easy)](https://leetcode.com/problems/balanced-binary-tree/)

<p>Given a binary tree, determine if it is height-balanced.</p>

<p>For this problem, a height-balanced binary tree is defined as:</p>

<blockquote>
<p>a binary tree in which the left and right subtrees of <em>every</em> node differ in height by no more than 1.</p>
</blockquote>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/06/balance_1.jpg" style="width: 342px; height: 221px;">
<pre><strong>Input:</strong> root = [3,9,20,null,null,15,7]
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/06/balance_2.jpg" style="width: 452px; height: 301px;">
<pre><strong>Input:</strong> root = [1,2,2,3,3,null,null,4,4]
<strong>Output:</strong> false
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> root = []
<strong>Output:</strong> true
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[0, 5000]</code>.</li>
	<li><code>-10<sup>4</sup> &lt;= Node.val &lt;= 10<sup>4</sup></code></li>
</ul>


**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Facebook](https://leetcode.com/company/facebook), [Spotify](https://leetcode.com/company/spotify)

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

**Similar Questions**:
* [Maximum Depth of Binary Tree (Easy)](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/balanced-binary-tree/
// Time: O(N)
// Space: O(H)

class Solution 
{
public:
    bool isBalanced(TreeNode* root) 
    {
        // If the tree is empty, we can say it’s balanced...
        if (root == NULL)  return true;
        
	// Height Function will return -1, when it’s an unbalanced tree...
	if (Height(root) == -1)  return false;
		return true;
    }
    // Create a function to return the “height” of a current subtree using recursion...
    int Height(TreeNode* root) 
    {
        // Base case
	if (root == NULL)  return 0;
        
	// Height of left subtree
	int leftHeight = Height(root->left);
        
	// Height of height subtree
	int rightHight = Height(root->right);
        
	// In case of left subtree or right subtree unbalanced or their heights differ by more than ‘1’, return -1
	if (leftHeight == -1 || rightHight == -1 || abs(leftHeight - rightHight) > 1)  return -1;
        
	// Otherwise, return the height of this subtree as max(leftHeight, rightHight) + 1
	return max(leftHeight, rightHight) + 1;
    }
};
```
