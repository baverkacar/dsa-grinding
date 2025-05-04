// create java code block
```java 

class Stack {
    private int maxSize;
    private int[] stackArray;
    private int top;

    public Stack(int size) {
        this.maxSize = size;
        this.stackArray = new int[maxSize];
        this.top = -1; // Stack is initially empty
    }

    // Push an element onto the stack
    public void push(int value) {
        if (top == maxSize - 1) {
            throw new RuntimeException("Stack is full");
        }
        stackArray[++top] = value;
    }

    // Pop an element from the stack
    public int pop() {
        if (isEmpty()) {
            throw new RuntimeException("Stack is empty");
        }
        return stackArray[top--];
    }

    // Peek at the top element of the stack

    public int peek() {
        if (isEmpty()) {
            throw new RuntimeException("Stack is empty");
        }
        return stackArray[top];
    }
}
```