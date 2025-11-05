# Question Link

https://leetcode.com/problems/find-the-difference-of-two-arrays/

# Code

```java

class Solution {
    public List<List<Integer>> findDifference(int[] nums1, int[] nums2) {
        HashSet<Integer> set1 = new HashSet<>();
        HashSet<Integer> set2 = new HashSet<>();
        
        for (int num : nums1) {
            set1.add(num);
        }
        
        for (int num : nums2) {
            set2.add(num);
        }
        
        List<Integer> diff1 = new ArrayList<>();
        List<Integer> diff2 = new ArrayList<>();
        
        for (int num : set1) {
            if (!set2.contains(num)) {
                diff1.add(num);
            }
        }
        
        for (int num : set2) {
            if (!set1.contains(num)) {
                diff2.add(num);
            }
        }
        
        List<List<Integer>> result = new ArrayList<>();
        result.add(diff1);
        result.add(diff2);
        
        return result;
    }
}
```

# Complexity Analysis
- Time Complexity: O(n + m), where n and m are the lengths of nums1 and nums2 respectively. We traverse both arrays once to populate the sets and then again to find the differences.
- Space Complexity: O(n + m), as we use two sets to store the unique elements from both arrays.
