# Question Link

https://leetcode.com/problems/remove-duplicates-from-sorted-array/

# Code

Java:
```java
class Solution {
    public int removeDuplicates(int[] nums) {   
        int k = 1;
        int slow = 0;
        for(int fast = 1; fast < nums.length; fast++) {
            if(nums[slow] != nums[fast]) {
                nums[++slow] = nums[fast];
                k++; 
            }
        }
        return k;
    }
}
```

Golang:

```go
func removeDuplicatest(nums []int) int {
    k := 1
    slow := 0
    for fast := 1; fast < len(nums); fast++ {
        if nums[slow] != nums[fast] {
            slow++
            nums[slow] = nums[fast]
            k++
        }
    }
    return k
}
```

# Complexity Analysis
- Time complexity: O(n) where n is the length of the array. We traverse the array once.
- Space complexity: O(1) as we are using constant extra space.