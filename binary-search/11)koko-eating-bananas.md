# Question Link

https://leetcode.com/problems/koko-eating-bananas/

# Code

```java
class Solution {
    public int minEatingSpeed(int[] piles, int h) {
        int min = 1;
        int max = 0;

        for(int i = 0; i < piles.length; i++) {
            max = Math.max(max, piles[i]);
        }

        while(min < max) {  
            int mid = min + (max - min) / 2;
            int spentHour = 0;

            for(int pile : piles) {
                spentHour += (int) Math.ceil((double) pile / mid);
            }

            if (spentHour <= h) {
                max = mid;
            }
            else {
                min = mid + 1;
            }
        }

        return min;

    }
}
```

# Complexity Analysis
- Time Complexity: O(n log m), where n is the number of piles and m is the maximum number of bananas in a pile. The binary search runs in O(log m) time, and for each mid value, we traverse the piles array in O(n) time.
- Space Complexity: O(1), as we are using only a constant amount of extra space for variables.

