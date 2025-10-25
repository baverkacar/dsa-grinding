# Question Link
https://leetcode.com/problems/merge-strings-alternately/

# Code

```java
class Solution {
    public String mergeAlternately(String word1, String word2) {
        StringBuilder sb = new StringBuilder();
        int index = 0;
        while (index < word1.length() && index < word2.length()) {
            sb.append(word1.charAt(index));
            sb.append(word2.charAt(index));
            index++;
        }

        if (word1.length() > word2.length()) {
            sb.append(word1.substring(index));
        } else if (word2.length() > word1.length()) {
            sb.append(word2.substring(index));
        }
        
        return sb.toString();
    }
}
```

```go

func mergeAlternately(word1 string, word2 string) string {
	result := make([]byte, 0, len(word1)+len(word2))

	index := 0

	for index < len(word1) && index < len(word2) {
		result = append(result, word1[index])
		result = append(result, word2[index])
		index++
	}

	if index < len(word1) {
		result = append(result, word1[index:]...)
	} else if index < len(word2) {
		result = append(result, word2[index:]...)
	}

	return string(result)
}
```

# Complexity Analysis
- Time complexity: O(m + n) where m and n are the lengths of word1 and word2 respectively. We traverse both strings once.
- Space complexity: O(m + n) for storing the result string.