# Question Link
https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/

# Code
```java
class Solution {
    public int findMin(int[] nums) {
        int l = 0;
        int r = nums.length - 1;
        int mid = 0;

        while (l < r) {
            mid = l + (r-l) / 2;
            if(nums[mid] > nums[r]) {
                l = mid + 1;
            }
            else if(nums[mid] < nums[r]) {
                r = mid;
            }
        }
        return nums[r]; // or nums[l], since l == r always
    }
}
```

```go
func findMin(nums []int) int {
    l, r := 0, len(nums)-1

    for l < r {
        mid := l + (r-l)/2
        if nums[mid] > nums[r] {
            l = mid + 1
        } else if nums[mid] < nums[r] {
            r = mid
        }
    }
    return nums[r] // or nums[l], since l == r always
}
```

# Complexity Analysis
- Time complexity: O(log n) where n is the number of elements in the array. The binary search approach reduces the search space by half in each iteration.
- Space complexity: O(1) as we are using constant extra space.