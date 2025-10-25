# Question Link
https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/

# Code
```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        int[] result = {-1, -1};
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if(nums[mid] < target) {
                left = mid + 1;
            }
            else if (nums[mid] > target) {
                right = mid - 1;
            }
            else {
                int l = findLeftMostIndexWithBS(target, left, mid, nums);
                int r = findRightMostIndexWithBS(target,mid ,right, nums);
                result[0] = Math.min(l, mid);
                result[1] = Math.max(mid, r);
                return result;
            }
        }
        return result;
    }

    private int findLeftMostIndexWithBS(int target, int left, int right, int[] nums) {
        int result = -1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if(target > nums[mid]) {
                left = mid + 1;
            }
            else {
                result = mid;
                right = mid -1;
            }
        }
        return result;
    }

    private int findRightMostIndexWithBS(int target, int left, int right, int[] nums) {
        int result = -1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if(target < nums[mid]) {
                right = mid - 1;
            }
            else {
                result = mid;
                left = mid + 1;
            }
        }
        return result;
    }
}
```

```go
func searchRange(nums []int, target int) []int {
    left, right := 0, len(nums)-1
    result := []int{-1, -1}

    for left <= right {
        mid := left + (right-left)/2
        if nums[mid] < target {
            left = mid + 1
        } else if nums[mid] > target {
            right = mid - 1
        } else {
            l := findLeftMostIndexWithBS(target, left, mid, nums)
            r := findRightMostIndexWithBS(target, mid, right, nums)
            if l != -1 {
                result[0] = l
            } else {
                result[0] = mid
            }
            if r != -1 {
                result[1] = r
            } else {
                result[1] = mid
            }
            return result
        }
    }
    return result
}
func findLeftMostIndexWithBS(target, left, right int, nums []int) int {
    result := -1
    for left <= right {
        mid := left + (right-left)/2
        if target > nums[mid] {
            left = mid + 1
        } else {
            result = mid
            right = mid - 1
        }
    }
    return result
}
func findRightMostIndexWithBS(target, left, right int, nums []int) int {
    result := -1
    for left <= right {
        mid := left + (right-left)/2
        if target < nums[mid] {
            right = mid - 1
        } else {
            result = mid
            left = mid + 1
        }
    }
    return result
}
```