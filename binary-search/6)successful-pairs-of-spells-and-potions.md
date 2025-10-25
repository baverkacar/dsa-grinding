# Question Link

https://leetcode.com/problems/successful-pairs-of-spells-and-potions/

# Code

Java:
```java
class Solution {
    public int[] successfulPairs(int[] spells, int[] potions, long success) {
        int[] result = new int[spells.length];
        Arrays.sort(potions);


        for(int i = 0 ; i < spells.length; i++) {
            result[i] = bs(success, potions, spells[i]);
        }
        return result;
    }

    private int bs(long success, int[] potions, int spell) {
        int left = 0;
        int right = potions.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            if ((long) potions[mid] * spell >= success) {
                right = mid - 1;
            }
            else {
                left = mid + 1;
            }
        }

        return potions.length - left;
    }
}
```

Golang:
```go
func successfulPairs(spells []int, potions []int, success int) []int {
	result := make([]int, len(spells))
	sort.Ints(potions)

	for i, spell := range spells {
		result[i] = bs(potions, success, spell)
	}

	return result
}

func bs(potions []int, success int, spell int) int {
	left, right := 0, len(potions)-1
	for left <= right {
		mid := left + (right-left)/2
		if potions[mid]*spell >= success {
			right = mid - 1
		} else {
			left = mid + 1
		}
	}
	return len(potions) - left
}
```

# Complexity Analysis
- Time complexity: O(m log m + n log m) where m is the number of potions and n is the number of spells. Sorting the potions takes O(m log m) time, and for each spell, we perform a binary search on the potions which takes O(log m) time.
- Space complexity: O(1) if we ignore the output array, otherwise O(n) for storing the result.