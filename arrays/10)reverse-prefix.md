# Question Link
https://leetcode.com/problems/reverse-prefix-of-word/

# Code

Java:

```java []

class Solution {
    public String reversePrefix(String word, char ch) {
        int lastIndex= word.indexOf(ch);
        StringBuilder sb = new StringBuilder(word);

        for(int start = 0; start < lastIndex; start++) {
            char temp = sb.charAt(start);
            sb.setCharAt(start, sb.charAt(lastIndex));
            sb.setCharAt(lastIndex, temp);
            lastIndex--;
        }

        return sb.toString();
    }
}

```

Golang:

```go []

func reversePrefix(word string, ch byte) string {
    sb := []byte(word)

	start := 0
	lastIndex := 0
	
	for i := 0; i < len(sb); i++ {
		if sb[i] == ch {
			lastIndex = i
            break
		}
	}

	for start < lastIndex {
		temp := sb[start]
		sb[start] = sb[lastIndex]
		sb[lastIndex] = temp
        start++
        lastIndex--
	}
	
	return string(sb)
}   
```


# Complexity
- Time complexity: O(n)
  We iterate through the array up to the index of the specified character, which takes O(n) time in the worst case.
- Space complexity: O(n)
  We create a new string builder to store the modified string, which takes O(n) space.