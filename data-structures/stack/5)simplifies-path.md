```java
class Solution {
    public String simplifyPath(String path) {
        // split path in to the directory list 
        String[] parts = path.split("/"); // "/" better than "/+" because we avoid regex for complexi

        // create pathStack with len of parts.len - 1 because first element of parts is "". 
        Deque<String> pathStack = new LinkedList<>(); // Deque is more efficient than array.

        for(String part : parts) {
            if (part.equals("..")) {
                if(!pathStack.isEmpty()) pathStack.pop();
            } 
            else if (!part.equals("") && !part.equals(".")) {
                pathStack.push(part);
            }
        }
        
        StringBuilder result = new StringBuilder();
        Iterator<String> it = pathStack.descendingIterator();
        while (it.hasNext()) {
            result.append("/").append(it.next());
        }

        return result.length() == 0 ? "/" : result.toString();
    }

}
```


Time Complexity: O(n) - where n is the length of the input path. We traverse the path once to split it into parts and then again to build the simplified path.
Space Complexity: O(n) - in the worst case, we might store all parts of the path in the stack.

