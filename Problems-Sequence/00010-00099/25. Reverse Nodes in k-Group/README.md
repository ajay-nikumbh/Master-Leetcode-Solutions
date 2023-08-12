# [25. Reverse Nodes in k-Group (Hard)](https://leetcode.com/problems/reverse-nodes-in-k-group/)

<p>Given a linked list, reverse the nodes of a linked list <em>k</em> at a time and return its modified list.</p>

<p><em>k</em> is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of <em>k</em> then left-out nodes, in the end, should remain as it is.</p>

<p>You may&nbsp;not alter the values in the list's nodes, only nodes themselves may be changed.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/03/reverse_ex1.jpg" style="width: 542px; height: 222px;">
<pre><strong>Input:</strong> head = [1,2,3,4,5], k = 2
<strong>Output:</strong> [2,1,4,3,5]
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/03/reverse_ex2.jpg" style="width: 542px; height: 222px;">
<pre><strong>Input:</strong> head = [1,2,3,4,5], k = 3
<strong>Output:</strong> [3,2,1,4,5]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> head = [1,2,3,4,5], k = 1
<strong>Output:</strong> [1,2,3,4,5]
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> head = [1], k = 1
<strong>Output:</strong> [1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the list&nbsp;is in the range <code>sz</code>.</li>
	<li><code>1 &lt;= sz &lt;= 5000</code></li>
	<li><code>0 &lt;= Node.val &lt;= 1000</code></li>
	<li><code>1 &lt;= k &lt;= sz</code></li>
</ul>

<p>&nbsp;</p>
<strong>Follow-up:</strong> Can you solve the problem in O(1) extra memory space?

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Facebook](https://leetcode.com/company/facebook), [Apple](https://leetcode.com/company/apple), [eBay](https://leetcode.com/company/ebay), [Adobe](https://leetcode.com/company/adobe), [Google](https://leetcode.com/company/google), [Walmart Labs](https://leetcode.com/company/walmart-labs)

**Related Topics**:  
[Linked List](https://leetcode.com/tag/linked-list/), [Recursion](https://leetcode.com/tag/recursion/)

**Similar Questions**:
* [Swap Nodes in Pairs (Medium)](https://leetcode.com/problems/swap-nodes-in-pairs/)
* [Swapping Nodes in a Linked List (Medium)](https://leetcode.com/problems/swapping-nodes-in-a-linked-list/)

## Video Notes

![Screenshot from 2022-07-25 08-11-24](https://user-images.githubusercontent.com/37560890/183300478-8e39acfe-b77b-4d6b-838b-fd0ad5d62765.png)
![Screenshot from 2022-07-25 08-12-08](https://user-images.githubusercontent.com/37560890/183300482-b2ef07c3-6c89-4b6a-a19b-0247ca8898aa.png)
![Screenshot from 2022-07-25 08-12-16](https://user-images.githubusercontent.com/37560890/183300485-62793488-4155-4b31-b746-6ede2120b7f4.png)
![Screenshot from 2022-07-25 08-16-09](https://user-images.githubusercontent.com/37560890/183300487-edd81ac8-7106-457d-ba0a-051135e6e69c.png)
![Screenshot from 2022-07-25 08-17-03](https://user-images.githubusercontent.com/37560890/183300488-c4ea5333-8842-4687-88ea-9c27dcea4e80.png)
![Screenshot from 2022-07-25 08-18-09](https://user-images.githubusercontent.com/37560890/183300490-fb4c7185-d6f4-40cd-9abc-24deed55f0c5.png)
![Screenshot from 2022-07-25 08-18-36](https://user-images.githubusercontent.com/37560890/183300491-8b4471e7-619d-45f3-93cd-8b5f57b9ee16.png)
![Screenshot from 2022-07-25 08-19-02](https://user-images.githubusercontent.com/37560890/183300494-8047cb2b-d971-4ea9-8459-c5f2ee70cda3.png)
![Screenshot from 2022-07-25 08-20-27](https://user-images.githubusercontent.com/37560890/183300498-f85faf89-4da0-4143-aff6-d96e439bc19b.png)
![Screenshot from 2022-07-25 08-20-51](https://user-images.githubusercontent.com/37560890/183300501-ace954a4-53c2-4d55-8fd9-d253338508e6.png)
![Screenshot from 2022-07-25 08-21-20](https://user-images.githubusercontent.com/37560890/183300506-31aa8052-aeb2-460d-afab-423e05365647.png)
![Screenshot from 2022-07-25 08-21-22](https://user-images.githubusercontent.com/37560890/183300510-d4e7c9e3-c872-403b-9b5a-268269cc07a5.png)



## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/reverse-nodes-in-k-group/
// Time: O(N)
// Space: O(1)

class Solution 
{
public:
    ListNode* reverseKGroup(ListNode* head, int k) 
    {
        // Edge case
        if(k==1 or head==NULL) return head;
        
        // Create the dummy node
        ListNode *dummy = new ListNode(0);
        
        // Update the dummy next
        dummy->next= head;
        
        // Make the 3 pointers
        ListNode *current= dummy, *net=dummy, *prev= dummy;
        int count=0;
        
        // Count the number of nodes
        while(current->next)
        {
            current= current->next;
            count++;
        }
        
        // Count >= k continue till then
        while(count>= k)
        {
            // Update the current
            current= prev->next;
            net= current->next;
            
            // Do the following operations
            for(int i=1;i<k;i++)
            {
                current->next= net->next;
                net->next= prev->next;
                prev->next= net;
                net= current->next;
            }
            
            // Update the prev
            prev = current;
            count -= k;
        }
        return dummy->next;
    }
};


```

