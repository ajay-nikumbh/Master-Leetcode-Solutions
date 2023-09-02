<h1><a href="https://leetcode.com/problems/excel-sheet-column-title/">168. Excel Sheet Column Title</a></h1><div><p>Given an integer <code>columnNumber</code>, return <em>its corresponding column title as it appears in an Excel sheet</em>.</p>

<p>For example:</p>

<pre>A -&gt; 1
B -&gt; 2
C -&gt; 3
...
Z -&gt; 26
AA -&gt; 27
AB -&gt; 28 
...
</pre>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre><strong>Input:</strong> columnNumber = 1
<strong>Output:</strong> "A"
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre><strong>Input:</strong> columnNumber = 28
<strong>Output:</strong> "AB"
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre><strong>Input:</strong> columnNumber = 701
<strong>Output:</strong> "ZY"
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= columnNumber &lt;= 2<sup>31</sup> - 1</code></li>
</ul>
</div>


## Solution 1. Use the maths formula

```cpp
// OJ: https://leetcode.com/problems/excel-sheet-column-number/
// Tc: O(n)
// Sc: O(1)

class Solution 
{
public:
    string convertToTitle(int n) 
    {
        // Declare the string ans
        string ans;
        
        // Loop till the condition fails
        while(n > 0) 
        {
            // Reduce the n val
            n--;
            
            // Extract the current
            int curr = n % 26;
            
            // Divide the n
            n = n / 26;
            
            // Push the result 
            ans.push_back(curr + 'A');
        }
        
        // Reverse the ans
        reverse(ans.begin(), ans.end());
        
        // Finally return the ans
        return ans;
        
    }
};
```
