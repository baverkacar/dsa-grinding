# Question Link
https://leetcode.com/problems/sqrtx/

# Code

```java

class Solution {
    public int mySqrt(int x) {
        int start = 0;
        int end = x;

        while (start <= end) {
            int mid = start + (end - start) / 2;
            long square = (long) mid * mid; 

            if (square > x) {
                end = mid - 1;
            } else if (square < x) {
                start = mid + 1;
            } else {
                return mid;
            }
        }
        return end; 
    }
}

```

```go
func mySqrt(x int) int {
    start, end := 0, x

    for start <= end {
        mid := start + (end - start) / 2
        square := mid * mid

        if square > x {
            end = mid - 1
        } else if square < x {
            start = mid + 1
        } else {
            return mid
        }
    }
    return end 
}
```

# Complexity Analysis
- Time complexity: O(log x) where x is the input number. The binary search algorithm reduces the search space by half in each iteration.
- Space complexity: O(1) as we are using a constant amount of space for variables.
