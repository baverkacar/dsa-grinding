```java
class MinStack {
    class Node {
        Node next;
        int data;
        int minVal;
        
        public Node(int val, int min) {
            this.data = val;
            this.next = null;
            this.minVal = min;
        }
    }

    Node top;

    public MinStack() {
        this.top = null;
    }
    
    public void push(int val) {
        int min = 0;
        if (top == null) {
            min = val;
        } else {
            min = Math.min(val, top.minVal);
        }
        Node newNode = new Node(val, min);
        newNode.next = top;
        top = newNode;
    }
    
    public void pop() {
        if(top == null) {
            return;
        }
        top = top.next;
    }
    
    public int top() {
        return top.data;
    }
    
    public int getMin() {
        return top.minVal;
    }
}
```
Golang:
```go
package main

import "math"

type MinStack struct {
	top *MinStackNode
}

type MinStackNode struct {
	next   *MinStackNode
	data   int
	minVal int
}

func NewMinStack() *MinStack {
	return &MinStack{
		top: nil,
	}
}

func (s *MinStack) Push(data int) {
	var min int

	if s.top == nil {
		min = data
	} else {
		min = int(math.Min(float64(data), float64(s.top.minVal)))
	}

	newNode := &MinStackNode{data: data, minVal: min, next: s.top}

	s.top = newNode
}

func (s *MinStack) Pop() int {
	if s.top == nil {
		panic("Stack is empty")
	}
	val := s.top.data
	s.top = s.top.next
	return val
}

func (s *MinStack) GetMin() int {
	if s.top == nil {
		panic("Stack is empty")
	}
	return s.top.minVal
}

```

# Complexity Analysis

Time Complexity: O(1) for all operations (push, pop, top, getMin).
Space Complexity: O(n) for the stack linked list.