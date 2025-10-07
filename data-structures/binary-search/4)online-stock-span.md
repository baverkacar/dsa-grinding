# Question Link
https://leetcode.com/problems/online-stock-span/

# Code

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

```go
package main

type StockSpanner struct {
	stack []pair
}

type pair struct {
	price int
	span  int
}

func Constructor() StockSpanner {
	return StockSpanner{stack: []pair{}}
}

func (this *StockSpanner) Next(price int) int {
	span := 1

	for len(this.stack) > 0 && this.stack[len(this.stack)-1].price <= price {
		top := this.stack[len(this.stack)-1]
		this.stack = this.stack[:len(this.stack)-1] // pop
		span += top.span
	}

	this.stack = append(this.stack, pair{price, span})
	return span
}
```

# Complexity Analysis
- Time complexity: O(1) on average for each call to next(). Each price is pushed and popped from the stack at most once.
- Space complexity: O(n) in the worst case when prices are in decreasing order, leading to all elements being stored in the stack.
