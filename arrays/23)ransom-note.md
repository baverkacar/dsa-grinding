# Question Link
https://leetcode.com/problems/ransom-note/


# Code

Java:

```java 
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        int[] counter = new int[26];

        for (int i = 0; i < magazine.length(); i++) {
            counter[magazine.charAt(i) - 'a']++;
        }

        for (int i = 0; i < ransomNote.length(); i++) {
            
            if (counter[ransomNote.charAt(i) - 'a'] < 1) {
                return false;
            }
            counter[ransomNote.charAt(i) - 'a']--;
        }

        return true;
    }
}
```


Complexity Analysis:
- Time complexity: O(m + n) where m is the length of the ransomNote and n is the length of the magazine. We traverse both strings once to count the characters and check availability.
- Space complexity: O(1) since the size of the counter array is fixed at 26, regardless of the input size.

