// create java code block
```java
import java.util.LinkedList;

class Stack {

    class Node {
        int data;
        Node next;

        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }
    
    private Node top;   
    
    public Stack() {
        this.top = null;
    }   
    // Push an element onto the stack
    public void push(int data) {
        Node newNode = new node(data);
        newNode.next = top;
        top = newNode;
    }
    
    // pop an element from the stack
    public int pop() {
        if (isEmpty()) {
            throw new RuntimeException("Stack is empty");
        }
        int data = top.data;
        top = top.next;
        return data;
    }
    // Peek at the top element of the stack
    
    public int peek() {
        if (isEmpty()) {
            throw new RuntimeException("Stack is empty");
        }
        return top.data;
    }
}
```