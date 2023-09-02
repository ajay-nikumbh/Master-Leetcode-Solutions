# [234. Palindrome Linked List (Easy)](https://leetcode.com/problems/palindrome-linked-list/)

<p>Given a singly linked list, determine if it is a palindrome.</p>

<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> 1-&gt;2
<strong>Output:</strong> false</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> 1-&gt;2-&gt;2-&gt;1
<strong>Output:</strong> true</pre>

<p><b>Follow up:</b><br>
Could you do it in O(n) time and O(1) space?</p>


**Companies**:  
[IXL](https://leetcode.com/company/ixl), [Microsoft](https://leetcode.com/company/microsoft), [Google](https://leetcode.com/company/google)

**Related Topics**:  
[Linked List](https://leetcode.com/tag/linked-list/), [Two Pointers](https://leetcode.com/tag/two-pointers/)

**Similar Questions**:
* [Palindrome Number (Easy)](https://leetcode.com/problems/palindrome-number/)
* [Valid Palindrome (Easy)](https://leetcode.com/problems/valid-palindrome/)
* [Reverse Linked List (Easy)](https://leetcode.com/problems/reverse-linked-list/)

## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/palindrome-linked-list/
// Time: O(N)
// Space: O(1)

class Solution 
{
public:
    
    // Method for the reversing the linked list
    ListNode *reverse(ListNode *head)
    {
        // Make the 2 pointers
        ListNode *prev= NULL;
        ListNode *next= NULL;
        
        // Iterate till head is alive
        while(head)
        {
            // Update pointer's
            next= head->next;
            head->next= prev;
            prev= head;
            head= next;
            
        }
        
        // Finally return the prev
        return prev;
    }
    
    
    bool isPalindrome(ListNode* head) 
    {
        // Edge case
        if(head== NULL or head->next== NULL) return 1;
        
        // Make the 2 pointers
        ListNode *slow= head;
        ListNode *fast = head;
        
        // Find the middle of the linked list
        while(fast->next and fast->next->next)
        {
            slow = slow->next;
            fast= fast->next->next;
        }
        
        // Reverse the linked list from the middle
        slow->next= reverse(slow->next);
        
        // Move the slow to the slow->next 
        // Basically to the first pos of the right half
        slow= slow->next;
        
        // Iterate till slow alive
        while(slow)
        {
            if(head->val != slow->val) return false;
            head= head->next;
            slow = slow->next;
            
        }
        
        // Finally return 1 if all cases satisify
        return 1; 
    }
};
```
