# Question Link

https://leetcode.com/problems/max-consecutive-ones-iii/


# Code

Java:

```java
class Solution {
    public int longestOnes(int[] nums, int k) {
        int l = 0;
        int len = 0;
        int zeroCounter = 0;

        for(int r = 0; r < nums.length; r++) {
            if(nums[r] == 0) {
                zeroCounter++;
            }

            while(zeroCounter > k) {
                if (nums[l] == 0) {
                    zeroCounter--;
                }
                l++;
            }

            len = Math.max(len, r - l +1);
        }
        return len;
    }
}
```

Complexity Analysis:
- Time complexity: O(n) where n is the length of the array. We traverse the array once using a sliding window approach.
- Space complexity: O(1) as we are using only a constant amount of extra space for variables regardless of the input size.
