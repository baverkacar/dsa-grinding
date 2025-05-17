
```java 
    public boolean isValid(String s) {
        int n = s.length();
        if (n % 2 == 1) return false; // odd-length strings can't be valid

        char[] stack = new char[n];
        int top = -1;

        for (char c : s.toCharArray()) {
            if (c == '(') {
                stack[++top] = ')';
            } else if (c == '{') {
                stack[++top] = '}';
            } else if (c == '[') {
                stack[++top] = ']';
            } else {
                if (top == -1 || stack[top--] != c) {
                    return false;
                }
            }
        }

        return top == -1;
    }
```

Time Complexity: O(n) – because we traverse the string once.
Space Complexity: O(n) – because we use a stack to store the closing brackets.