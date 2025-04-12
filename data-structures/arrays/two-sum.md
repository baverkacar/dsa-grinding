# Question Link
https://leetcode.com/problems/two-sum/

# Intuition
In this problem, we are given an array and a target number. My first thought was to check every pair of numbers in the array to see if their sum equals the target. But this brute-force approach would take O(n²) time. To optimize, I thought about using a HashMap to store already visited numbers for fast lookup.

# Approach
- Create a HashMap where:
  - *Key* → Number from the array  
  - *Value* → Index of that number  
- Iterate through the array:
  - For each number, calculate its complement (target - current number).
  - Check if the complement exists in the HashMap.
    - If it does, return the current index and the index of the complement from the map.
  - Otherwise, put the current number and its index into the map.
- If no pair found, return null (this case won't happen because the problem guarantees a solution).

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
