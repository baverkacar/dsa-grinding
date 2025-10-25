# Question Link

https://leetcode.com/problems/move-zeroes/

# Code

Java:

```java

class Solution {
    public void moveZeroes(int[] nums) {
    int l = 0; 
    
    for (int r = 0; r < nums.length; r++) {
        if (nums[r] != 0) {
            int temp = nums[l];
            nums[l] = nums[r];
            nums[r] = temp;
            l++;
        }
    }
    }
}
```

Complexity Analysis:
- Time complexity: O(n) where n is the length of the array. We traverse the array once using a two-pointer approach.
- Space complexity: O(1) as we are using only a constant amount of extra space for variables regardless of the input size.

