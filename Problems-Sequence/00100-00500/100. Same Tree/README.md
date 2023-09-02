# [100. Same Tree (Easy)](https://leetcode.com/problems/same-tree/)

<p>Given two binary trees, write a function to check if they are the same or not.</p>

<p>Two binary trees are considered the same if they are structurally identical and the nodes have the same value.</p>

<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong>     1         1
          / \       / \
         2   3     2   3

        [1,2,3],   [1,2,3]

<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong>     1         1
          /           \
         2             2

        [1,2],     [1,null,2]

<strong>Output:</strong> false
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong>     1         1
          / \       / \
         2   1     1   2

        [1,2,1],   [1,1,2]

<strong>Output:</strong> false
</pre>


**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-first Search](https://leetcode.com/tag/depth-first-search/)

## My personal notes.

```cpp
Algorithm

1. 3 cases it will be same tree.
      a. Both the trees are NULL.
      b. If both p and q are alive and both p->val == q->val.
      c. Explore it's children and check for left and right.
 
2. Finally return the above condition. 
```

## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/same-tree/
// Time: O(N)
// Space: O(H)

class Solution 
{
public:
    bool isSameTree(TreeNode* p, TreeNode* q) 
    {
        // 3 cases it will be same tree
        
        // 1. Both the trees are NULL
        // 2. If both p and q are alive and both p->val == q->val 
        // 3. Explore it's children and check for left and right
         return (!p and !q) || 
                (p and q and p->val == q->val and 
                isSameTree(p->left,q->left) and 
                isSameTree(p->right, q->right));
    }
};
```
