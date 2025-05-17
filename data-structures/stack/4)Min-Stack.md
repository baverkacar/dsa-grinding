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

Time Complexity: O(1) for all operations (push, pop, top, getMin).
Space Complexity: O(n) for the stack linked list.