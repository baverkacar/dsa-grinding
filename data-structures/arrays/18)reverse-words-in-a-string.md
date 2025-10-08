# Question Link
https://leetcode.com/problems/reverse-words-in-a-string/

# Code
```java
class Solution {
    public String reverseWords(String s) {
        String[] words = s.trim().split("\\s+"); 
        StringBuilder sb = new StringBuilder();


        for (int i = words.length - 1; i >= 0; i--) {
            sb.append(words[i]);
            if (i > 0) sb.append(" "); 
        }

        return sb.toString();
    }
}
```

```go

func reverseWords(s string) string {
	words := strings.Fields(s)

	for i, j := 0, len(words)-1; i < j; i, j = i+1, j-1 {
		words[i], words[j] = words[j], words[i]
	}
	return strings.Join(words, " ")
}
```
# Complexity Analysis
- Time complexity: O(n) where n is the length of the string. We traverse the string to split it into words and then again to join them in reverse order.
- Space complexity: O(n) for storing the words in an array and the final result string.