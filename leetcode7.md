34. Find First and Last Position of Element in Sorted Array
Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return [-1, -1].

Example 1:

Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
Example 2:

Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]


解题思路：二分查找法

```
class Solution {
    public int[] searchRange(int[] nums, int target) {
        if(nums.length == 1){
            if(nums[0] == target){
                return new int[]{0,0};
            }else{
                return new int[]{-1,-1};
            }
        }
        //二分查找发
        int l = 0;  
        int[] rs = new int[]{-1,-1};
        int r = nums.length -1;
        while(l <= r){
             //取中间的位置
             int mid = (l + r) /2 ;
             int value = nums[mid];
             if(target > value){
                 //如果目标值大于中间位置，那么左边的位置，定位到中间加一
                 l = mid + 1;
             }else if(target < value){
                 //如果目标值小于中间位置，那么右边的位置，定位到中间减一
                 r = mid -1;
             }else if(target == value){
                 int start = mid, end = mid;
                 while(start >=0 && nums[start] == target){start--;}
                 while(end < nums.length && nums[end] == target){ end++;}
                 rs[0] = start +1;
                 rs[1] = end -1;
                 return rs;
             }
        }
        return rs;
    }
}
```
