# Question Link
https://leetcode.com/problems/reverse-vowels-of-a-string/

# Code

Java:

```java []
class Solution {
    public String reverseVowels(String s) {
        int leftIndex = 0;
        int rightIndex = s.length() - 1;

        char[] characters = s.toCharArray();

        while (leftIndex < rightIndex) {
            char leftChar = characters[leftIndex];
            char rightChar = characters[rightIndex];

            if (!isVowel(leftChar)) {
                leftIndex++;
                continue;
            }
            if (!isVowel(rightChar)) {
                rightIndex--;
                continue;
            }
            // swap
            characters[leftIndex] = rightChar;
            characters[rightIndex] = leftChar;
            leftIndex++;
            rightIndex--;
        }
        return new String(characters);
    }

    public boolean isVowel(char character) {
        return character == 'A' || character == 'E' || character == 'I' || character == 'O' || character == 'U' ||
                character == 'a' || character == 'e' || character == 'i' || character == 'o' || character == 'u';
    }
}
```

Golang:

```go []
func reverseVowels(s string) string {
    leftIndex := 0
    rightIndex := len(s) - 1

    characters := []rune(s)

    for leftIndex < rightIndex {
        leftChar := characters[leftIndex]
        rightChar := characters[rightIndex]

        if !isVowel(leftChar) {
            leftIndex++
            continue
        }
        if !isVowel(rightChar) {
            rightIndex--
            continue
        }
        // swap
        characters[leftIndex], characters[rightIndex] = characters[rightIndex], characters[leftIndex]
        leftIndex++
        rightIndex--
    }
    return string(characters)
}

func isVowel(character rune) bool {
    return character == 'A' || character == 'E' || character == 'I' || character == 'O' || character == 'U' ||
        character == 'a' || character == 'e' || character == 'i' || character == 'o' || character == 'u'
}
```

# Complexity

- Time complexity: O(n)
  We iterate through the string once, with each character being processed at most twice (once by each pointer).
- Space complexity: O(n)
  We create a character array to hold the modified string, which requires O(n) space.

