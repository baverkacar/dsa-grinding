# Question Link

https://leetcode.com/problems/longest-substring-without-repeating-characters/

# Code

Java:

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        HashSet<Character> map = new HashSet<>();

        int len = 0;
        int l = 0;

        for(int r = 0; r < s.length(); r++) {
            while (map.contains(s.charAt(r))) {
                map.remove(s.charAt(l));
                l++;
            }
            map.add(s.charAt(r));
            len = Math.max(len, r - l + 1);
        }

        return len;  
    }
}
```

Complexity Analysis:
- Time complexity: O(n) where n is the length of the string. We use a sliding window approach, where each character is processed at most twice (once when expanding the window and once when contracting it).
- Space complexity: O(min(m, n)) where m is the size of the character set and n is the length of the string. In the worst case, we may need to store all characters in the current window.

