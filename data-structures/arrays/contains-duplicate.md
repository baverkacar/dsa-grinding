# Question Link
<!-- Add the link to the question here, e.g. https://leetcode.com/problems/contains-duplicate/description/-->
https://leetcode.com/problems/contains-duplicate/

# Intuition
The problem asks whether there are any duplicate elements in the given array.  
My first thought is to use a data structure that allows me to check for the existence of an element quickly.  
A HashSet fits perfectly here because it provides constant time lookup.  
If I see the same element again while iterating through the array, I can immediately return true.

# Approach
- Initialize an empty HashSet to keep track of seen elements.
- Iterate through each element in the array:
    - If the current element already exists in the HashSet, return true (we found a duplicate).
    - Otherwise, add the element to the HashSet.
- If the iteration finishes without finding any duplicates, return false.

This approach ensures O(1) lookup and insertion using a HashSet, making the solution efficient and simple.

# Complexity
- Time complexity: O(n) 
  We iterate through the array once, and each HashSet operation (add / contains) takes O(1) on average.

- Space complexity: O(n) 
  In the worst case (when all elements are unique), we store all n elements in the HashSet.

# Code
```java []
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> seen = new HashSet<>();
        for (int num : nums) {
            if (seen.contains(num)) {
                return true;
            }
            seen.add(num);
        }
        return false;
    }
}
```