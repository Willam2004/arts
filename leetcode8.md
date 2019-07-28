35. Search Insert Position

Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

Example 1:

Input: [1,3,5,6], 5
Output: 2
Example 2:

Input: [1,3,5,6], 2
Output: 1
Example 3:

Input: [1,3,5,6], 7
Output: 4
Example 4:

Input: [1,3,5,6], 0
Output: 0

答案：
1. 遍历数组，当发现数组中的值大于目标值，返回。
2. 二分查找，会比完全遍历和循环次数少了不少。
3. 第一次使用go来操作。
```
func searchInsert(nums []int, target int) int {
    if(nums[0] > target ){
        return 0
    }
    if(nums[len(nums) -1] < target){
        return len(nums)
    }
    for i, v := range nums {
        if(v == target){
            return i
        }else if(nums[i] < target && nums[i+1] > target){
            return i+1
        }
    }
    return 0
}
```
