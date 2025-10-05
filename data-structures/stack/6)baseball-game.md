# Question Link
https://leetcode.com/problems/baseball-game/

# Code

Java:

```java []
class Solution {
    public int calPoints(String[] operations) {
        Stack<Integer> stack = new Stack<>();
        int score = 0;

        for (String s : operations) {
            if (s.equals("+")) {
                int newScore = stack.get(stack.size() - 1) + stack.get(stack.size() - 2);
                score += newScore;
                stack.push(newScore);

            }
            else if(s.equals("D")) {
                int doubledPrevScode = stack.peek() * 2;
                score += doubledPrevScode;
                stack.push(doubledPrevScode);
            }
            else if(s.equals("C")) {
                score -= stack.pop();
            }
            else {
                score += Integer.valueOf(s);
                stack.push(Integer.valueOf(s));
            }
        }
        return score;
    }
}
```

Golang:

```go []
func calPoints(operations []string) int {
	var stack []int
	score := 0

	for _, operation := range operations {
		if operation == "+" {
			newScore := stack[len(stack)-1] + stack[len(stack)-2]
			score += newScore
			stack = append(stack, newScore)
		} else if operation == "D" {
			doubled := stack[len(stack)-1] * 2
			score += doubled
			stack = append(stack, doubled)
		} else if operation == "C" {
			score -= stack[len(stack)-1]
			stack = stack[:len(stack)-1] // pop last score
		} else {
			// string to int
			val, _ := strconv.Atoi(operation)
			score += val
			stack = append(stack, val)
		}
	}
	return score
}
```


# Complexity
- Time complexity: O(n)
  We traverse the operations list once, ensuring each operation is processed at most once.
- Space complexity: O(n)
  In the worst case, we might store all scores in the stack.