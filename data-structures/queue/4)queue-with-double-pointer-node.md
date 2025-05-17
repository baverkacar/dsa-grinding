```java 
public class QueueNodeDoublePointer {
    class Node {
        int val;
        Node next;

        Node(int val) {
            this.val = val;
            this.next = null;
        }
    }
    Node front;
    Node rear;

    public void enqueue(int val) {
        Node newNode = new Node(val);
        if (front == null) {
            front = newNode;
            rear = newNode;
        } else {
            rear.next = newNode;
            rear = newNode;
        }
    }

    public int dequeue() {
        if (front == null) {
            return -1; // or throw an exception
        }
        int dequeuedValue = front.val;
        front = front.next;
        if (front == null) { // If the queue is now empty, set rear to null as well
            rear = null;
        }
        return dequeuedValue;
    }
}

```

Time Complexity: O(1) for both enqueue and dequeue operations.
Space Complexity: O(n) for the queue linked list.