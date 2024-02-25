# [2. Add Two Numbers (Medium)](https://leetcode.com/problems/add-two-numbers/)

<p>You are given two <strong>non-empty</strong> linked lists representing two non-negative integers. The digits are stored in <strong>reverse order</strong>, and each of their nodes contains a single digit. Add the two numbers and return the sum&nbsp;as a linked list.</p>

<p>You may assume the two numbers do not contain any leading zero, except the number 0 itself.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/02/addtwonumber1.jpg" style="width: 483px; height: 342px;">
<pre><strong>Input:</strong> l1 = [2,4,3], l2 = [5,6,4]
<strong>Output:</strong> [7,0,8]
<strong>Explanation:</strong> 342 + 465 = 807.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> l1 = [0], l2 = [0]
<strong>Output:</strong> [0]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
<strong>Output:</strong> [8,9,9,9,0,0,0,1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in each linked list is in the range <code>[1, 100]</code>.</li>
	<li><code>0 &lt;= Node.val &lt;= 9</code></li>
	<li>It is guaranteed that the list represents a number that does not have leading zeros.</li>
</ul>


**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Facebook](https://leetcode.com/company/facebook), [Bloomberg](https://leetcode.com/company/bloomberg), [Adobe](https://leetcode.com/company/adobe), [Apple](https://leetcode.com/company/apple), [Google](https://leetcode.com/company/google), [Yahoo](https://leetcode.com/company/yahoo), [Uber](https://leetcode.com/company/uber), [Capital One](https://leetcode.com/company/capital-one), [JPMorgan](https://leetcode.com/company/jpmorgan), [Huawei](https://leetcode.com/company/huawei)

**Related Topics**:  
[Linked List](https://leetcode.com/tag/linked-list/), [Math](https://leetcode.com/tag/math/), [Recursion](https://leetcode.com/tag/recursion/)

**Similar Questions**:
* [Multiply Strings (Medium)](https://leetcode.com/problems/multiply-strings/)
* [Add Binary (Easy)](https://leetcode.com/problems/add-binary/)
* [Sum of Two Integers (Medium)](https://leetcode.com/problems/sum-of-two-integers/)
* [Add Strings (Easy)](https://leetcode.com/problems/add-strings/)
* [Add Two Numbers II (Medium)](https://leetcode.com/problems/add-two-numbers-ii/)
* [Add to Array-Form of Integer (Easy)](https://leetcode.com/problems/add-to-array-form-of-integer/)
* [Add Two Polynomials Represented as Linked Lists (Medium)](https://leetcode.com/problems/add-two-polynomials-represented-as-linked-lists/)

## Video Notes

![Screenshot from 2022-07-21 07-54-03](https://user-images.githubusercontent.com/37560890/180349447-69325349-5522-4d9a-9eaf-88136ce7ac5e.png)
![Screenshot from 2022-07-21 07-54-27](https://user-images.githubusercontent.com/37560890/180349448-3d392990-bfab-4290-94c5-7e7bbce1524a.png)
![Screenshot from 2022-07-21 07-54-36](https://user-images.githubusercontent.com/37560890/180349449-9e986258-e03a-4f2a-b45f-d55b72528ffc.png)
![Screenshot from 2022-07-21 07-56-29](https://user-images.githubusercontent.com/37560890/180349450-925226d3-09cb-4955-ae5d-c6d4b011afcd.png)
![Screenshot from 2022-07-21 07-57-10](https://user-images.githubusercontent.com/37560890/180349451-805f1a1a-093b-4fab-9b26-992999a98746.png)
![Screenshot from 2022-07-21 07-57-52](https://user-images.githubusercontent.com/37560890/180349453-fa33f805-9511-4af7-9453-a0c31291e3fc.png)
![Screenshot from 2022-07-21 07-57-59](https://user-images.githubusercontent.com/37560890/180349454-7d84b269-4b2a-4d8c-813b-33a02f2b4f57.png)
![Screenshot from 2022-07-21 07-58-20](https://user-images.githubusercontent.com/37560890/180349459-987b7307-b10f-4ec1-8230-429f1c52c4c7.png)
![Screenshot from 2022-07-21 07-58-29](https://user-images.githubusercontent.com/37560890/180349460-5ee01399-d19f-4cc6-8871-d5a45e530232.png)

## My personal notes

```cpp
Algorithm

1. Create the dummy node.
2. Declare the temp pointer and point it to the dummy node.
3. Declare the carray and assign it to the 0.
4. While loop till l1 || l2 || carry is active
	.Declare the sum =0
	.If the l1 is alive
		.Update the sum+l1->val.
		.Move the l1 to the next node.
	.If the l2 is alive
		.Update the sum+l2->val.
		.Move the l2 to the next node.
	.Final sum will be sum= sum + carry.
	.Compute the carry = sum/10.
	.Make the new node and push sum%10 since we need only 1 value.
	.Make the temp next to the newly created node.
	.Update the temp of next.
5. Return the dummy next.

```


## Solution 1 - Python

```py
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:

    # Define the method
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        
        # Create the dummy node
        dummy = ListNode(0)
        
        # Point the current node to the dummy node
        curr = dummy

        # Initialize the carry to 0
        carry = 0
        
        # Loop till the l1 or l2 or carry is 1
        while l1 or l2 or  carry == 1: 
            
            # Define the variable for the sum_compute
            sum_compute = 0
            
            # If the l1 is active then
            if l1:
                
                # Update the sum_compute 
                sum_compute += l1.val
                
                # Move the l1 to the next node
                l1 = l1.next
            
            # If the l2 is active then 
            if l2:
                
                # Update the sum_compute
                sum_compute += l2.val

                # Move the l2 to the next node
                l2 = l2.next
            
            
            # Add the carry to the sum_compute
            sum_compute += carry
            
            # Update the carry
            carry = sum_compute//10
            
            # Make the new node 
            node = ListNode(sum_compute % 10)
            
            # Attach the new node to the current next
            curr.next = node
            
            # Update the current next
            curr = curr.next
        
        # Return the dummy next
        return dummy.next
```

## Solution 1 - C++

```cpp
// OJ: https://leetcode.com/problems/add-two-numbers/
// Time: O(max(l1,l2))
// Space: O(n)

class Solution 
{
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) 
    {
        // Create the dummy node
        ListNode *dummy = new ListNode();
        
        // Assign the temp to the dummy node
        ListNode *temp= dummy;
        
        // Make the val of carry as 0
        int carry=0;
        
        // Traverse till l1 or l2 or carry is alive
        while(l1 != NULL or l2  or carry)
        {
            // Make the sum to 0
            int sum=0;
            
            // If l1 is alive
            if(l1)
            {
                // Add sum to l1 of value
                sum = sum + l1->val;
                
                // Update the l1 to the next node
                l1= l1->next;
            }
            
            // If the l2 is alive
            if(l2)
            {
                // Add sum to the l1 of value
                sum = sum+l2->val;
                
                // Update l2 to the next node
                l2= l2->next;
            }
            
            // Final sum will be sum= sum + carry
            sum = sum + carry;
            
            // Compute the carry
            carry = sum /10;
            
            // Make the new node and push sum%10 since we need only 1 value 
            ListNode *node= new ListNode(sum %10);
            
            // Make the temp next to the newly created node
            temp->next= node;
            
            // Update the temp of next
            temp = temp->next;
        }
        
        return dummy->next;
    }
};
```
