# Question Link
https://leetcode.com/problems/find-peak-element/

# Code
```java
class Solution {
    public int findPeakElement(int[] nums) {
        int left = 0;
        int right = nums.length - 1;
        while( left <= right) {
            int mid = left + (right - left) / 2;

            if(mid > 0 && nums[mid] < nums[mid -1]) {
                right = mid - 1;
            }
            else if (mid < nums.length - 1 && nums[mid] < nums[mid+1]) {
                left = mid + 1;
            }
            else {
                return mid;
            }
        }
        return -1;
    }
}
```

```go
func findPeakElement(nums []int) int {
    left, right := 0, len(nums)-1

    for left <= right {
        mid := left + (right-left)/2

        if mid > 0 && nums[mid] < nums[mid-1] {
            right = mid - 1
        } else if mid < len(nums)-1 && nums[mid] < nums[mid+1] {
            left = mid + 1
        } else {
            return mid
        }
    }
    return -1
}
```
# Complexity Analysis
- Time complexity: O(log n) where n is the number of elements in the array. The binary search approach reduces the search space by half in each iteration.
- Space complexity: O(1) as we are using constant extra space.