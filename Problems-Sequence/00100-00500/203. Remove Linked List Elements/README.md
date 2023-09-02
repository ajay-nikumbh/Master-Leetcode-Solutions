# [203. Remove Linked List Elements (Easy)](https://leetcode.com/problems/remove-linked-list-elements/)

<p>Given the <code>head</code> of a linked list and an integer <code>val</code>, remove all the nodes of the linked list that has <code>Node.val == val</code>, and return <em>the new head</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/06/removelinked-list.jpg" style="width: 500px; height: 142px;">
<pre><strong>Input:</strong> head = [1,2,6,3,4,5,6], val = 6
<strong>Output:</strong> [1,2,3,4,5]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> head = [], val = 1
<strong>Output:</strong> []
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> head = [7,7,7,7], val = 7
<strong>Output:</strong> []
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the list is in the range <code>[0, 10<sup>4</sup>]</code>.</li>
	<li><code>1 &lt;= Node.val &lt;= 50</code></li>
	<li><code>0 &lt;= val &lt;= 50</code></li>
</ul>


**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Apple](https://leetcode.com/company/apple)

**Related Topics**:  
[Linked List](https://leetcode.com/tag/linked-list/), [Recursion](https://leetcode.com/tag/recursion/)

**Similar Questions**:
* [Remove Element (Easy)](https://leetcode.com/problems/remove-element/)
* [Delete Node in a Linked List (Easy)](https://leetcode.com/problems/delete-node-in-a-linked-list/)

## Solution 0. Using the recursion method

```cpp
// OJ: https://leetcode.com/problems/remove-linked-list-elements/
// Time: O(N)
// Space: O(N)

class Solution 
{
public:
    ListNode* removeElements(ListNode* head, int val) 
    {
        // Base Condition
        if(!head) return NULL;
		
	// Delete the nodes that are on the right of our current node
        head->next = removeElements(head->next, val);
		
	// Omit current node if this has to be deleted or else keep this node 
        return (head->val==val)? head->next:head;
    }
};
```


## Solution 1. Using the 2 pointer's

```cpp
// OJ: https://leetcode.com/problems/remove-linked-list-elements/
// Time: O(N)
// Space: O(1)

class Solution 
{
public:
    ListNode* removeElements(ListNode* head, int val) 
    {
        // Create the dummy node
        ListNode *dummy= new ListNode;
        
        // Assign the dummy next to the head
        dummy->next= head;
        
        // Make the new pointer current for helping
        ListNode *current= dummy;
        
        // Loop till the linked list
        while(current->next)
        {
            // Value matched then delete the connection
            if(current->next->val == val) current->next= current->next->next;
            
            // Else update the current pointer and move ahead
            else current= current->next;
        }
        
        // Finally return the dummy next as required o/p
        return dummy->next;
    }
};
```

## Solution 2. Using the 1 pointer's

```cpp
// OJ: https://leetcode.com/problems/remove-linked-list-elements/
// Time: O(N)
// Space: O(1)

class Solution 
{
public:
    ListNode* removeElements(ListNode* head, int val)
    {
        // Handle the base case
        if(head==nullptr) return head;
	
        // Loop on the linked list and check for the cases
        while(head!=nullptr && head->val==val) head = head->next;
        
        // Make the current as a single pointer
        ListNode* curr = head;
        
        // Loop on the linked list
        while(curr!=nullptr  && curr->next!=nullptr)
        {
            // If case matching
            if(curr->next->val==val) curr->next = curr->next->next;
			
            // Else case matching
            else curr = curr->next;
        }
        
        // Finally return the head
        return head;
    }
};
```

