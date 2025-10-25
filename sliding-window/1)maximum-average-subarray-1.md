# Question Link
https://leetcode.com/problems/maximum-average-subarray-i/


# Code

Java:

```java
class Solution {
    public double findMaxAverage(int[] nums, int k) {
        double sum = 0;

        for(int i = 0; i < k; i++) {
            sum += nums[i];
        }

        double currSum = sum;
        for(int i = k; i < nums.length; i++) {
            currSum += - nums[i - k] + nums[i];

            sum = Math.max(sum, currSum);
        }

        return sum / k;
    }
}
```

Complexity Analysis:
- Time complexity: O(n) where n is the number of elements in the array. We traverse the array once to calculate the initial sum of the first k elements and then again to slide the window across the array.
- Space complexity: O(1) as we are using only a constant amount of extra space for variables regardless of the input size.

