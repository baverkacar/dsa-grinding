# Question Link
https://leetcode.com/problems/how-many-numbers-are-smaller-than-the-current-number/

# Intuition
The simplest solution that came to my mind was using brute force with nested loops. For each element, I could compare it with every other element and count how many numbers are smaller. But this approach would take O(n²) time.

After that, I thought about using Sorting with a HashMap. Sorting helps to understand the order of elements and how many smaller numbers exist before a given number.

If the number range is small (like 0 to 100), another optimal solution is using Counting Sort. It counts the frequency of each number and uses prefix sum to calculate how many numbers are smaller than the current one.

---

# Approach
### Approach 1 → Sorting + HashMap
- Clone the original array and sort it.
- Create a HashMap to store:  
  *key* → number, *value* → index of its first appearance in sorted array.
- Iterate the original array and for each number, use the map to get how many numbers are smaller.

---

### Approach 2 → Counting Sort
- Create a count array of size 101 (because 0 <= nums[i] <= 100).
- Count the frequency of each number.
- Create a prefix sum of the count array to know how many numbers are smaller than each number.
- Iterate the original array and use the count array to fill the result.

---

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