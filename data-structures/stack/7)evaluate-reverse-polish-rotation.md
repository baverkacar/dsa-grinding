# Question Link
https://leetcode.com/problems/evaluate-reverse-polish-notation/

# Code

Java:

```java []
class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> resultStack = new Stack();

        for (String s : tokens) {
            int valueOne;
            int valueTwo;
            if ( s.equals("+")) {
                valueOne = resultStack.pop();
                valueTwo = resultStack.pop();
                resultStack.push(valueTwo + valueOne);
            }
            else if(s.equals("*")) {
                valueOne = resultStack.pop();
                valueTwo = resultStack.pop();
                resultStack.push(valueTwo * valueOne);
            }
            else if(s.equals("/")) {
                valueOne = resultStack.pop();
                valueTwo = resultStack.pop();
                resultStack.push(valueTwo / valueOne);

            }
            else if(s.equals("-")) {
                valueOne = resultStack.pop();
                valueTwo = resultStack.pop();
                resultStack.push(valueTwo - valueOne);
            }else {
                resultStack.push(Integer.valueOf(s));
            }
        }
        return resultStack.peek();
    }
}
```

Golang:

```go []
func evalRPN(tokens []string) int {
	stack := make([]int, 0, len(tokens))

	pop := func() (v int) {
		v = stack[len(stack)-1]
		stack = stack[:len(stack)-1]
		return
	}

    for _, t := range tokens {
		switch t {
		case "+":
			stack = append(stack, pop()+pop())
		case "*":
			stack = append(stack, pop()*pop())
		case "-":
			v1,v2 := pop(),pop()
			stack = append(stack, v2-v1)
		case "/":
			v1,v2 := pop(),pop()
			stack = append(stack, v2/v1)
		default:
			v, _ := strconv.Atoi(t)
			stack = append(stack, v)
		}
	}

	return pop()
}
```

# Complexity Analysis
Time Complexity: O(n) - where n is the number of tokens in the input array. We traverse the array once, performing constant-time operations for each token.
Space Complexity: O(n) - in the worst case, we might store all operands in the stack.