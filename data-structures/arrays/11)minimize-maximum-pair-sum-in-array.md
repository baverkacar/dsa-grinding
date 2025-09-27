# Question Link
https://leetcode.com/problems/minimize-maximum-pair-sum-in-array

# Code

# Java:

```java []
class Solution {
    public int minPairSum(int[] nums) {
        Arrays.sort(nums);
        int max = 0;

        for(int i = 0, j = nums.length - 1; i < j; i++, j--) {
            max = Math.max(nums[i] + nums[j], max);
        }

        return max;
    }
}
```

# Golang:

```go []
import "sort"
func minPairSum(nums []int) int {
	sort.Ints(nums)

	maxSum := 0
	start, end := 0, len(nums)-1

	for start < end {
		sum := nums[start] + nums[end]
		if sum > maxSum {
			maxSum = sum
		}
		start++
		end--
	}

	return maxSum
}   
```

# Complexity
- Time complexity: O(n log n)
  The sorting step takes O(n log n) time, and the subsequent iteration through the array takes O(n) time. Thus, the overall time complexity is dominated by the sorting step.
- Space complexity: O(1)
  We are using a constant amount of extra space for variables, regardless of the input size. The sorting is done in place.