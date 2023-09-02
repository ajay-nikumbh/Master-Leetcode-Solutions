# [147. Insertion Sort List (Medium)](https://leetcode.com/problems/insertion-sort-list/)

<p>Given the <code>head</code> of a singly linked list, sort the list using <strong>insertion sort</strong>, and return <em>the sorted list's head</em>.</p>

<p>The steps of the <strong>insertion sort</strong> algorithm:</p>

<ol>
	<li>Insertion sort iterates, consuming one input element each repetition and growing a sorted output list.</li>
	<li>At each iteration, insertion sort removes one element from the input data, finds the location it belongs within the sorted list and inserts it there.</li>
	<li>It repeats until no input elements remain.</li>
</ol>

<p>The following is a graphical example of the insertion sort algorithm. The partially sorted list (black) initially contains only the first element in the list. One element (red) is removed from the input data and inserted in-place into the sorted list with each iteration.</p>
<img alt="" src="https://upload.wikimedia.org/wikipedia/commons/0/0f/Insertion-sort-example-300px.gif" style="height:180px; width:300px">
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/04/sort1linked-list.jpg" style="width: 422px; height: 222px;">
<pre><strong>Input:</strong> head = [4,2,1,3]
<strong>Output:</strong> [1,2,3,4]
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/04/sort2linked-list.jpg" style="width: 542px; height: 222px;">
<pre><strong>Input:</strong> head = [-1,5,3,4,0]
<strong>Output:</strong> [-1,0,3,4,5]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the list is in the range <code>[1, 5000]</code>.</li>
	<li><code>-5000 &lt;= Node.val &lt;= 5000</code></li>
</ul>


**Companies**:  
[Apple](https://leetcode.com/company/apple)

**Related Topics**:  
[Linked List](https://leetcode.com/tag/linked-list/), [Sorting](https://leetcode.com/tag/sorting/)

**Similar Questions**:
* [Sort List (Medium)](https://leetcode.com/problems/sort-list/)
* [Insert into a Sorted Circular Linked List (Medium)](https://leetcode.com/problems/insert-into-a-sorted-circular-linked-list/)

## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/insertion-sort-list/
// Time: O(N^2)
// Space: O(1)

class Solution 
{
public:
    ListNode* insertionSortList(ListNode* head) 
    {
        // Create the dummy node
        ListNode * dummy = new ListNode(INT_MIN, head);
        
        // Make the current pointer to point it to the head
        ListNode *current= head;
        
        // Itereatee on the 
        while(current->next)
        {
            // If all values in seq then keep moving forward
            if(current->next->val > current->val) current= current->next;
            
            // Else case
            else
            {
                // Declare the 2 variable's
                ListNode *j= dummy;
                ListNode *current_next_next = current->next->next;
                
                // Check if the smaller val is coming from the unsorted region
                while(j->next->val < current->next->val) j= j->next;
                
                // Update the currnet next next
                current->next->next= j->next;
                
                // Update j next
                j->next= current->next;
                
                // Update current next
                current->next= current_next_next;
            }
        }
        
        // Finally return dummy next
        return dummy ->next;
    }
};
```
