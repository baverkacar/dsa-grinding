```java
class Solution {
    public int missingNumber(int[] nums) {
        int k = nums.length;
        int sumOfNumbers = (k * (k + 1)) / 2;
        for (int i = 0; i < nums.length; i++){
            sumOfNumbers -= nums[i];
        }
        return sumOfNumbers;
    }
}
```

Time Complexity: O(n) – because it iterates through the array once to subtract each number.

Space Complexity: O(1) – because it uses only a constant amount of extra memory regardless of input size.