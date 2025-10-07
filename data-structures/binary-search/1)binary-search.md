# Question Link
https://leetcode.com/problems/binary-search/

# Code
```java
class Solution {
    public int search(int[] nums, int target) {
        int left =0;
        int right = nums.length - 1;

        while(left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] > target) {
                right = mid - 1;
            }
            else if(nums[mid] < target) {
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

Golang:
```go

func search(nums []int, target int) int {
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
	return -1;
}
```

Complexity Analysis
- Time complexity: O(log n) where n is the number of elements in the array. In each step, we reduce the search space by half.
- Space complexity: O(1) since we are using only a constant amount of extra space.