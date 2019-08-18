### leetcode第十周，坚持用go语言实现
53. Maximum Subarray
Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

Example:

Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
Follow up:

If you have figured out the O(n) solution, try coding another solution using the divide and conquer approach, which is more subtle.

my answer：
```
func maxSubArray(nums []int) int {
	var max int = 0
	var largest int = math.MinInt32
	for _,i := range nums {
		max += i
		if max > largest {
			largest = max
		}
		if max <= 0 {
			max = 0
		}
	}
	return largest
}
```

### 解题思路
* 遍历数组
* 累加数组，并赋值给返回数
* 如果累加的值小于等于0，那么重新设为0
