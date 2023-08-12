# [14. Longest Common Prefix (Easy)](https://leetcode.com/problems/longest-common-prefix/)

<p>Write a function to find the longest common prefix string amongst an array of strings.</p>

<p>If there is no common prefix, return an empty string <code>""</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> strs = ["flower","flow","flight"]
<strong>Output:</strong> "fl"
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> strs = ["dog","racecar","car"]
<strong>Output:</strong> ""
<strong>Explanation:</strong> There is no common prefix among the input strings.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= strs.length &lt;= 200</code></li>
	<li><code>0 &lt;= strs[i].length &lt;= 200</code></li>
	<li><code>strs[i]</code> consists of only lower-case English letters.</li>
</ul>


**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Facebook](https://leetcode.com/company/facebook), [Adobe](https://leetcode.com/company/adobe), [Apple](https://leetcode.com/company/apple), [Snapchat](https://leetcode.com/company/snapchat), [Google](https://leetcode.com/company/google), [Bloomberg](https://leetcode.com/company/bloomberg), [Microsoft](https://leetcode.com/company/microsoft), [Yahoo](https://leetcode.com/company/yahoo), [Uber](https://leetcode.com/company/uber), [Paypal](https://leetcode.com/company/paypal), [Intel](https://leetcode.com/company/intel)

**Related Topics**:  
[String](https://leetcode.com/tag/string/)

## Solution 1. Horizontal Scanning

```cpp
// OJ: https://leetcode.com/problems/longest-common-prefix/
// Time: O(NW)
// Space: O(1)

class Solution
{
public:
    string longestCommonPrefix(vector<string>& s) 
    {
        // Declare the ans var
        int ans= s[0].length();
        
        // Compute the size of the string
        int n= s.size();
        
        // Iterate on the string s
        for(int i=1; i<n ;i++)
        {
            // Declare the j pointer
            int j=0;
            
            // Iterate till the condition satisife's
            while(j<s[i].length() and s[i][j] == s[0][j]) j++;
            
            // Update the ans
            ans= min(ans,j);  
        }
        
        // Finally return the ans 
        return s[0].substr(0,ans);
    }
};

```
