# [21. Merge Two Sorted Lists (Easy)](https://leetcode.com/problems/merge-two-sorted-lists/)

<p>Merge two sorted linked lists and return it as a <strong>sorted</strong> list. The list should be made by splicing together the nodes of the first two lists.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/03/merge_ex1.jpg" style="width: 662px; height: 302px;">
<pre><strong>Input:</strong> l1 = [1,2,4], l2 = [1,3,4]
<strong>Output:</strong> [1,1,2,3,4,4]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> l1 = [], l2 = []
<strong>Output:</strong> []
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> l1 = [], l2 = [0]
<strong>Output:</strong> [0]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in both lists is in the range <code>[0, 50]</code>.</li>
	<li><code>-100 &lt;= Node.val &lt;= 100</code></li>
	<li>Both <code>l1</code> and <code>l2</code> are sorted in <strong>non-decreasing</strong> order.</li>
</ul>


**Related Topics**:  
[Linked List](https://leetcode.com/tag/linked-list/), [Recursion](https://leetcode.com/tag/recursion/)

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Facebook](https://leetcode.com/company/facebook), [Google](https://leetcode.com/company/google), [Adobe](https://leetcode.com/company/adobe), [Apple](https://leetcode.com/company/apple), [Bloomberg](https://leetcode.com/company/bloomberg), [Yahoo](https://leetcode.com/company/yahoo), [Arista Networks](https://leetcode.com/company/arista-networks), [Uber](https://leetcode.com/company/uber), [Indeed](https://leetcode.com/company/indeed), [Cisco](https://leetcode.com/company/cisco), [Tencent](https://leetcode.com/company/tencent), [Airbnb](https://leetcode.com/company/airbnb), [Oracle](https://leetcode.com/company/oracle), [IBM](https://leetcode.com/company/ibm), [Huawei](https://leetcode.com/company/huawei), [Paypal](https://leetcode.com/company/paypal), [Yandex](https://leetcode.com/company/yandex)

**Similar Questions**:
* [Merge k Sorted Lists (Hard)](https://leetcode.com/problems/merge-k-sorted-lists/)
* [Merge Sorted Array (Easy)](https://leetcode.com/problems/merge-sorted-array/)
* [Sort List (Medium)](https://leetcode.com/problems/sort-list/)
* [Shortest Word Distance II (Medium)](https://leetcode.com/problems/shortest-word-distance-ii/)
* [Add Two Polynomials Represented as Linked Lists (Medium)](https://leetcode.com/problems/add-two-polynomials-represented-as-linked-lists/)

## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/merge-two-sorted-lists/
// Time: O(A + B)
// Space: O(1)

class Solution 
{
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) 
    {
        // Edge cases
        // First linked list is empty return l2
        if(!l1) return l2;
        
        // Second linked list is empty return l1
        if(!l2) return l1;
        
        // If the l1 val > l2 val then swap l1 and l2
        if(l1->val > l2->val) std::swap(l1,l2);
        
        // Make a pointer points to the l1
        // Basically remebered the head of the merged sorted list
        ListNode *res= l1;
        
        // Iterate till l1 and l2 are alive
        while(l1 and l2 )
        {
            // Assign the temp =NULL for every iteration
            ListNode *temp = NULL;
            
            // Iterate till this conditon never fails
            while(l1 and l1->val <= l2->val)
            {
                temp = l1;
                l1= l1->next;
            }
            
            // Once you come out then assign temp next to l2
            temp->next = l2;
            
            // Swap the 2 pointers
            std::swap(l1,l2); 
        }
        return res;
    }
};
```
