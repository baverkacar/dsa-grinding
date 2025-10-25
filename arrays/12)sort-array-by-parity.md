# Question Link
https://leetcode.com/problems/sort-array-by-parity/

# Code

```java

class Solution {
    public int[] sortArrayByParity(int[] nums) {
        int start = 0 , end = nums.length - 1;

        while (start < end) {
            if (nums[start] % 2 == 0) {
                start++;
            }
            else if (nums[end] % 2 != 0) {
                end--;
            }
            else {
                int temp = nums[start];
                nums[start] = nums[end];
                nums[end] = temp;
            }
        }
        return nums;
    }
}

```

Golang:
```go
func sortArrayByParity(nums []int) []int {
    start, end := 0, len(nums) - 1

    for start < end {
        if nums[start] % 2 == 0 {
            start++
        } else if nums[end] % 2 != 0 {
            end--
        } else {
            nums[start], nums[end] = nums[end], nums[start]
        }
    }
    return nums
}
``` 

# Complexity
- Time complexity: O(n)
  We iterate through the array with two pointers, ensuring each element is checked at most once.
- Space complexity: O(1)
  We perform the sorting in place, using only a constant amount of extra space for the pointers and temporary variable used during swapping.

