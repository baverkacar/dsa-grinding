# Question Link

https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/

# Code

Java:

```java
class Solution {
    public int maxVowels(String s, int k) {
        int vowelCount = 0; 
        for(int i = 0; i < k; i++) {
            if (isVowel(s.charAt(i))) {
                vowelCount++;
            }
        }
        
        int windowCount = vowelCount;
        for(int i = k; i < s.length(); i++) {
            if(isVowel(s.charAt(i))) {
                windowCount++;
            }
            if(isVowel(s.charAt(i - k))) {
                windowCount--;
            }

            vowelCount = Math.max(vowelCount, windowCount);
        }

        return vowelCount;
    }


    private boolean isVowel(char c) {
        return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u';
    }
}
```

Complexity Analysis:
- Time complexity: O(n) where n is the length of the string. We traverse the string once using a sliding window approach.
- Space complexity: O(1) as we are using only a constant amount of extra space for variables regardless of the input size.