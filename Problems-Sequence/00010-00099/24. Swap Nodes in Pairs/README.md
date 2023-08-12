# [24. Swap Nodes in Pairs (Medium)](https://leetcode.com/problems/swap-nodes-in-pairs/)

<p>Given a&nbsp;linked list, swap every two adjacent nodes and return its head. You must solve the problem without&nbsp;modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/03/swap_ex1.jpg" style="width: 422px; height: 222px;">
<pre><strong>Input:</strong> head = [1,2,3,4]
<strong>Output:</strong> [2,1,4,3]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> head = []
<strong>Output:</strong> []
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> head = [1]
<strong>Output:</strong> [1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the&nbsp;list&nbsp;is in the range <code>[0, 100]</code>.</li>
	<li><code>0 &lt;= Node.val &lt;= 100</code></li>
</ul>


**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Bloomberg](https://leetcode.com/company/bloomberg)

**Related Topics**:  
[Linked List](https://leetcode.com/tag/linked-list/), [Recursion](https://leetcode.com/tag/recursion/)

**Similar Questions**:
* [Reverse Nodes in k-Group (Hard)](https://leetcode.com/problems/reverse-nodes-in-k-group/)
* [Swapping Nodes in a Linked List (Medium)](https://leetcode.com/problems/swapping-nodes-in-a-linked-list/)

## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/swap-nodes-in-pairs/
// Time: O(N)
// Space: O(1)

class Solution 
{
public:
    ListNode* swapPairs(ListNode* head) 
    {
        // Make the 3 pointer's for the reverseing of the linked list
        ListNode *current= head;
        ListNode *next= NULL;
        ListNode *prev= NULL;
        
        // Declare the count variable
        int count=0;
        
        // Loop on the linked list and reverse on the first 2 pair's
        while(current and count<2)
        {
            // Update the next node
            next= current->next;
            
            // Update the current next node
            current->next= prev;
            
            // Update the prev
            prev= current;
            
            // Update the current
            current=next;
            
            // Incr the count
            count++;
        }
        
        // After reversing the 2 pair's rest of the work will be done by recursion
        if(next != NULL) head->next= swapPairs(next);
        
        // Return the prev
        return prev;
    }
};
```
