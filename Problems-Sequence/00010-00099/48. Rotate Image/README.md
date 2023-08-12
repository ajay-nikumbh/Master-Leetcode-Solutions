# [48. Rotate Image (Medium)](https://leetcode.com/problems/rotate-image/)

<p>You are given an <em>n</em> x <em>n</em> 2D <code>matrix</code> representing an image, rotate the image by 90 degrees (clockwise).</p>

<p>You have to rotate the image <a href="https://en.wikipedia.org/wiki/In-place_algorithm" target="_blank"><strong>in-place</strong></a>, which means you have to modify the input 2D matrix directly. <strong>DO NOT</strong> allocate another 2D matrix and do the rotation.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/08/28/mat1.jpg" style="width: 642px; height: 242px;">
<pre><strong>Input:</strong> matrix = [[1,2,3],[4,5,6],[7,8,9]]
<strong>Output:</strong> [[7,4,1],[8,5,2],[9,6,3]]
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/08/28/mat2.jpg" style="width: 800px; height: 321px;">
<pre><strong>Input:</strong> matrix = [[5,1,9,11],[2,4,8,10],[13,3,6,7],[15,14,12,16]]
<strong>Output:</strong> [[15,13,2,5],[14,3,4,1],[12,6,8,9],[16,7,10,11]]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> matrix = [[1]]
<strong>Output:</strong> [[1]]
</pre>

<p><strong>Example 4:</strong></p>

<pre><strong>Input:</strong> matrix = [[1,2],[3,4]]
<strong>Output:</strong> [[3,1],[4,2]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>matrix.length == n</code></li>
	<li><code>matrix[i].length == n</code></li>
	<li><code>1 &lt;= n &lt;= 20</code></li>
	<li><code>-1000 &lt;= matrix[i][j] &lt;= 1000</code></li>
</ul>


**Related Topics**:  
[Array](https://leetcode.com/tag/array/)

## Video Notes

![vlcsnap-2022-07-19-08h21m40s471](https://user-images.githubusercontent.com/37560890/179654340-323be059-6fc1-4483-aad2-89705200ff72.png)
![vlcsnap-2022-07-19-08h21m49s645](https://user-images.githubusercontent.com/37560890/179654349-7a01278f-631e-400e-b67e-57ab6c2ee948.png)
![vlcsnap-2022-07-19-08h21m55s193](https://user-images.githubusercontent.com/37560890/179654352-c598f33e-6844-4af3-ba15-eb79f983f209.png)
![vlcsnap-2022-07-19-08h22m23s643](https://user-images.githubusercontent.com/37560890/179654354-443be8f0-8157-4b31-ba57-7e0d7301b3eb.png)
![vlcsnap-2022-07-19-08h22m55s291](https://user-images.githubusercontent.com/37560890/179654356-cd0b8c44-ba50-4352-91c3-e5c604af9d70.png)
![vlcsnap-2022-07-19-08h23m18s426](https://user-images.githubusercontent.com/37560890/179654357-88174f4d-45bc-4665-b05c-9952aad5eb7d.png)
![vlcsnap-2022-07-19-08h23m27s726](https://user-images.githubusercontent.com/37560890/179654359-ab148314-a555-4c8b-b753-3dd26caa6b5b.png)


## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/rotate-image/
// Time: O(N^2)
// Space: O(1)

class Solution 
{
public:
    void rotate(vector<vector<int>>& matrix) 
    {
        // Compute the size of the matrix
        int n =matrix.size();
        
        // Travel through the matrix and trasnpose the matrix
        for(int i=0;i<n;i++)
        {
            for(int j=0;j<i;j++) swap(matrix[i][j] , matrix[j][i] );
        }
        
        // At last just reverse the rows of the matrix
        for(int i=0;i<n;i++) reverse(matrix[i].begin(), matrix[i].end());
    }
};
```
