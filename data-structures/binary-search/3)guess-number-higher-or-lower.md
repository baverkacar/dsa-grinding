# Question Link
https://leetcode.com/problems/guess-number-higher-or-lower/

# Code

```java
/**
 * Forward declaration of guess API.
 * @param  num   your guess
 * @return 	     -1 if num is higher than the picked number
 *			      1 if num is lower than the picked number
 *               otherwise return 0
 * int guess(int num);
 */

public class Solution extends GuessGame {
    public int guessNumber(int n) {
        int start = 0;
        int end = n;
        int mid = 0;

        while (start <= end) {
            mid = start + (end - start) / 2;

            if(guess(mid) == -1) {
                end = mid - 1;
            }
            else if(guess(mid) == 1) {
                start = mid+1;
            }
            else if(guess(mid) == 0) {
                break;
            }
        }

        return mid;
    }
}
```

```go
func guessNumber(n int) int {
    start, end := 0, n
    mid := 0

    for start <= end {
        mid = start + (end - start) / 2

        if guess(mid) == -1 {
            end = mid - 1
        } else if guess(mid) == 1 {
            start = mid + 1
        } else if guess(mid) == 0 {
            break
        }
    }

    return mid
}
```

# Complexity Analysis
- Time complexity: O(log n) where n is the range of numbers from 1 to n. In each step, we reduce the search space by half.
- Space complexity: O(1) since we are using only a constant amount of extra space.
