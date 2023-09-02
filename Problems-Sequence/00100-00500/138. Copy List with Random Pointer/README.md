# [138. Copy List with Random Pointer (Medium)](https://leetcode.com/problems/copy-list-with-random-pointer/)

<p>A linked list of length <code>n</code> is given such that each node contains an additional random pointer, which could point to any node in the list, or <code>null</code>.</p>

<p>Construct a <a href="https://en.wikipedia.org/wiki/Object_copying#Deep_copy" target="_blank"><strong>deep copy</strong></a> of the list. The deep copy should consist of exactly <code>n</code> <strong>brand new</strong> nodes, where each new node has its value set to the value of its corresponding original node. Both the <code>next</code> and <code>random</code> pointer of the new nodes should point to new nodes in the copied list such that the pointers in the original list and copied list represent the same list state. <strong>None of the pointers in the new list should point to nodes in the original list</strong>.</p>

<p>For example, if there are two nodes <code>X</code> and <code>Y</code> in the original list, where <code>X.random --&gt; Y</code>, then for the corresponding two nodes <code>x</code> and <code>y</code> in the copied list, <code>x.random --&gt; y</code>.</p>

<p>Return <em>the head of the copied linked list</em>.</p>

<p>The linked list is represented in the input/output as a list of <code>n</code> nodes. Each node is represented as a pair of <code>[val, random_index]</code> where:</p>

<ul>
	<li><code>val</code>: an integer representing <code>Node.val</code></li>
	<li><code>random_index</code>: the index of the node (range from <code>0</code> to <code>n-1</code>) that the <code>random</code> pointer points to, or <code>null</code> if it does not point to any node.</li>
</ul>

<p>Your code will <strong>only</strong> be given the <code>head</code> of the original linked list.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/12/18/e1.png" style="width: 700px; height: 142px;">
<pre><strong>Input:</strong> head = [[7,null],[13,0],[11,4],[10,2],[1,0]]
<strong>Output:</strong> [[7,null],[13,0],[11,4],[10,2],[1,0]]
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/12/18/e2.png" style="width: 700px; height: 114px;">
<pre><strong>Input:</strong> head = [[1,1],[2,1]]
<strong>Output:</strong> [[1,1],[2,1]]
</pre>

<p><strong>Example 3:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2019/12/18/e3.png" style="width: 700px; height: 122px;"></strong></p>

<pre><strong>Input:</strong> head = [[3,null],[3,0],[3,null]]
<strong>Output:</strong> [[3,null],[3,0],[3,null]]
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> head = []
<strong>Output:</strong> []
<strong>Explanation:</strong> The given linked list is empty (null pointer), so return null.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= n &lt;= 1000</code></li>
	<li><code>-10000 &lt;= Node.val &lt;= 10000</code></li>
	<li><code>Node.random</code> is <code>null</code> or is pointing to some node in the linked list.</li>
</ul>


**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [Linked List](https://leetcode.com/tag/linked-list/)

**Similar Questions**:
* [Clone Graph (Medium)](https://leetcode.com/problems/clone-graph/)
* [Clone Binary Tree With Random Pointer (Medium)](https://leetcode.com/problems/clone-binary-tree-with-random-pointer/)
* [Clone N-ary Tree (Medium)](https://leetcode.com/problems/clone-n-ary-tree/)

## Video Notes

![Screenshot from 2022-08-02 19-01-14](https://user-images.githubusercontent.com/109052326/183301397-3014f206-a0dd-4489-a3ac-ddce4c1e172d.png)
![Screenshot from 2022-08-02 19-02-23](https://user-images.githubusercontent.com/109052326/183301401-e253b4c8-72d5-4b05-a724-3aeb63802e2b.png)
![Screenshot from 2022-08-02 19-03-36](https://user-images.githubusercontent.com/109052326/183301403-66a43910-cae1-45d8-9292-1e1377bc5359.png)
![Screenshot from 2022-08-02 19-05-06](https://user-images.githubusercontent.com/109052326/183301405-e5f41d77-e119-411d-8177-1d590b3c5272.png)
![Screenshot from 2022-08-02 19-05-29](https://user-images.githubusercontent.com/109052326/183301409-ba1c443f-5638-40e6-9b80-e17112fb285a.png)
![Screenshot from 2022-08-02 19-06-49](https://user-images.githubusercontent.com/109052326/183301410-e965b7ea-0f4f-431f-b3c7-74e8023b3207.png)
![Screenshot from 2022-08-02 19-09-42](https://user-images.githubusercontent.com/109052326/183301412-37112502-1e73-4b25-b96b-d365c88caef9.png)
![Screenshot from 2022-08-02 19-10-36](https://user-images.githubusercontent.com/109052326/183301414-d58cee56-e181-470b-b24a-4570f22e4a10.png)
![Screenshot from 2022-08-02 19-11-44](https://user-images.githubusercontent.com/109052326/183301416-02fa89d8-bd55-49f0-98c5-09329962a713.png)
![Screenshot from 2022-08-02 19-12-01](https://user-images.githubusercontent.com/109052326/183301420-c3f29b0f-b8a3-4ed7-ab23-33f1432bae01.png)
![Screenshot from 2022-08-02 19-12-23](https://user-images.githubusercontent.com/109052326/183301424-025d0d74-6fbf-430d-b15c-9f2af95c2c51.png)
![Screenshot from 2022-08-02 19-15-35](https://user-images.githubusercontent.com/109052326/183301426-9da80792-74c9-46a1-9699-5cb651864c3e.png)
![Screenshot from 2022-08-02 19-16-16](https://user-images.githubusercontent.com/109052326/183301428-18d6dd62-dd93-49a5-aae3-c308efddfbd8.png)
![Screenshot from 2022-08-02 19-17-28](https://user-images.githubusercontent.com/109052326/183301430-06ae81e5-613f-4151-913a-6ea769a60a2e.png)
![Screenshot from 2022-08-02 19-17-33](https://user-images.githubusercontent.com/109052326/183301432-e3a1aa8d-41de-492c-9032-207871d191f3.png)



## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/copy-list-with-random-pointer/
// Time: O(N)
// Space: O(1)

class Solution 
{
public:
    Node* copyRandomList(Node* head) 
    {
        // Make the 2 dummy pointers
        Node *iter= head;
        Node *front= head;
        
        // 1st round = Make a copy of each node
        while(iter)
        {
            // Place the front
            front= iter->next;
            
            // Make the new node
            Node *copy = new Node(iter->val);
            
            // Update the iter->next
            iter->next= copy;
            
            // Update copy->next
            copy->next= front;
            
            // Update iter
            iter= front;
            
        }
        
        // 2nd round = Assign the random ptrs for copy nodes
        iter= head;
        
        while(iter)
        {
            if(iter->random)
            {
                iter->next->random = iter->random->next;
            }
            
            // Update the iter next
            iter= iter->next->next;
        }
        
        // 3rd round = Restore the original list and extract the original list
        iter = head;
        Node *pseudoHead = new Node(0);
        Node *copy = pseudoHead;

        while (iter != NULL) 
        {
            front = iter->next->next;

            // extract the copy
            copy->next = iter->next;

            // restore the original list
            iter->next = front;
            
            // Update the copy pointeer
            copy = copy -> next; 
            
            // Update the iter
            iter = front;
        }

        // Return the new header
        return pseudoHead->next;   
    }
};

```
