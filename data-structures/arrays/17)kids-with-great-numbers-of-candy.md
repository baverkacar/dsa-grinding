# Question Link
https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/

# Code

```java
class Solution {
    public List<Boolean> kidsWithCandies(int[] candies, int extraCandies) {
        int max = 0;
        for(int i = 0; i < candies.length; i++) {
            if(candies[i] > max) {
                max = candies[i];
            }
        }
        
        List<Boolean> result = new ArrayList<>();
        for(int i = 0; i < candies.length; i++) {
            if (candies[i] + extraCandies >= max) {
                result.add(true);
                continue;
            }
            result.add(false);
        }

        return result;
     }
}
```

```go
func kidsWithCandies(candies []int, extraCandies int) []bool {
    max := 0
    for i := 0; i < len(candies); i++ {
        if candies[i] > max {
            max = candies[i]
        }
    }

    result := make([]bool, len(candies))
    for i := 0; i < len(candies); i++ {
        if candies[i]+extraCandies >= max {
            result[i] = true
            continue
        }
        result[i] = false
    }

    return result
}
```
# Complexity Analysis
- Time complexity: O(n) where n is the number of kids. We traverse the candies array twice, once to find the maximum and once to determine if each kid can have the greatest number of candies.
- Space complexity: O(n) for storing the result list.