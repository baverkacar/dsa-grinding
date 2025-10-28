# Question Link
https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/

# Code

```java
// write with comment

class Solution {
    public int shipWithinDays(int[] weights, int days) {
        int left = 0;
        int right = 0;

        // Determine the minimum and maximum possible capacities
        for (int weight : weights) {
            left = Math.max(left, weight); // Minimum capacity must be at least the heaviest package
            right += weight; // Maximum capacity is the sum of all package weights
        }

        // Binary search to find the minimum capacity that allows shipping within the given days
        while (left < right) {
            int mid = left + (right - left) / 2;
            int requiredDays = 1; // Start with one day
            int currentLoad = 0; // Current load on the ship

            // Calculate how many days are needed with the current mid capacity
            for (int weight : weights) {
                if (currentLoad + weight > mid) {
                    requiredDays++; // Need an additional day
                    currentLoad = 0; // Reset current load for the new day
                }
                currentLoad += weight; // Add weight to current load
            }

            // Adjust search range based on the number of required days
            if (requiredDays > days) {
                left = mid + 1; // Increase capacity
            } else {
                right = mid; // Try a smaller capacity
            }
        }

        return left; // Minimum capacity to ship within the given days
    }
}
```

# Complexity Analysis
- Time Complexity: O(n log m), where n is the number of packages and m is the total weight of all packages. The binary search runs in O(log m) time, and for each mid value, we traverse the weights array in O(n) time.
- Space Complexity: O(1), as we are using only a constant amount of extra space for variables.
