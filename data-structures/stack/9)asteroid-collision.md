# Question Link
https://leetcode.com/problems/asteroid-collision/

# Code

```java

class Solution {
    public int[] asteroidCollision(int[] asteroids) {
        Deque<Integer> stack = new ArrayDeque<>();

        for (int asteroid : asteroids) {
            boolean isAsteroidAlive = true;
            while (!stack.isEmpty() && stack.peek() > 0 && isAsteroidAlive && asteroid < 0) {
                if (-asteroid > stack.peek()) {
                    stack.pop();
                    continue;
                } else if (stack.peek() == -asteroid) {
                    stack.pop();
                }
                isAsteroidAlive = false;
            }
            if (isAsteroidAlive) {
                stack.push(asteroid);
            }
        }

        int[] intArray = new int[stack.size()];
        int i = 0;
        Iterator<Integer> iterator = stack.descendingIterator(); // bottom to top
        while (iterator.hasNext()) {
            intArray[i++] = iterator.next();
        }
        return intArray;
    }
}
```

```go
func asteroidCollision(asteroids []int) []int {
	var stack []int

	for _, asteroid := range asteroids {
		isAsteroidAlive := true
		for (isAsteroidAlive && asteroid < 0 && len(stack) > 0 && stack[len(stack)-1] > 0) {
			if(-asteroid > stack[len(stack) - 1]) {
				stack = stack[:len(stack)-1]
				continue
			} else if(-asteroid == stack[len(stack) - 1]) {
				stack = stack[:len(stack)-1]
			}
			isAsteroidAlive = false
		}
		if isAsteroidAlive {
			stack = append(stack, asteroid)
		}
	}
	return stack
}
```
# Complexity Analysis
- Time complexity: O(n) where n is the number of asteroids. Each asteroid is pushed and popped from the stack at most once.
- Space complexity: O(n) in the worst case when all asteroids are moving in the same direction, leading to all elements being stored in the stack. The result array also takes O(n) space.