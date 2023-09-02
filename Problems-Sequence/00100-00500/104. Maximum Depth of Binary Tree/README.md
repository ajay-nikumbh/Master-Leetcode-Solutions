# [104. Maximum Depth of Binary Tree (Easy)](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

<p>Given the <code>root</code> of a binary tree, return <em>its maximum depth</em>.</p>

<p>A binary tree's <strong>maximum depth</strong>&nbsp;is the number of nodes along the longest path from the root node down to the farthest leaf node.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/26/tmp-tree.jpg" style="width: 400px; height: 277px;">
<pre><strong>Input:</strong> root = [3,9,20,null,null,15,7]
<strong>Output:</strong> 3
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> root = [1,null,2]
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[0, 10<sup>4</sup>]</code>.</li>
	<li><code>-100 &lt;= Node.val &lt;= 100</code></li>
</ul>


**Companies**:  
[LinkedIn](https://leetcode.com/company/linkedin), [Amazon](https://leetcode.com/company/amazon), [Google](https://leetcode.com/company/google), [Spotify](https://leetcode.com/company/spotify), [Microsoft](https://leetcode.com/company/microsoft)

**Related Topics**:  
[Tree](https://leetcode.com/tag/tree/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/), [Binary Tree](https://leetcode.com/tag/binary-tree/)

**Similar Questions**:
* [Balanced Binary Tree (Easy)](https://leetcode.com/problems/balanced-binary-tree/)
* [Minimum Depth of Binary Tree (Easy)](https://leetcode.com/problems/minimum-depth-of-binary-tree/)
* [Maximum Depth of N-ary Tree (Easy)](https://leetcode.com/problems/maximum-depth-of-n-ary-tree/)
* [Time Needed to Inform All Employees (Medium)](https://leetcode.com/problems/time-needed-to-inform-all-employees/)

### Video Notes

![Screenshot from 2022-09-04 08-40-56](https://user-images.githubusercontent.com/37560890/188295522-d797751d-e6ea-4d9f-8c4c-e5a94ade000f.png)
![Screenshot from 2022-09-04 08-41-12](https://user-images.githubusercontent.com/37560890/188295524-892c0eed-8fe3-4abb-a623-96bdd4c4a1b4.png)
![Screenshot from 2022-09-04 08-42-00](https://user-images.githubusercontent.com/37560890/188295526-898eae32-f70d-4799-9330-1e055fc3e8f3.png)
![Screenshot from 2022-09-04 08-43-45](https://user-images.githubusercontent.com/37560890/188295528-b7e10d14-0286-445b-842b-47cc5b5ebb8a.png)
![Screenshot from 2022-09-04 08-43-57](https://user-images.githubusercontent.com/37560890/188295529-94217f26-549e-4324-b8ae-7a2ee32740db.png)



## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/maximum-depth-of-binary-tree/
// Author: github.com/lzl124631x
// Time: O(N)
// Space: O(N)
class Solution {
public:
    int maxDepth(TreeNode* root) {
        return root ? 1 + max(maxDepth(root->left), maxDepth(root->right)) : 0;
    }
};
```
