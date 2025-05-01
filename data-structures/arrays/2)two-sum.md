# Question Link
https://leetcode.com/problems/two-sum/

# Complexity
- Time complexity:  
O(n) — because we traverse the array only once.

- Space complexity:  
O(n) — because we store up to n elements in the HashMap.

# Code
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();

        for (int index = 0; index < nums.length; index++) {
            int complement = target - nums[index];
            if (map.containsKey(complement)) {
                return new int[] { map.get(complement), index };
            }
            map.put(nums[index], index);
        }

        return null;
    }
}
