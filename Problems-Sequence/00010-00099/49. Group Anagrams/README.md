# [49. Group Anagrams (Medium)](https://leetcode.com/problems/group-anagrams/)

<p>Given an array of strings <code>strs</code>, group <strong>the anagrams</strong> together. You can return the answer in <strong>any order</strong>.</p>

<p>An <strong>Anagram</strong> is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> strs = ["eat","tea","tan","ate","nat","bat"]
<strong>Output:</strong> [["bat"],["nat","tan"],["ate","eat","tea"]]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> strs = [""]
<strong>Output:</strong> [[""]]
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> strs = ["a"]
<strong>Output:</strong> [["a"]]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= strs.length &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= strs[i].length &lt;= 100</code></li>
	<li><code>strs[i]</code> consists of lower-case English letters.</li>
</ul>


**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Microsoft](https://leetcode.com/company/microsoft), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [eBay](https://leetcode.com/company/ebay), [Apple](https://leetcode.com/company/apple), [BlackRock](https://leetcode.com/company/blackrock), [Facebook](https://leetcode.com/company/facebook), [Paypal](https://leetcode.com/company/paypal), [Uber](https://leetcode.com/company/uber), [Yandex](https://leetcode.com/company/yandex), [Salesforce](https://leetcode.com/company/salesforce), [Walmart Labs](https://leetcode.com/company/walmart-labs), [Twilio](https://leetcode.com/company/twilio), [Two Sigma](https://leetcode.com/company/two-sigma), [Google](https://leetcode.com/company/google), [VMware](https://leetcode.com/company/vmware), [Snapchat](https://leetcode.com/company/snapchat), [Splunk](https://leetcode.com/company/splunk), [Atlassian](https://leetcode.com/company/atlassian), [Citadel](https://leetcode.com/company/citadel)

**Related Topics**:  
[Hash Table](https://leetcode.com/tag/hash-table/), [String](https://leetcode.com/tag/string/), [Sorting](https://leetcode.com/tag/sorting/)

**Similar Questions**:
* [Valid Anagram (Easy)](https://leetcode.com/problems/valid-anagram/)
* [Group Shifted Strings (Medium)](https://leetcode.com/problems/group-shifted-strings/)

### Video Notes

![Screenshot from 2022-09-11 09-11-14](https://user-images.githubusercontent.com/37560890/189511869-2cd1abec-e8f8-4c01-973a-f5eb69ba6f4d.png)
![Screenshot from 2022-09-11 09-12-18](https://user-images.githubusercontent.com/37560890/189511871-ab093089-ccc5-4fb2-8b71-af66ac7b66c8.png)
![Screenshot from 2022-09-11 09-12-42](https://user-images.githubusercontent.com/37560890/189511874-e11c494d-3f90-4043-be31-f174fa15720b.png)
![Screenshot from 2022-09-11 09-13-15](https://user-images.githubusercontent.com/37560890/189511876-b219c940-eade-4f67-8ed0-77726d94cdfa.png)
![Screenshot from 2022-09-11 09-13-29](https://user-images.githubusercontent.com/37560890/189511880-9d34d5e9-3cd4-4711-8fc8-31f362d56178.png)
![Screenshot from 2022-09-11 09-15-20](https://user-images.githubusercontent.com/37560890/189511886-a2199958-88ba-4e2c-876f-f3a50424d629.png)
![Screenshot from 2022-09-11 09-16-02](https://user-images.githubusercontent.com/37560890/189511887-d8b28e8a-a5ab-4dd4-994f-67690e412b14.png)
![Screenshot from 2022-09-11 09-29-42](https://user-images.githubusercontent.com/37560890/189511889-4d9954c2-dfc1-431a-b25a-0f100023f2a6.png)
![Screenshot from 2022-09-11 09-30-35](https://user-images.githubusercontent.com/37560890/189511890-53b48a11-ebb2-412e-a80f-da49e19d9adc.png)
![Screenshot from 2022-09-11 09-31-08](https://user-images.githubusercontent.com/37560890/189511892-5ac6a081-5d64-4e6f-a103-04cef1da1921.png)
![Screenshot from 2022-09-11 09-31-23](https://user-images.githubusercontent.com/37560890/189511894-1d571bc2-1c43-4443-95e7-3af77ed209f8.png)


## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/group-anagrams/
// Time: O(NWlogW)
// Space: O(NW)


class Solution 
{
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) 
    {
        // C++ ffast i/o operations
        ios_base::sync_with_stdio(false);
        cin.tie(NULL);
        
        // Create an unordered map
        unordered_map<string, vector<string>> mp;
        
        // Compute the size
        int n= strs.size();
        string temp;
        
        // Iterate on the strs
        for(int i=0;i<n;i++)
        {
            // Extract the first word 
            temp = strs[i];
            
            // Sort the first word
            sort(strs[i].begin(), strs[i].end());
            
            // Push into the hashmap
            mp[strs[i]].push_back(temp);
            
        }
        
        // Make the new vector
        vector<vector<string>> result;
        
        // Push the final computed buckets into the reesult vector
        for(auto it= mp.begin() ; it != mp.end() ; it++) result.push_back(it->second);
            
        // Finally return the result
        return result;
            
    }
};
```

or

```cpp

class Solution 
{
public:
    vector<vector<string>> groupAnagrams(vector<string>& A) 
    {
    	// Decalre the map
    	unordered_map<string, vector<string>> m;
        
	// Iterate on the nums
	for (auto &s : A) 
	{
	    // Extract the key
            auto key = s;
	    
	    // Sort the string 
            sort(begin(key), end(key));
	    
	    // Put into the map 
            m[key].push_back(s);
        }
	
	// Decalre the ans vector
        vector<vector<string>> ans;
	
	// Push into the result the precomputed buckets
        for (auto &[key, strs] : m) ans.push_back(strs);
        
	// Finally return the ans
	return ans;
    }
};
```

or

```cpp

class Solution 
{
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) 
    {
        // C++ ffast i/o operations
        ios_base::sync_with_stdio(false);
        cin.tie(NULL);
        
        // Create an map
        map<map<char,int>, vector<string>> mp;
        
        // Decalre the itr 
        int i=0;
        
        // Compute the size of the string array
        int n = strs.size();
        
        // Iterate till the size of n
        while(i<n)
        {
            // Decalre the map
            map<char,int> helper_map;
            
            // Compute the freq of each char
            for(int j= 0; j<strs[i].size();j++) helper_map[strs[i][j]]++;
            
            // Push the helper map into the orignal map
            mp[helper_map].push_back(strs[i]);
            
            // Incr itr
            i++;
        }
        
        // Make the new vector
        vector<vector<string>> result;
        
        // Push the final computed buckets into the reesult vector
        for(auto it= mp.begin() ; it != mp.end() ; it++) result.push_back(it->second);
            
        // Finally return the result
        return result;
            
    }
};
```
