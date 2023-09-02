# [236. Lowest Common Ancestor of a Binary Tree (Medium)](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)

<p>Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.</p>

<p>According to the <a href="https://en.wikipedia.org/wiki/Lowest_common_ancestor" target="_blank">definition of LCA on Wikipedia</a>: “The lowest common ancestor is defined between two nodes <code>p</code> and <code>q</code> as the lowest node in <code>T</code> that has both <code>p</code> and <code>q</code> as descendants (where we allow <b>a node to be a descendant of itself</b>).”</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2018/12/14/binarytree.png" style="width: 200px; height: 190px;">
<pre><strong>Input:</strong> root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
<strong>Output:</strong> 3
<strong>Explanation:</strong> The LCA of nodes 5 and 1 is 3.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2018/12/14/binarytree.png" style="width: 200px; height: 190px;">
<pre><strong>Input:</strong> root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4
<strong>Output:</strong> 5
<strong>Explanation:</strong> The LCA of nodes 5 and 4 is 5, since a node can be a descendant of itself according to the LCA definition.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> root = [1,2], p = 1, q = 2
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[2, 10<sup>5</sup>]</code>.</li>
	<li><code>-10<sup>9</sup> &lt;= Node.val &lt;= 10<sup>9</sup></code></li>
	<li>All <code>Node.val</code> are <strong>unique</strong>.</li>
	<li><code>p != q</code></li>
	<li><code>p</code> and <code>q</code> will exist in the tree.</li>
</ul>


**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Google](https://leetcode.com/company/google), [LinkedIn](https://leetcode.com/company/linkedin), [Adobe](https://leetcode.com/company/adobe), [Apple](https://leetcode.com/company/apple), [Uber](https://leetcode.com/company/uber), [Zillow](https://leetcode.com/company/zillow), [Walmart Labs](https://leetcode.com/company/walmart-labs), [Reddit](https://leetcode.com/company/reddit), [Atlassian](https://leetcode.com/company/atlassian), [Riot Games](https://leetcode.com/company/riot-games)

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

**Similar Questions**:
* [Lowest Common Ancestor of a Binary Search Tree (Easy)](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)
* [Smallest Common Region (Medium)](https://leetcode.com/problems/smallest-common-region/)
* [Lowest Common Ancestor of a Binary Tree II (Medium)](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree-ii/)
* [Lowest Common Ancestor of a Binary Tree III (Medium)](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree-iii/)
* [Lowest Common Ancestor of a Binary Tree IV (Medium)](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree-iv/)

## Video Notes

![img459](https://user-images.githubusercontent.com/37560890/170345436-af049d7b-8bba-4123-a4dc-9adb5c012383.jpg)
![img461](https://user-images.githubusercontent.com/37560890/170345443-19cf06b5-3eac-4e20-ac65-37a74e7a31ad.jpg)
![img463](https://user-images.githubusercontent.com/37560890/170345447-e0374a2f-2075-4f0c-a6c6-b55c4acea3c1.jpg)
![img465](https://user-images.githubusercontent.com/37560890/170345450-8ee5f9ce-5efe-4975-bbc7-4c7d7bc50b44.jpg)
![img467](https://user-images.githubusercontent.com/37560890/170345454-b67b8f9a-5603-4799-b773-355c4a3e0d4a.jpg)
![img469](https://user-images.githubusercontent.com/37560890/170345458-8a103d8d-21a5-44d9-b504-d5feab79dc91.jpg)
![img471](https://user-images.githubusercontent.com/37560890/170345460-534ecac3-c541-4530-b260-1175d0442844.jpg)
![img473](https://user-images.githubusercontent.com/37560890/170345463-a40726a8-bba1-4de2-ab0d-41b831e53068.jpg)
![img475](https://user-images.githubusercontent.com/37560890/170345467-2b70538a-5ef6-46b9-aa7e-6b8668238738.jpg)
![img477](https://user-images.githubusercontent.com/37560890/170345472-f6a45d47-52bb-4b7e-96b2-7b93ca290f18.jpg)
![img479](https://user-images.githubusercontent.com/37560890/170345474-ffc1fc95-71f4-4c93-a2fa-8a0f0c274756.jpg)
![img481](https://user-images.githubusercontent.com/37560890/170345478-1b9199fc-3a38-43b2-8cb1-2983e99704b9.jpg)
![img483](https://user-images.githubusercontent.com/37560890/170345480-061efe7b-9992-4e97-b363-6822f4b778e2.jpg)
![img485](https://user-images.githubusercontent.com/37560890/170345483-8c620e87-5c44-429c-9ad0-99ba6489d023.jpg)
![img487](https://user-images.githubusercontent.com/37560890/170345486-089f26f0-02c9-4e3f-8dcc-481bc604752f.jpg)
![img489](https://user-images.githubusercontent.com/37560890/170345492-85020889-add4-4aba-9951-da6a00ee2d16.jpg)
![img491](https://user-images.githubusercontent.com/37560890/170345493-195908bb-4cf8-48bd-b654-3792ffb904cb.jpg)
![img493](https://user-images.githubusercontent.com/37560890/170345498-8bc50242-5c36-42e7-ad7f-713710885c63.jpg)
![img495](https://user-images.githubusercontent.com/37560890/170345499-81e3ad17-50ab-4218-9ca8-689199905cf2.jpg)
![img497](https://user-images.githubusercontent.com/37560890/170345504-903a654a-57d8-4948-b134-321ce7d8cb9c.jpg)
![img499](https://user-images.githubusercontent.com/37560890/170345505-83c691cf-d03b-4279-a25b-c81342e885d9.jpg)
![img501](https://user-images.githubusercontent.com/37560890/170345508-e3d79467-8741-4408-b097-b557c4f9b5bc.jpg)
![img503](https://user-images.githubusercontent.com/37560890/170345510-33040795-7d58-4fed-b67e-e965257c9091.jpg)
![img505](https://user-images.githubusercontent.com/37560890/170345513-90a0b6e5-caf0-4d27-b385-0044abcccd42.jpg)


## Solution 1.

Get the two paths from root to target nodes, and return the last node that appears in both paths. Also, this solution works even when `p` or `q` is not found (i.e. [1644. Lowest Common Ancestor of a Binary Tree II (Medium)](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree-ii/))

```cpp
// OJ: https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/
// Time: O(N)
// Space: O(H)

class Solution 
{
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) 
    {
        // Handle the base case
        if(root==NULL or root==p or root==q) return root;
        
        // Supply the 2 recursive calls
        TreeNode *left= lowestCommonAncestor(root->left,p, q) ;
        TreeNode *right=lowestCommonAncestor(root->right,p,q) ;
        
        // If the left appears to be null
        if(left==NULL) return right;
        
        // Else return right
        else if(right==NULL) return left;
        
        // If that is not the case then return the root i.e we found the ans
        else
        {
            return root;
        }   
    } 
};
```
