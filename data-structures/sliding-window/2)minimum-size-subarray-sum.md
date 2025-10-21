# Question Link
https://leetcode.com/problems/minimum-size-subarray-sum/

# Code

Java:

```java

class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int left = 0, sum = 0;
        int len = Integer.MAX_VALUE;

        for(int right = 0; right < nums.length; right++) {
            sum += nums[right];
            while (sum >= target) {
                len = Math.min(len, right - left + 1);
                sum -= nums[left++];
            }
        }

        return len == Integer.MAX_VALUE ? 0 : len;
    }
}
```

Complexity Analysis:
- Time complexity: O(n) where n is the number of elements in the array. We use a sliding window approach, where each element is processed at most twice (once when expanding the window and once when contracting it).
- Space complexity: O(1) as we are using only a constant amount of extra space for variables regardless of the input size.

