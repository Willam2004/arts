Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
For example, two is written as II in Roman numeral, just two one's added together. Twelve is written as, XII, which is simply X + II. The number twenty seven is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

I can be placed before V (5) and X (10) to make 4 and 9. 
X can be placed before L (50) and C (100) to make 40 and 90. 
C can be placed before D (500) and M (1000) to make 400 and 900.
Given a roman numeral, convert it to an integer. Input is guaranteed to be within the range from 1 to 3999.

Example 1:

Input: "III"
Output: 3
Example 2:

Input: "IV"
Output: 4
Example 3:

Input: "IX"
Output: 9
Example 4:

Input: "LVIII"
Output: 58
Explanation: L = 50, V= 5, III = 3.
Example 5:

Input: "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.


my answer:
```
class Solution {
    public int romanToInt(String s) {
        if(s == null || s.length() == 0){
            return 0;
        }
        Map<String,Integer> maps = new HashMap<String,Integer>();
        maps.put("I", 1);
        maps.put("V", 5);
        maps.put("X", 10);
        maps.put("L", 50);
        maps.put("C", 100);
        maps.put("D", 500);
        maps.put("M", 1000);
        
        
        maps.put("IV", 4);
        maps.put("IX", 9);
        maps.put("XL", 40);
        maps.put("XC", 90);
        maps.put("CD",400);
        maps.put("CM", 900);
        
        Integer result = maps.get(s);
        if(result != null){
            return result;
        }
        int sum = 0;
        for(int i=0;i<s.length();i++){
            String c = String.valueOf(s.charAt(i));
            int nextIndex = i+1;
              if(nextIndex == s.length()){
               //last num
                sum = sum + maps.get(c);
                break;
              }
            char next = s.charAt(nextIndex);
            if(c.equals("I")){
                if(next == 'V' || next == 'X'){
                        sum = sum + maps.get(c + next);
                        i = i + 1; 
                        continue;
                     }else{
                         sum = sum + maps.get(c);
                }
               
            }else if(c.equals("X")){
                if(next == 'L' || next == 'C'){
                    sum = sum + maps.get(c + next);
                    i = i + 1; 
                    continue;
                }else{
                     sum = sum + maps.get(c);
                }
            }else if(c.equals("C")){
                if(next == 'D' || next == 'M'){
                    sum = sum + maps.get(c + next);
                    i = i + 1; 
                    continue;
                }else{
                     sum = sum + maps.get(c);
                }
            }else{
                sum = sum + maps.get(c);
            }
        }
        return sum;
                
    }
}
```
要点：
1. 数组的判断
2. map的使用
