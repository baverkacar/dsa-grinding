# Question Link
https://leetcode.com/problems/reverse-string/

# Code
Java:

```java []

class Solution {
    public void reverseString(char[] s) {
        for(int leftIndex = 0, rightIndex = s.length - 1; leftIndex < rightIndex; leftIndex++, rightIndex--) {
            char temp = s[leftIndex];
            s[leftIndex] = s[rightIndex];
            s[rightIndex] = temp;
        }
    }
}
```

Golang:

```go []
func reverseString(s []byte)  {
	leftIndex, rightIndex := 0, len(s)-1
	for leftIndex < rightIndex {
		s[leftIndex], s[rightIndex] = s[rightIndex], s[leftIndex]
		leftIndex++
		rightIndex--
	}
}
```
# Complexity

- Time complexity: O(n)
  We iterate through half of the array to swap elements, which takes O(n) time.
- Space complexity: O(1)
  We perform the reversal in place, using only a constant amount of extra space for the temporary variable used during swapping.
