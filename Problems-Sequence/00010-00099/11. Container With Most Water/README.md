# [11. Container With Most Water (Medium)](https://leetcode.com/problems/container-with-most-water/)

<p>Given <i>n</i> non-negative integers <i>a<sub>1</sub></i>, <i>a<sub>2</sub></i>, ..., <i>a<sub>n&nbsp;</sub></i>, where each represents a point at coordinate (<i>i</i>, <i>a<sub>i</sub></i>). <i>n</i> vertical lines are drawn such that the two endpoints of line <i>i</i> is at (<i>i</i>, <i>a<sub>i</sub></i>) and (<i>i</i>, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.</p>

<p><strong>Note:&nbsp;</strong>You may not slant the container and <i>n</i> is at least 2.</p>

<p>&nbsp;</p>

<p><img alt="" src="https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question_11.jpg" style="width: 600px; height: 287px;"></p>

<p><small>The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain&nbsp;is 49. </small></p>

<p>&nbsp;</p>

<p><strong>Example:</strong></p>

<pre><strong>Input:</strong> [1,8,6,2,5,4,8,3,7]
<strong>Output:</strong> 49</pre>

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Two Pointers](https://leetcode.com/tag/two-pointers/)

**Similar Questions**:
* [Trapping Rain Water (Hard)](https://leetcode.com/problems/trapping-rain-water/)

![image](https://user-images.githubusercontent.com/37560890/189956895-fe94265d-1569-43ed-8930-714a418c24e8.png)


## Solution 1. Two pointers

```cpp
// OJ: https://leetcode.com/problems/container-with-most-water/
// Time: O(N)
// Space: O(1)

class Solution
{
public:
    int maxArea(vector<int>& height) 
    {
        // Decalre the ans
        int ans = 0;
        
        // Make the 2 pointers
        int left =0 , right= height.size()-1;
        
        // Loop till condition fails
        while(left<=right)
        {
            // Update the ans 
            ans= max(min(height[left], height[right]) * (right-left),ans);
            
            // If the height of left < height of right increment left
            if(height[left] < height[right]) left++;
            
            // If the height of left > height of right decrement right
            else right--;
        }
        
        // Finally return the ans
        return ans;
    }
};
```

or

```cpp
// OJ: https://leetcode.com/problems/container-with-most-water/
// Time: O(N^2)
// Space: O(1)

class Solution
{
public:
    int maxArea(vector<int>& height) 
    {
        // Make the left pointer
        int left = 0;
        
        // Make the right pointer
        int right = height.size() - 1;
        
        // Create the maxi
        int maxi = 0;
        
        // Loop till left < right
        while(left < right)
        {
            // Compute the water
            int w = right - left;
            
            // Compute the height
            int h = min(height[left], height[right]);
            
            // Compute the area
            int area = h * w;
            
            // Update the maxi
            maxi = max(maxi, area);
            
            // Check the height 
            if(height[left] < height[right]) left++;
            else if(height[left] > height[right]) right--;
            
            // Else case
            else 
            {
                left++;
                right--;
            }
        }
        
        // Finally return the maxi
        return maxi;
    }
};
```
