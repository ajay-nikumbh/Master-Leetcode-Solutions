# [22. Generate Parentheses (Medium)](https://leetcode.com/problems/generate-parentheses/)

<p>
Given <i>n</i> pairs of parentheses, write a function to generate all combinations of well-formed parentheses.
</p>

<p>
For example, given <i>n</i> = 3, a solution set is:
</p>
<pre>[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
</pre>

**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Google](https://leetcode.com/company/google), [Uber](https://leetcode.com/company/uber), [Facebook](https://leetcode.com/company/facebook), [Adobe](https://leetcode.com/company/adobe), [Apple](https://leetcode.com/company/apple), [Yandex](https://leetcode.com/company/yandex)

**Related Topics**:  
[String](https://leetcode.com/tag/string/), [Backtracking](https://leetcode.com/tag/backtracking/)

## Solution 1. DFS

Let's try to generate the valid parentheses.

Starting from empty string, we have two options in each step:

* insert '(' if we still have '(' available
* insert ')' if there are more ')' available than '('

We keep doing this until there is no '(' and ')' available.

```cpp
// OJ: https://leetcode.com/problems/generate-parentheses/
// Time: O(C(N)) where C(N) is the Nth Catalan number
// Space: O(N)

class Solution
{
public:
    
    void helper(vector<string>&ans,int n,int open,int close,string current_string)
    {
        // Hitting the base case
        if(current_string.size() == 2*n)
        {
            // If the size == 2*n that means we got our generated parentheis and push into ans
            ans.push_back(current_string);
            
            // Finally return back from here 
            return;
        }
        
        // Condition for open
        if(open<n) helper(ans,n,open+1,close,current_string+"(");
        
        // Condition for close
        if(close<open) helper(ans,n,open,close+1,current_string+")");
        
    }
    
    vector<string> generateParenthesis(int n) 
    {
        // Create the ans vector
        vector<string> ans;
        
        // Calling the helper method
        helper(ans,n,0,0,"");
        
        // Finally return the ans
        return ans;
    }
};
```
