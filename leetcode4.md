### 11. Container With Most Water
Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

Note: You may not slant the container and n is at least 2.

![图片地址](https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question_11.jpg)

The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.


Example:
```
Input: [1,8,6,2,5,4,8,3,7]
Output: 49

```

答案：
解题思路：数组遍历，然后比较最大的数。

```
class Solution {
    public int maxArea(int[] height) {
        int maxOutput = 0;
        if(height == null || height.length == 0){
            return maxOutput;
        }
        for(int i=0;i<height.length;i++){
            for(int j=i+1;j<height.length;j++){
                int x = j - i ; 
                int y = height[j] > height[i] ? height[i] : height[j];
                if(maxOutput < x*y){
                    maxOutput = x*y;
                }
            }
        }
        return maxOutput;
    }
}

```
