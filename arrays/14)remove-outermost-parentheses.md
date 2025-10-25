# Question Link
https://leetcode.com/problems/remove-outermost-parentheses/

# Code

Java:

```java []
class Solution {
    public String removeOuterParentheses(String s) {
        int counter = 0;
        StringBuilder sb = new StringBuilder();

        for(char paranthesis : s.toCharArray()) {
            if(paranthesis == '(') {
                if (counter != 0) {
                    sb.append(paranthesis);
                }
                counter++;
            }
            else if(paranthesis == ')') {
                if(counter > 1) {
                    sb.append(paranthesis);
                }
                counter--;
            }
        }
        return sb.toString();
    }
}
```
Golang:

```go []

func removeOuterParentheses(s string) string {
	counter := 0
	var sb strings.Builder

	for _, char := range s {
		if char == '(' {
			if counter != 0 {
				sb.WriteRune(char)
			}
			counter++
		} else if char == ')' {
			if counter > 1 {
				sb.WriteRune(char)
			}
			counter--
		}
	}
	return sb.String()
}
```

# Complexity

- Time complexity: O(n)
  We traverse the string once, ensuring each character is processed at most once.
- Space complexity: O(n)
  We create a new string to store the result, which requires O(n) space. The input string is not modified.

