# Question Link

https://leetcode.com/problems/container-with-most-water/

# Code

Java:

```java

class Solution {
    public int maxArea(int[] height) {
        int maxArea = 0;
        int left = 0;
        int right = height.length - 1;

        while (left < right) {
            int distance = right - left;
            int h = Math.min(height[left], height[right]);
            maxArea = Math.max(maxArea, distance * h);
            if(height[left] > height[right]) {
                right--;
            }else {
                left++;
            }
        }

        return maxArea;
    }
}
```
Complexity Analysis:
- Time complexity: O(n) where n is the number of lines. We use two pointers that traverse the array from both ends towards the center, ensuring each element is processed at most once.
- Space complexity: O(1) as we are using only a constant amount of extra space for the pointers and variables.

