leetcode link : https://leetcode.com/problems/implement-strstr/

Implement strStr().

Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

Example 1:

Input: haystack = "hello", needle = "ll"
Output: 2
Example 2:

Input: haystack = "aaaaa", needle = "bba"
Output: -1
Clarification:

What should we return when needle is an empty string? This is a great question to ask during an interview.

For the purpose of this problem, we will return 0 when needle is an empty string. This is consistent to C's strstr() and Java's indexOf().

Answer： 我的答案

```
class Solution {
    public int strStr(String haystack, String needle) {
        if(needle == null || needle.length() == 0){
            return 0;
        }
        int loop = haystack.length() - needle.length();
        for(int i=0 ; i<= loop; i++){
            String original = String.valueOf(haystack.charAt(i));
            String match = String.valueOf(needle.charAt(0));
            if(!original.equals(match)){
                continue;
            }
            String strStr = haystack.substring(i, needle.length() + i);
            if(strStr.equals(needle)){
                return i;
            }
        }
        return -1;
    }
}
```
