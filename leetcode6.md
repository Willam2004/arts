Given an array nums and a value val, remove all instances of that value in-place and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

Example 1:

Given nums = [3,2,2,3], val = 3,

Your function should return length = 2, with the first two elements of nums being 2.

It doesn't matter what you leave beyond the returned length.
Example 2:

Given nums = [0,1,2,2,3,0,4,2], val = 2,

Your function should return length = 5, with the first five elements of nums containing 0, 1, 3, 0, and 4.

Note that the order of those five elements can be arbitrary.

It doesn't matter what values are set beyond the returned length.

解题思路：
1. 注意使用in-place algorithm，就是不能单独再分配一个数组进行处理。 
2. 涉及到数组中删除，转变思路不是判断相等而进行删除，而是把不同的更改原数组。 


* [in-place算法](https://zh.wikipedia.org/wiki/%E5%8E%9F%E5%9C%B0%E7%AE%97%E6%B3%95)


## java实现

```
class Solution {
    public int removeElement(int[] nums, int val) {
        if(nums == null || nums.length == 0){
            return 0;
        }
        int  j = 0;
        for(int i = 0; i<nums.length; i++){
            int v = nums[i];
            if(v != val){
                nums[j] = nums[i];
                j++;
            }
        }
        return j;
    }
}
```

## kotlin实现
```
class Solution {
    fun removeElement(nums: IntArray, `val`: Int): Int {
        var  i:Int = 0;
        for( j in 0 until nums.size ){
            var v = nums.get(j);
            if(`val` != v){
                nums.set(i, v);
                i++;
            }
        }
        return i;
    }
}
```
