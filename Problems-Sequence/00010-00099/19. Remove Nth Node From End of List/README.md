# [19. Remove Nth Node From End of List (Medium)](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

<p>Given the <code>head</code> of a linked list, remove the <code>n<sup>th</sup></code> node from the end of the list and return its head.</p>

<p><strong>Follow up:</strong>&nbsp;Could you do this in one pass?</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/03/remove_ex1.jpg" style="width: 542px; height: 222px;">
<pre><strong>Input:</strong> head = [1,2,3,4,5], n = 2
<strong>Output:</strong> [1,2,3,5]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> head = [1], n = 1
<strong>Output:</strong> []
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> head = [1,2], n = 1
<strong>Output:</strong> [1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the list is <code>sz</code>.</li>
	<li><code>1 &lt;= sz &lt;= 30</code></li>
	<li><code>0 &lt;= Node.val &lt;= 100</code></li>
	<li><code>1 &lt;= n &lt;= sz</code></li>
</ul>


**Related Topics**:  
[Linked List](https://leetcode.com/tag/linked-list/), [Two Pointers](https://leetcode.com/tag/two-pointers/)

**Similar Questions**:
* [Swapping Nodes in a Linked List (Medium)](https://leetcode.com/problems/swapping-nodes-in-a-linked-list/)
* [Delete N Nodes After M Nodes of a Linked List (Easy)](https://leetcode.com/problems/delete-n-nodes-after-m-nodes-of-a-linked-list/)

## Video Notes

![Screenshot from 2022-07-21 07-40-13](https://user-images.githubusercontent.com/37560890/180349234-5d3d9eaa-739c-469c-892f-d261326f6bda.png)
![Screenshot from 2022-07-21 07-40-53](https://user-images.githubusercontent.com/37560890/180349241-a9b11bef-e237-41c1-9f5b-57131606ee64.png)
![Screenshot from 2022-07-21 07-41-31](https://user-images.githubusercontent.com/37560890/180349244-8be996ff-407a-4cbb-8365-3a8f85c92f13.png)
![Screenshot from 2022-07-21 07-41-40](https://user-images.githubusercontent.com/37560890/180349246-cef37ee3-d9b0-47c7-83c8-ff63a20e0d91.png)
![Screenshot from 2022-07-21 07-41-42](https://user-images.githubusercontent.com/37560890/180349249-8489db4d-23e5-4a5a-9f0d-999b1c833f1b.png)
![Screenshot from 2022-07-21 07-41-59](https://user-images.githubusercontent.com/37560890/180349251-2952f698-df1a-4bc2-b6cf-804c221e7de6.png)
![Screenshot from 2022-07-21 07-42-10](https://user-images.githubusercontent.com/37560890/180349253-6dd5c675-f697-470a-aea0-91b5fdb2d506.png)
![Screenshot from 2022-07-21 07-42-24](https://user-images.githubusercontent.com/37560890/180349254-ec4728d9-7336-4c2c-b02a-e777bf459f94.png)
![Screenshot from 2022-07-21 07-43-17](https://user-images.githubusercontent.com/37560890/180349255-41ba4483-09ed-4b95-b3c8-aaa55ef380ab.png)
![Screenshot from 2022-07-21 07-43-22](https://user-images.githubusercontent.com/37560890/180349258-888f5e67-d752-48be-8d03-88ee56d11d08.png)
![Screenshot from 2022-07-21 07-43-34](https://user-images.githubusercontent.com/37560890/180349260-5915f082-1cc1-4243-afae-2c1242914412.png)
![Screenshot from 2022-07-21 07-44-11](https://user-images.githubusercontent.com/37560890/180349262-269162d3-3de5-4944-9a0e-b1033c4e501a.png)
![Screenshot from 2022-07-21 07-44-29](https://user-images.githubusercontent.com/37560890/180349266-c596fe18-c2c9-4763-adad-a2d1379c074f.png)
![Screenshot from 2022-07-21 07-44-41](https://user-images.githubusercontent.com/37560890/180349270-9c5fb848-38c6-4ca7-9043-497eddfda76c.png)


## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/remove-nth-node-from-end-of-list/
// Time: O(N)
// Space: O(1)

class Solution 
{
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) 
    {
        // Make a new dummy node
        ListNode *start = new ListNode();
        
        // Point that dummy node to the head
        start->next = head;
        
        // Make 2 pointers fast and slow
        ListNode *fast= start;
        ListNode *slow = start;
        
        // Move the fast till the given n
        for(int i=1;i<=n;i++)
        {
            fast= fast->next;
        }
        
        // Iterate till the fast next is not null
        while(fast->next != NULL)
        {
            // Move the fast and slow by 1 position
            fast= fast->next;
            slow= slow->next;
        }
        
        // Make the slow next point to the slow next of next
        slow->next= slow->next->next;
        
        // Finally return the slow next this is basically the edge case 
        return start->next;
    }
};

```
