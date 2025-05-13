```java 
public int removeElement(int[] nums, int val) {
    int slow = 0;
    for (int fast = 0; fast < nums.length; fast++) {
        if (nums[fast] != val) {
            nums[slow] = nums[fast];
            slow++;
        }
    }  
    return slow;
}
```

# Time Complexity: O(n) – because we traverse the array once.
# Space Complexity: O(1) – because we only use a constant amount of extra space.