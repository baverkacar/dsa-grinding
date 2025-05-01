# Question Link
https://leetcode.com/problems/how-many-numbers-are-smaller-than-the-current-number/

# Complexity

| Approach | Time Complexity | Space Complexity |
|----------|-----------------|-----------------|
| Sorting + HashMap | O(n log n) | O(n) |
| Counting Sort | O(n + k) | O(k), where k is the range of numbers |

---

# Code (Sorting + HashMap)
```java
class Solution {
    public int[] smallerNumbersThanCurrent(int[] nums) {
        int[] result = new int[nums.length];
        int[] sorted = nums.clone();
        Arrays.sort(sorted);

        HashMap<Integer, Integer> map = new HashMap<>();

        for (int i = 0; i < sorted.length; i++) {
            if (!map.containsKey(sorted[i])) {
                map.put(sorted[i], i);
            }
        }

        for (int i = 0; i < nums.length; i++) {
            result[i] = map.get(nums[i]);
        }

        return result;
    }
}
```

# Code (Counting sort)

```java
class Solution {
    public int[] smallerNumbersThanCurrent(int[] nums) {
        int[] count = new int[101];

        for (int num : nums) {
            count[num]++;
        }

        for (int i = 1; i < 101; i++) {
            count[i] += count[i - 1];
        }

        int[] result = new int[nums.length];

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == 0) {
                result[i] = 0;
            } else {
                result[i] = count[nums[i] - 1];
            }
        }

        return result;
    }
}

```