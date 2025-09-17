# Question Link
https://leetcode.com/problems/concatenation-of-two-arrays/

# Code

Java:

```java []
    public int[] getConcatenation(int[] nums) {
        int[] concatenationArr = new int[nums.length * 2];

        for (int index = 0; index < nums.length; index++) {
            concatenationArr[index] = nums[index];
            concatenationArr[index + nums.length] = nums[index];
        }
        return concatenationArr;
    }
```

Golang:

```go []
func getConcatenation(nums []int) []int {
	concatenationArr := make([]int, len(nums) * 2)

	for index := 0; index < len(nums); index++ {
		concatenationArr[index] = nums[index]
		concatenationArr[index + len(nums)] = nums[index]
	}

	return concatenationArr
}
```

# Complexity

- Time complexity: O(n)
  We iterate through the array once to copy elements to the new array.
- Space complexity: O(n)
  We create a new array of size 2n to store the concatenated result.
