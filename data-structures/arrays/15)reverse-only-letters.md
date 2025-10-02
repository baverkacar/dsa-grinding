# Question Link
https://leetcode.com/problems/reverse-only-letters/

# Code

Java:

```java []
class Solution {
    public String reverseOnlyLetters(String s) {
        char[] chars = s.toCharArray();
        int left = 0; 
        int right = chars.length - 1; 

        while (left < right) { 

            
            while (left < right && !Character.isLetter(chars[left])) {
                left++;
            }

           
            while (left < right && !Character.isLetter(chars[right])) {
                right--; 
            }

            if (left < right) {
                char temp = chars[left]; 
                chars[left] = chars[right]; 
                chars[right] = temp;
                left++; 
                right--;
            }
        }

        return new String(chars); 
    }
}
```

Golang:

```go []
func reverseOnlyLetters(s string) string {
	chars := []rune(s)
	
	start, end := 0, len(chars)-1
	
	for start < end {
		if !unicode.IsLetter(chars[start]) {
			start++
		} else if !unicode.IsLetter(chars[end]) {
			end--
		} else {
			chars[start], chars[end] = chars[end], chars[start]
			start++
			end--
		}
	}
	return string(chars)
}
```

# Complexity
- Time complexity: O(n)
  We traverse the string once using two pointers, ensuring each character is processed at most once.
- Space complexity: O(n)
  We create a new array to store the characters, which requires O(n) space. The input string is not modified.
