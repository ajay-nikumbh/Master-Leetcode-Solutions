# [199. Binary Tree Right Side View (Medium)](https://leetcode.com/problems/binary-tree-right-side-view/)

<p>Given a binary tree, imagine yourself standing on the <em>right</em> side of it, return the values of the nodes you can see ordered from top to bottom.</p>

<p><strong>Example:</strong></p>

<pre><strong>Input:</strong>&nbsp;[1,2,3,null,5,null,4]
<strong>Output:</strong>&nbsp;[1, 3, 4]
<strong>Explanation:
</strong>
   1            &lt;---
 /   \
2     3         &lt;---
 \     \
  5     4       &lt;---
</pre>

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-first Search](https://leetcode.com/tag/depth-first-search/), [Breadth-first Search](https://leetcode.com/tag/breadth-first-search/), [Recursion](https://leetcode.com/tag/recursion/), [Queue](https://leetcode.com/tag/queue/)

**Similar Questions**:
* [Populating Next Right Pointers in Each Node (Medium)](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)
* [Boundary of Binary Tree (Medium)](https://leetcode.com/problems/boundary-of-binary-tree/)

## Video Notes

![img391](https://user-images.githubusercontent.com/37560890/170320858-f8cc06d4-c989-44ca-a22f-f7734352be35.jpg)
![img393](https://user-images.githubusercontent.com/37560890/170320868-e7c189a7-7c8c-4b84-a333-e95782a6ee4b.jpg)
![img395](https://user-images.githubusercontent.com/37560890/170320871-a48aabfc-06a2-49cc-a5e3-e736347c1734.jpg)
![img397](https://user-images.githubusercontent.com/37560890/170320873-6265184a-86c1-4f7d-a356-639e5510c267.jpg)
![img399](https://user-images.githubusercontent.com/37560890/170320879-f4a1bb84-5b0d-4d31-972e-777cfbf1cc01.jpg)
![img401](https://user-images.githubusercontent.com/37560890/170320882-b08c15de-3c34-44d5-8b41-069588c2c668.jpg)
![img403](https://user-images.githubusercontent.com/37560890/170320891-04e74767-eb66-4687-857a-d77f29a4ad49.jpg)
![img405](https://user-images.githubusercontent.com/37560890/170320895-d82daa1c-6262-4a94-951b-0b3e4e62b995.jpg)
![img407](https://user-images.githubusercontent.com/37560890/170320908-5c346ef3-c52a-419e-9987-79a2a5fc0e80.jpg)
![img409](https://user-images.githubusercontent.com/37560890/170320913-565d6b48-57b8-469c-aa2c-36fd829fda25.jpg)

## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/binary-tree-right-side-view/
// Time: O(N)
// Space: O(H)

class Solution 
{
public:
    
    void helper(TreeNode *root, int level, vector<int>&ans)
    {
        // If the root is null
        if(root==NULL) return ;
        
        // Push if the level == node.size()
        if(ans.size() == level) ans.push_back(root->val);
        
        // Recursive calls
        helper(root->right,level+1,ans);
        helper(root->left, level+1,ans);
        
    }
    
    vector<int> rightSideView(TreeNode* root) 
    {
        // Create the ans vector
        vector<int> ans;
        
        // Calling the helper function
        helper(root,0,ans);
        
        // Finally return the ans
        return ans;
    }
};

```
## Solution 2.

```cpp
// OJ: https://leetcode.com/problems/binary-tree-right-side-view/
// Time: O(N)
// Space: O(H)

class Solution 
{
    // Declare the ans vector
    vector<int> ans;
    
    // Make the dfs call
    void dfs(TreeNode *root, int lv) 
    {
        // Handle the edge case
        if (!root) return;
        
        // If level == ans.size() then push back the root val
        if (lv == ans.size()) ans.push_back(root->val);
        
        // Else case
        else ans[lv] = root->val;
        
        // Make the 2 recursive calls
        dfs(root->left, lv + 1);
        dfs(root->right, lv + 1);
    }
public:

    vector<int> rightSideView(TreeNode* root) 
    {
        // Calling the dfs call
        dfs(root, 0);
        
        // Finally return the ans
        return ans;
    }
};
```

