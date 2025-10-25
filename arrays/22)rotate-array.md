# Question Link

https://leetcode.com/problems/rotate-array/

# Code

Java:

```java
class Solution {
    public void rotate(int[] nums, int k) {
        k = k % nums.length;

        reverse(nums, 0, nums.length - 1);   // 1. tüm diziyi ters çevir
        reverse(nums, 0, k - 1);             // 2. ilk k elemanı düzelt
        reverse(nums, k, nums.length - 1);   // 3. kalan kısmı düzelt
    }

    private void reverse(int[] nums, int start, int end) {
        while (start < end) {
            int temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
            start++;
            end--;
        }
    }
}
```

Complexity Analysis:
- Time complexity: O(n) where n is the number of elements in the array. The algorithm involves three passes through the array, each taking O(n) time.
- Space complexity: O(1) as the rotation is done in place without using any additional data structures that grow with input size.