# Question Link
https://leetcode.com/problems/longest-common-prefix/

# Code

Java:

```java []
public class Solution {
        public String longestCommonPrefix(String[] strs) {
            if (strs == null || strs.length == 0) return "";
            String longestPrefix = strs[0];

            for (int i = 1; i < strs.length; i++) {
                longestPrefix = findLongestPrefix(longestPrefix, strs[i]);
                if (longestPrefix.isEmpty()) {
                    break;
                }
            }
            return longestPrefix;
        }

        private String findLongestPrefix(String a, String b) {
            int minLen = Math.min(a.length(), b.length());
            int i = 0;

            while (i < minLen && a.charAt(i) == b.charAt(i)) {
                i++;
            }
            return a.substring(0, i);
        }
}
```

Golang:

```go []
func longestCommonPrefix(strs []string) string {
	if strs == nil || len(strs) == 0 {
		return ""
	}
	longestPrefix := strs[0]
	for i := 0; i < len(strs); i++ {
		longestPrefix = findLongestPrefix(longestPrefix, strs[i])

		if longestPrefix == "" {
			break
		}
	}
	return longestPrefix
}

func findLongestPrefix(a string, b string) string {
	minLen := int(math.Min(float64(len(a)), float64(len(b))))
	i := 0

	for i < minLen && a[i] == b[i] {
		i++
	}
	return a[:i]
}
```

# Complexity
- Time complexity: O(n * m)
  - n is the number of strings in the array.
  - m is the length of the shortest string.
  - In the worst case, we compare each character of each string with the current longest prefix.
- Space complexity: O(1)
  - We use a constant amount of extra space for variables, regardless of the input size.