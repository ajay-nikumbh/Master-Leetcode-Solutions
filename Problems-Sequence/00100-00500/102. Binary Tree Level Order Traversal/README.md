# [102. Binary Tree Level Order Traversal (Medium)](https://leetcode.com/problems/binary-tree-level-order-traversal/)

<p>Given a binary tree, return the <i>level order</i> traversal of its nodes' values. (ie, from left to right, level by level).</p>

<p>
For example:<br>
Given binary tree <code>[3,9,20,null,null,15,7]</code>,<br>
</p><pre>    3
   / \
  9  20
    /  \
   15   7
</pre>
<p></p>
<p>
return its level order traversal as:<br>
</p><pre>[
  [3],
  [9,20],
  [15,7]
]
</pre>
<p></p>

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Breadth-first Search](https://leetcode.com/tag/breadth-first-search/)

**Similar Questions**:
* [Binary Tree Zigzag Level Order Traversal (Medium)](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)
* [Binary Tree Level Order Traversal II (Easy)](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)
* [Minimum Depth of Binary Tree (Easy)](https://leetcode.com/problems/minimum-depth-of-binary-tree/)
* [Binary Tree Vertical Order Traversal (Medium)](https://leetcode.com/problems/binary-tree-vertical-order-traversal/)
* [Average of Levels in Binary Tree (Easy)](https://leetcode.com/problems/average-of-levels-in-binary-tree/)
* [N-ary Tree Level Order Traversal (Medium)](https://leetcode.com/problems/n-ary-tree-level-order-traversal/)
* [Cousins in Binary Tree (Easy)](https://leetcode.com/problems/cousins-in-binary-tree/)

## Video Notes

![1  Stiver video notes  1-53 -1-201_pages-to-jpg-0062](https://user-images.githubusercontent.com/37560890/169857810-925cbec3-c7dc-4ab3-8ada-2e1a24b5fa41.jpg)
![1  Stiver video notes  1-53 -1-201_pages-to-jpg-0063](https://user-images.githubusercontent.com/37560890/169857932-af0543ea-953f-4547-bc55-6c3e9d8e5fef.jpg)
![1  Stiver video notes  1-53 -1-201_pages-to-jpg-0064](https://user-images.githubusercontent.com/37560890/169858077-643dbc76-337b-4a92-a162-1f8fc9bffcd0.jpg)
![1  Stiver video notes  1-53 -1-201_pages-to-jpg-0065](https://user-images.githubusercontent.com/37560890/169858051-89c6f82b-bcd5-4a10-a247-146eddbf24f4.jpg)
![1  Stiver video notes  1-53 -1-201_pages-to-jpg-0069](https://user-images.githubusercontent.com/37560890/169858341-3d22fa64-dbd2-4a42-a4b6-42a491f913d9.jpg)

## My personal notes

```cpp
Algorithm

1. Check for the base case i.e whether the root is null.
2. Declare the 2d vector ans.
3. Declare the queue of type treenode & push the root node.
4. Declare the temp pointer and the len variable.
5. While till the queue is not empty.
     .Compute the length of the queue.
     .Make the temp vector for that level named as v.
     .Declare the i for the iterator.
     .while i<len
          .Extract the front node.
          .Pop the front node
          .Push the value of front node into the v.
          .If the left alive then push the left into the queue.
          .If the right exists then push the right into the queue.
          .Increment the i value.
     .Push the temp vector into the final ans variable.
6. Finally return the ans vector.

```

## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/binary-tree-level-order-traversal/
// Time: O(N)
// Space: O(N)

class Solution 
{
public:
    vector<vector<int>> levelOrder(TreeNode* root) 
    {
        // Base case checking
        if(root==NULL) return {};
        
        // Decalre the variable's
        vector<vector<int>> ans;
        queue<TreeNode *> q;
        q.push(root);
        TreeNode *temp;
        int len;
        
        // Iterate till the q is not empty
        while(!q.empty())
        {
            // Compute the length
            len= q.size();
            
            // Make the temp vector for that level 
            vector<int> v;
            
            // Declare the i for the iterator 
            int i=0;
            
            // Level wise push the nodes
            while(i<len)
            {
                // Extract the front node
                temp= q.front();
                
                // Pop the node 
                q.pop();
                
                // Push back the node's value
                v.push_back(temp->val);
                
                // If the left alive then push the left into the queue
                if(temp->left) q.push(temp->left);
                
                // If the right exists then push the right into the queue
                if(temp->right) q.push(temp->right);
                
                // Increment the i variable
                i++;
                
            }
            
            // Push the temp vector into the final ans variable
            ans.push_back(v);
        }
        
        // Finallly return the ans
        return ans;
        
    }
    
};

```
