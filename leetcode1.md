Given a string, find the length of the longest substring without repeating characters.

Example 1:
```
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
Example 2:

Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
Example 3:

Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

java计算
```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        if(s == null || s.length() == 0){
            return 0;
        }
        int max = 1;
        int start = 0;
        for(int i= 1 ; i< s.length(); i++){
            for(int j = i-1; j >= start; j--){
                if(s.charAt(i) == s.charAt(j)){
                    start =  j +1;
                }   
            }            
            max = Math.max(max, i-start + 1);
        }
        return max;
    }
}
```
