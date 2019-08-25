17. Letter Combinations of a Phone Number
Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

Example:

Input: "23"
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].

代码解决方案：
```
var letters map[string]string
var output []string

func letterCombinations(digits string) []string {
	letters = make(map[string]string)
	output = make([]string, 0)
	letters["2"] = "abc"
	letters["3"] = "def"
	letters["4"] = "ghi"
	letters["5"] = "jkl"
	letters["6"] = "mno"
	letters["7"] = "pqrs"
	letters["8"] = "tuv"
	letters["9"] = "wxyz"

	if len(digits) != 0 {
		backTrack("", digits)
	}
	return output
}


func backTrack(combination string, next_digits string) {
	if len(next_digits) == 0 {
		output = append(output, combination)
	} else {
		var digit = next_digits[0:1]
		s := letters[digit]
		for index, _ := range s {
			lt := letters[digit][index : index+1]
			backTrack(combination+lt, next_digits[1:])
		}
	}
}

```
