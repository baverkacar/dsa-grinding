# Question Link
https://leetcode.com/problems/search-insert-position/description/

# Code
```java

class Solution {
    public int searchInsert(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        while(left <= right) {
            int mid = left + (right - left) / 2;

            if(nums[mid] > target) {
                right = mid - 1;
            }
            else if (nums[mid] < target) {
                left = mid + 1;
            }
            else {
                return mid;
            }
        }
        return left;
    }
}
```

When the while loop ends, the left pointer will be at the position where the target should be inserted to maintain the sorted order of the array. This is because:
1. If the target is less than all elements in the array, the left pointer will remain at 0, indicating that the target should be inserted at the beginning.
2. If the target is greater than all elements in the array, the left pointer will move to the end of the array (i.e., nums.length), indicating that the target should be inserted at the end.
3. If the target is between two elements in the array, the left pointer will end up at the position where the target should be inserted to maintain the sorted order.

```go
func searchInsert(nums []int, target int) int {
    start, end := 0, len(nums) - 1

    for start <= end {
        mid := start + (end - start) / 2
        if nums[mid] > target {
            end = mid -1
        } else if nums[mid] < target {
            start = mid + 1
        }else {
            return mid;
        }
    }
    return start;
}
```
# Complexity Analysis
- Time complexity: O(log n) where n is the number of elements in the array. In each step, we reduce the search space by half.
- Space complexity: O(1) since we are using only a constant amount of extra space.