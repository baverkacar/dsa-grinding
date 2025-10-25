# Question Link
https://leetcode.com/problems/squares-of-a-sorted-array/

# Code

Java:

```java []
class Solution {
    public int[] sortedSquares(int[] nums) {
        int[] result = new int[nums.length];

        int start = 0;
        int end = nums.length -1;
        int fillerIndex = nums.length -1;
        while (fillerIndex >= 0) {
            if(Math.abs(nums[start]) > Math.abs(nums[end])) {
                result[fillerIndex] = nums[start] * nums[start];
                start++;
            } else {
                result[fillerIndex] = nums[end] * nums[end];
                end--;
            }
            fillerIndex--;
        }
        return result;

    }
}
```

Golang:

```go []
func sortedSquares(nums []int) []int {
	result := make([]int, len(nums))
	start , end := 0, len(nums) -1
	for i := len(nums) - 1; i >= 0; i-- {
		if math.Abs(float64(nums[start])) > math.Abs(float64(nums[end])) {
			result[i] = nums[start] * nums[start]
			start++
		} else {
			result[i] = nums[end] * nums[end]
			end--
		}
	}
	return result;
}
```

# Complexity
- Time complexity: O(n)
  We traverse the array once using two pointers, ensuring each element is processed at most once.
- Space complexity: O(n)
  We create a new array to store the squared values, which requires O(n) space. The input array is not modified.