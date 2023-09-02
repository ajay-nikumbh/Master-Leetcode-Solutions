# [242. Valid Anagram (Easy)](https://leetcode.com/problems/valid-anagram/)

<p>Given two strings <em>s</em> and <em>t&nbsp;</em>, write a function to determine if <em>t</em> is an anagram of <em>s</em>.</p>

<p><b>Example 1:</b></p>

<pre><b>Input:</b> <em>s</em> = "anagram", <em>t</em> = "nagaram"
<b>Output:</b> true
</pre>

<p><b>Example 2:</b></p>

<pre><b>Input:</b> <em>s</em> = "rat", <em>t</em> = "car"
<b>Output: </b>false
</pre>

<p><strong>Note:</strong><br>
You may assume the string contains only lowercase alphabets.</p>

<p><strong>Follow up:</strong><br>
What if the inputs contain unicode characters? How would you adapt your solution to such case?</p>


**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [Sort](https://leetcode.com/tag/sort/)

**Similar Questions**:
* [Group Anagrams (Medium)](https://leetcode.com/problems/group-anagrams/)
* [Palindrome Permutation (Easy)](https://leetcode.com/problems/palindrome-permutation/)
* [Find All Anagrams in a String (Medium)](https://leetcode.com/problems/find-all-anagrams-in-a-string/)
![image](https://user-images.githubusercontent.com/37560890/189510386-6d615238-8928-4ce4-b514-4453f1ca4a3c.png)

## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/valid-anagram/
// Time: O(N)
// Space: O(C)

class Solution 
{
public:
    bool isAnagram(string s, string t) 
    {   
        // Check the edge case
        if(s.length() != t.length()) return false;
        
        // Make the frequency array
        int frequency[26] = {0};
        
        // Iterate on the for loop 
        for(int i=0;i<s.length() ;i++)
        {
            frequency[s[i] - 'a']++;
            frequency[t[i] - 'a']--;
        }
        
        // Check if any of 26 ccharacters is true in the hashmap then return false else true
        for(auto i=0;i<26;i++) if(frequency[i]) return false;
        
        // Finally return false
        return true;
    }
};


```
