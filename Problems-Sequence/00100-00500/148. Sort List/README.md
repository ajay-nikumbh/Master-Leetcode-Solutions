# [148. Sort List (Medium)](https://leetcode.com/problems/sort-list/)

<p>Given the <code>head</code> of a linked list, return <em>the list after sorting it in <strong>ascending order</strong></em>.</p>

<p><strong>Follow up:</strong> Can you sort the linked list in <code>O(n logn)</code> time and <code>O(1)</code>&nbsp;memory (i.e. constant space)?</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/14/sort_list_1.jpg" style="width: 450px; height: 194px;">
<pre><strong>Input:</strong> head = [4,2,1,3]
<strong>Output:</strong> [1,2,3,4]
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/14/sort_list_2.jpg" style="width: 550px; height: 184px;">
<pre><strong>Input:</strong> head = [-1,5,3,4,0]
<strong>Output:</strong> [-1,0,3,4,5]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> head = []
<strong>Output:</strong> []
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the list is in the range <code>[0, 5 * 10<sup>4</sup>]</code>.</li>
	<li><code>-10<sup>5</sup> &lt;= Node.val &lt;= 10<sup>5</sup></code></li>
</ul>


**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Adobe](https://leetcode.com/company/adobe), [Yahoo](https://leetcode.com/company/yahoo), [Bloomberg](https://leetcode.com/company/bloomberg), [ByteDance](https://leetcode.com/company/bytedance)

**Related Topics**:  
[Linked List](https://leetcode.com/tag/linked-list/), [Sort](https://leetcode.com/tag/sort/)

**Similar Questions**:
* [Merge Two Sorted Lists (Easy)](https://leetcode.com/problems/merge-two-sorted-lists/)
* [Sort Colors (Medium)](https://leetcode.com/problems/sort-colors/)
* [Insertion Sort List (Medium)](https://leetcode.com/problems/insertion-sort-list/)

## Solution 1. Merge Sort

```cpp
// OJ: https://leetcode.com/problems/sort-list/
// Time: O(NlogN)
// Space: O(logN)

class Solution 
{
public:
    
    ListNode *merge_list(ListNode *left, ListNode *right)
    {
        // Make the new node
        ListNode *ptr= new ListNode(0);
        
        // Make the temp pointer
        ListNode *current = ptr;
        
        // Iterate till l1 and l2 is alive
        while(left and right)
        {
            if(left->val <= right->val)
            {
                current->next= left;
                left= left->next;
            }
            else
            {
                current->next= right;
                right= right->next;
            }
            
            // Update the current next
            current= current->next;
        }
        
        // For the unequal length 
        if(left != NULL)
        {
            // Update the current next
            current -> next = left;
            
            // Move left to the next node
            left = left->next;
        }
        
        if(right != NULL)
        {
            // Update the current next
            current -> next = right;
            
            // Move the right to the next
            right = right ->next;
        }
        
        // Finally return the ptr next
        return ptr->next;
        
    }
    
    ListNode* sortList(ListNode* head) 
    {
        // If the list contains the single node
        if(head==NULL or head->next == NULL) return head;
        
        // Make the 3 pointer's
        ListNode *slow = head, *fast= head, *temp = NULL;
        
        // Find the middle node of the linked list
        while(fast and fast->next)
        {
            // Make the 3 pointer assignment's
            temp= slow;
            slow= slow->next;
            fast= fast->next->next;
        }
        
        // Update the temp ->next
        temp->next= NULL;
        
        // Make the 2 recursive calls
        ListNode *left=  sortList(head);
        ListNode *right= sortList(slow);
        
        // Finally return the merged list
        return merge_list(left,right);
        
    }
};
```
