# Question Link

https://leetcode.com/problems/decode-string/

# Code

Java:

```java
class Solution {
    public String decodeString(String s) {
        Stack<StringBuilder> strStack = new Stack<>();
        Stack<Integer> countStack = new Stack<>();

        StringBuilder curr = new StringBuilder();
        int num = 0;
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);

            if (Character.isDigit(c)) {
                num = num * 10 + (c - '0');
            } else if (c == '[') {
                countStack.push(num); 
                strStack.push(curr);
                curr = new StringBuilder();
                num = 0;
            } else if (c == ']') {
                int count = countStack.pop();
                StringBuilder temp = strStack.pop();
                temp.append(curr.toString().repeat(count)); 
                curr = temp;
            } else {
                curr.append(c);
            }
        }
        return curr.toString();
    }
}
```

Complexity Analysis:
- Time complexity: O(n * k) where n is the length of the string and k is the maximum number of times a substring can be repeated. In the worst case, we may need to repeat a substring multiple times.
- Space complexity: O(m + d) where m is the maximum depth of nested brackets and d is the number of distinct substrings stored in the stacks. In the worst case, we may need to store multiple substrings and counts in the stacks.
