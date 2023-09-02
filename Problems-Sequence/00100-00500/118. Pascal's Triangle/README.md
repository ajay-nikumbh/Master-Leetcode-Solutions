# [118. Pascal's Triangle (Easy)](https://leetcode.com/problems/pascals-triangle/)

<p>Given a non-negative integer&nbsp;<em>numRows</em>, generate the first <em>numRows</em> of Pascal's triangle.</p>

<p><img alt="" src="https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif" style="height:240px; width:260px"><br>
<small>In Pascal's triangle, each number is the sum of the two numbers directly above it.</small></p>

<p><strong>Example:</strong></p>

<pre><strong>Input:</strong> 5
<strong>Output:</strong>
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
</pre>


**Companies**:  
[Bloomberg](https://leetcode.com/company/bloomberg), [Google](https://leetcode.com/company/google), [Facebook](https://leetcode.com/company/facebook)

## Video Notes

![vlcsnap-2022-07-18-08h11m58s856](https://user-images.githubusercontent.com/37560890/179438615-04265ba0-41da-4d11-bc9e-bbe88878c730.png)
![vlcsnap-2022-07-18-08h12m04s883](https://user-images.githubusercontent.com/37560890/179438617-1070290b-c6b7-441f-8e25-795e8857e086.png)
![vlcsnap-2022-07-18-08h14m30s093](https://user-images.githubusercontent.com/37560890/179438618-1fd3df72-3a8d-4008-9cf5-6faae17004be.png)
![vlcsnap-2022-07-18-08h15m02s765](https://user-images.githubusercontent.com/37560890/179438623-68622ffb-ca9d-45d6-a231-3bdfb57efd7f.png)
![vlcsnap-2022-07-18-08h15m30s055](https://user-images.githubusercontent.com/37560890/179438627-be8199dd-b573-42d4-b354-553d6123c535.png)
![vlcsnap-2022-07-18-08h16m20s578](https://user-images.githubusercontent.com/37560890/179438628-080bd1c9-f3d5-4bef-b285-d7f1bd931b16.png)
![vlcsnap-2022-07-18-08h16m57s370](https://user-images.githubusercontent.com/37560890/179438630-10fa98be-65e9-48e7-9105-a618b2ca59b8.png)
![vlcsnap-2022-07-18-08h17m06s000](https://user-images.githubusercontent.com/37560890/179438632-8bfc4368-a78e-4f85-a77e-42d5d35cec90.png)
![vlcsnap-2022-07-18-08h17m48s030](https://user-images.githubusercontent.com/37560890/179438634-121a12aa-99d8-4b51-ad3e-c724d826e908.png)



## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/pascals-triangle/
// Time: O(N^2)
// Space: O(1)

class Solution 
{
public:
    vector<vector<int>> generate(int numRows) 
    {
        // Declare the 2d vector
        vector<vector<int>> r(numRows);
        
        // Iterate over the numRows
        for (int i = 0; i < numRows; ++i) 
        {
            // Resize it
            r[i].resize(i+1);
            
            // Make the first row and last col as 1
            r[i][0] = r[i][i]=1;
            
            // Now compute the sum
            for (int j = 1; j < i; ++j) ans[i][j] = ans[i - 1][j - 1] + ans[i - 1][j];
        }
        
        // Finally return the r
        return r;
    }
};
```
