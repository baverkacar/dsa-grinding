# Question Link
https://leetcode.com/problems/contains-duplicate/

# Code

Java:

```java []
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> seen = new HashSet<>();
        for (int num : nums) {
            if (seen.contains(num)) {
                return true;
            }
            seen.add(num);
        }
        return false;
    }
}
```

Golang:

```go []
func containsDuplicate(nums []int) bool {
    seen := make(map[int]struct{})
    for _, num := range nums {
        if _, exists := seen[num]; exists {
            return true
        }
        seen[num] = struct{}{}
    }
    return false
}
```
# Complexity
- Time complexity: O(n)
  We iterate through the array once, and each HashSet operation (add / contains) takes O(1) on average.

- Space complexity: O(n)
  In the worst case (when all elements are unique), we store all n elements in the HashSet.
