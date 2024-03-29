链接： https://leetcode.com/problems/string-to-integer-atoi/

Implement atoi which converts a string to an integer.

The function first discards as many whitespace characters as necessary until the first non-whitespace character is found. Then, starting from this character, takes an optional initial plus or minus sign followed by as many numerical digits as possible, and interprets them as a numerical value.

The string can contain additional characters after those that form the integral number, which are ignored and have no effect on the behavior of this function.

If the first sequence of non-whitespace characters in str is not a valid integral number, or if no such sequence exists because either str is empty or it contains only whitespace characters, no conversion is performed.

If no valid conversion could be performed, a zero value is returned.

Note:

Only the space character ' ' is considered as whitespace character.
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. If the numerical value is out of the range of representable values, INT_MAX (231 − 1) or INT_MIN (−231) is returned.

答案：
```
class Solution {
    public int myAtoi(String str) {
        if(str == null || "".equals(str)){
            return 0;
        }
        StringBuilder sb = new StringBuilder();
        for(int i=0;i<str.length();i++){
            char c = str.charAt(i);
            String last = sb.toString();
            if(c == ' '){
                if(sb.length() > 0){
                     break;
                }
                continue;
            }
            if( c == '-' || c == '+'){
                if(last.indexOf("-") > -1 || last.indexOf("+") > -1){
                    break;
                }else if(last.length() > 0 && Character.isDigit(last.charAt(0))) {
                    break;
                }else{
                    sb.append(c);
                }
            }else if(Character.isDigit(c)){
                 sb.append(c);
            }else break;
        }
        String result = sb.toString();
        if(result.length() == 0){
            return 0;
        }
        if(result.equals("-") || result.equals("+")){
            return 0;
        }
        Double v = Double.valueOf(sb.toString());
        if(v < Integer.MIN_VALUE)return Integer.MIN_VALUE;
        if(v > Integer.MAX_VALUE)return Integer.MAX_VALUE;
        return v.intValue();
    }
}
```
