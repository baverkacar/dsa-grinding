# Question Link
https://leetcode.com/problems/daily-temperatures/

# Code

```java
class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        int[] result = new int[temperatures.length];
        Deque<int[]> stack = new ArrayDeque<>(); 

        for(int i = 0; i < temperatures.length; i++) {
            while(!stack.isEmpty() && stack.peek()[0] < temperatures[i]) {
                result[stack.peek()[1]] = i - stack.pop()[1];
            }
            stack.push(new int[]{temperatures[i], i});
        }

        return result;
    }
}
```

```go

func dailyTemperatures(temperatures []int) []int {
	result := make([]int, len(temperatures))
	stack := []struct {
		temperature int
		index       int
	}{}

	for i, temp := range temperatures {
		for len(stack) > 0 && stack[len(stack)-1].temperature < temp {
			top := stack[len(stack)-1] // peek
			stack = stack[:len(stack)-1] // pop
			result[top.index] = i - top.index // calculate the number of days
		}
		stack = append(stack, struct {
			temperature int
			index       int
		}{temperature: temp, index: i})
	}
	return result
}

```

# Complexity Analysis
- Time complexity: O(n) where n is the number of days. Each temperature is pushed and popped from the stack at most once.
- Space complexity: O(n) in the worst case when the temperatures are in decreasing order, leading to all elements being stored in the stack. The result array also takes O(n) space.
