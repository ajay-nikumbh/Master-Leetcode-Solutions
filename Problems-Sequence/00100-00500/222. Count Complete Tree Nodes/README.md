# [222. Count Complete Tree Nodes (Medium)](https://leetcode.com/problems/count-complete-tree-nodes/)

<p>Given a <b>complete</b> binary tree, count the number of nodes.</p>

<p><b>Note: </b></p>

<p><b><u>Definition of a complete binary tree from <a href="http://en.wikipedia.org/wiki/Binary_tree#Types_of_binary_trees" target="_blank">Wikipedia</a>:</u></b><br>
In a complete binary tree every level, except possibly the last, is completely filled, and all nodes in the last level are as far left as possible. It can have between 1 and 2<sup>h</sup> nodes inclusive at the last level h.</p>

<p><strong>Example:</strong></p>

<pre><strong>Input:</strong> 
    1
   / \
  2   3
 / \  /
4  5 6

<strong>Output:</strong> 6</pre>


**Related Topics**:  
[Binary Search](https://leetcode.com/tag/binary-search/), [Tree](https://leetcode.com/tag/tree/)

**Similar Questions**:
* [Closest Binary Search Tree Value (Easy)](https://leetcode.com/problems/closest-binary-search-tree-value/)

## Solution 1.

Given a subtree, we just compute the lengths of the leftmost path and the rightmost path.

* if they are the same, then this subtree is complete and its node count is `2^length - 1`.
* otherwise, we recursively count nodes for the left subtree and the right subtree and return the sum of them plus 1.

```cpp
// OJ: https://leetcode.com/problems/count-complete-tree-nodes/
// Time: O(H^2)
// Space: O(H)

class Solution
{
public:

    int countNodes(TreeNode* root) 
    {
        // Handle the base case
        if(!root) return 0;

        // Declare the 2 variable's
        int hl=0, hr=0;

        // Declare the 2 pointer's
        TreeNode *l=root, *r=root;

        // If the left exist's then incr the left height and move left
        while(l) {hl++;l=l->left;}

        // If the right exists then incr the right height and move right
        while(r) {hr++;r=r->right;}

        // If both the leftheight== rightheight then 2^h -1 will be our ans
        if(hl==hr) return pow(2,hl)-1;

        // Return the 1 + 2 recursive calls left and right
        return 1+countNodes(root->left)+countNodes(root->right);
    }

};
```
