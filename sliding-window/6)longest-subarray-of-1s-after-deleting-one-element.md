# Question Link
https://leetcode.com/problems/longest-subarray-of-1s-after-deleting-one-element/

# Code

Java:

```java
class Solution {
    public int longestSubarray(int[] nums) {
        int len = 0;
        int left = 0;
        int zeroCount = 0;

        for(int right = 0; right < nums.length; right++) {
            if(nums[right] == 0) {
                zeroCount++;
            }

            while(zeroCount > 1) {
                if(nums[left] == 0) {
                    zeroCount--;
                }
                left++;
            }

            len = Math.max(len, right - left);
        }

        return len;
    }
}
```

Complexity Analysis:
- Time complexity: O(n) where n is the length of the array. We traverse the array once using a sliding window approach.
- Space complexity: O(1) as we are using only a constant amount of extra space for variables regardless of the input size.