# [125. Valid Palindrome (Easy)](https://leetcode.com/problems/valid-palindrome/)

<p>Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.</p>

<p><strong>Note:</strong>&nbsp;For the purpose of this problem, we define empty string as valid palindrome.</p>

<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> "A man, a plan, a canal: Panama"
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> "race a car"
<strong>Output:</strong> false
</pre>


**Companies**:  
[Facebook](https://leetcode.com/company/facebook), [Microsoft](https://leetcode.com/company/microsoft), [Apple](https://leetcode.com/company/apple)

**Related Topics**:  
[Two Pointers](https://leetcode.com/tag/two-pointers/), [String](https://leetcode.com/tag/string/)

**Similar Questions**:
* [Palindrome Linked List (Easy)](https://leetcode.com/problems/palindrome-linked-list/)
* [Valid Palindrome II (Easy)](https://leetcode.com/problems/valid-palindrome-ii/)

## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/valid-palindrome/
// Time: O(N)
// Space: O(1)

class Solution
{
public:
    bool isPalindrome(string s) 
    {
        // Declare the 2 pointers
        int i=0, j=s.size();
        
        // Loop till i<j
        while(i<j)
        {
            // By pass alphanumeric chars from starting
            while(i<j and !isalnum(s[i])) ++i;
            
            // By pass alphanumeric chars from backend
            while(i<j and !isalnum(s[j])) --j;
            
            // Now after bypassing check if the string is equal or not
            if(i<j and tolower(s[i++]) !=  tolower(s[j--])) return false;
        }
        return true;
    }
};
```
