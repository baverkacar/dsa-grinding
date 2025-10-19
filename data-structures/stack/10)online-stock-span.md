# Question Link

https://leetcode.com/problems/online-stock-span/description/
# Code

Java:

```java
class StockSpanner {
    
    Deque<int[]> stack;
    public StockSpanner() {
        this.stack = new ArrayDeque<>();
    }
    
    public int next(int price) {
        int span = 1;

        if(stack.isEmpty()) {
            stack.push(new int[]{price,span});
            return span;
        }

        while(!stack.isEmpty() && stack.peek()[0] <= price) {
            span += stack.pop()[1];
        }

        stack.push(new int[]{price,span});

        return span;
    }
}
```

Golang:

```go
type StockSpanner struct {
    stack [][]int
}

func Constructor() StockSpanner {
    return StockSpanner{
        stack: [][]int{},
    }
}

func (this *StockSpanner) Next(price int) int {
    span := 1

    for len(this.stack) > 0 && this.stack[len(this.stack)-1][0] <= price {
        span += this.stack[len(this.stack)-1][1]
        this.stack = this.stack[:len(this.stack)-1] // pop
    }

    this.stack = append(this.stack, []int{price, span})

    return span
}
```

# Complexity Analysis
- Time complexity: O(1) amortized time for each `next` call. Each price is pushed and popped from the stack at most once.
- Space complexity: O(n) where n is the number of calls to `next`, in the worst case when prices are in decreasing order, leading to all elements being stored in the stack.

