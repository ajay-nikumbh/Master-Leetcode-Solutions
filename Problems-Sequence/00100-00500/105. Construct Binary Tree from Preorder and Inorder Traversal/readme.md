<h1><a href="https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/">105. Construct Binary Tree from Preorder and Inorder Traversal</a></h1>
<div><p>Given two integer arrays <code>preorder</code> and <code>inorder</code> where <code>preorder</code> is the preorder traversal of a binary tree and <code>inorder</code> is the inorder traversal of the same tree, construct and return <em>the binary tree</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/02/19/tree.jpg" style="width: 277px; height: 302px;">
<pre><strong>Input:</strong> preorder = [3,9,20,15,7], inorder = [9,3,15,20,7]
<strong>Output:</strong> [3,9,20,null,null,15,7]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> preorder = [-1], inorder = [-1]
<strong>Output:</strong> [-1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= preorder.length &lt;= 3000</code></li>
	<li><code>inorder.length == preorder.length</code></li>
	<li><code>-3000 &lt;= preorder[i], inorder[i] &lt;= 3000</code></li>
	<li><code>preorder</code> and <code>inorder</code> consist of <strong>unique</strong> values.</li>
	<li>Each value of <code>inorder</code> also appears in <code>preorder</code>.</li>
	<li><code>preorder</code> is <strong>guaranteed</strong> to be the preorder traversal of the tree.</li>
	<li><code>inorder</code> is <strong>guaranteed</strong> to be the inorder traversal of the tree.</li>
</ul>
</div>

## Video Notes

![img265](https://user-images.githubusercontent.com/37560890/170551135-29420baa-755d-4b59-96d7-ee1967c72792.jpg)
![img267](https://user-images.githubusercontent.com/37560890/170551137-a2609ead-c467-4fdc-9475-dc554380c294.jpg)
![img269](https://user-images.githubusercontent.com/37560890/170551140-01a548da-af92-4ca8-a44d-e7738a10127e.jpg)
![img271](https://user-images.githubusercontent.com/37560890/170551143-cdfb27a2-c805-4e9c-8857-dcdb1f0495b0.jpg)
![img273](https://user-images.githubusercontent.com/37560890/170551147-d0b3a1f3-c897-4ed1-b08c-1b2644059266.jpg)
![img275](https://user-images.githubusercontent.com/37560890/170551152-fee6e742-fe57-4917-bab3-cb35405d0f67.jpg)
![img277](https://user-images.githubusercontent.com/37560890/170551156-24948fd4-8bdb-4319-bc79-203cd832c8b1.jpg)
![img279](https://user-images.githubusercontent.com/37560890/170551158-61a89fbc-2688-4583-9373-9fc3fdc68c62.jpg)
![img281](https://user-images.githubusercontent.com/37560890/170551161-e0443a3d-2494-41c1-866d-30d5aa802baa.jpg)
![img283](https://user-images.githubusercontent.com/37560890/170551163-c09fd6c4-025d-4950-856d-2bd6b1f2d1df.jpg)
![img285](https://user-images.githubusercontent.com/37560890/170551167-5d625dc2-2300-48c9-a73a-348679d3ec31.jpg)
![img287](https://user-images.githubusercontent.com/37560890/170551169-124c9406-26b2-47f9-b001-eef82abc1ef8.jpg)
![img245](https://user-images.githubusercontent.com/37560890/170551175-efe77511-9d6b-4f7a-b079-15adb943cb00.jpg)
![img247](https://user-images.githubusercontent.com/37560890/170551179-63c34560-f89b-4ad9-97bf-d4b40d27f6d9.jpg)
![img249](https://user-images.githubusercontent.com/37560890/170551182-7f30cc51-19c5-4529-8353-06d27d5fbed3.jpg)
![img251](https://user-images.githubusercontent.com/37560890/170551183-0e4d3edd-6696-4095-8c21-133c8d8aef33.jpg)
![img253](https://user-images.githubusercontent.com/37560890/170551188-469fb0c8-17a4-4720-9b5b-b4d5b6a5f66d.jpg)
![img221](https://user-images.githubusercontent.com/37560890/170552064-d88f22b1-3f95-478d-8b35-8026b69cd58d.jpg)
![img223](https://user-images.githubusercontent.com/37560890/170552069-a59297ae-e741-4747-8438-1fa2f60dbc6a.jpg)
![img225](https://user-images.githubusercontent.com/37560890/170552071-fa5a69a5-64ed-4a30-a5e4-bd69f1306795.jpg)
![img227](https://user-images.githubusercontent.com/37560890/170552077-36f8cdab-5fcc-4e03-a4db-c76e92f747e8.jpg)
![img229](https://user-images.githubusercontent.com/37560890/170552082-9b15cf61-52b4-4a14-8e31-d075700ad5ba.jpg)
![img231](https://user-images.githubusercontent.com/37560890/170552085-089850e6-b210-4ebc-8e08-c65f4fc969df.jpg)
![img233](https://user-images.githubusercontent.com/37560890/170552087-d6857015-f4e6-48cc-a494-5ee696f27889.jpg)

```cpp

// Time Complexity: O(N)
// Space Complexity : O(N)

class Solution 
{
public:
    
    // Helper method
    TreeNode* construct(vector<int>&preorder, int preStart, int preEnd, vector<int> &inorder,
    			int inStart, int inEnd, map<int,int> &mp)
    {
        // Edge case
        if(preStart>preEnd || inStart>inEnd) return NULL;
        
        // Make a new root
        TreeNode* root = new TreeNode(preorder[preStart]);
        
        // Find the inroot from the map
        int inRoot = mp[root->val];
        
        // Find the leftmost elements
        int numsLeft = inRoot-inStart;
        
        // Build left and right subtree
        root->left = construct(preorder,preStart+1,preStart+numsLeft,inorder,inStart,inRoot-1,mp);
        root->right = construct(preorder,preStart+numsLeft+1,preEnd,inorder,inRoot+1,inEnd,mp);
        
        // Return root
        return root;
    }
    
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) 
    {
        // Make a map for hashing the inorder
        map<int,int> mp;
        
        // Hash the inorder array
        for(int i=0;i<preorder.size();i++)
        {
            mp[inorder[i]]=i;
        }
        
        // Calling the recursive function
        TreeNode* root = construct(preorder,0,preorder.size()-1,inorder,0,inorder.size()-1,mp);
        
        // Return the root
        return root;
    }
   
};

```
