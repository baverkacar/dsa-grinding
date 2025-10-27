# Question Link

https://leetcode.com/problems/find-the-highest-altitude/

# Code

```java

class Solution {
    public int largestAltitude(int[] gain) {
        int initialAltitude = 0;
        int maxAltitude = 0;

        for(int i = 0; i < gain.length; i++) {
            initialAltitude += gain[i];
            maxAltitude = Math.max(maxAltitude, initialAltitude);
        }

        return maxAltitude;
    }
}
```

Complexity Analysis
- Time Complexity: O(n), where n is the length of the gain array. We traverse the gain array once to calculate the altitudes.
- Space Complexity: O(1), as we are using only a constant amount of extra space for variables.

