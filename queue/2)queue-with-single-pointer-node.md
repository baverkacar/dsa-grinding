```java

public class QueueNodeSinglePointer {
    class Node {
        int val;
        Node next;

        Node(int val) {
            this.val = val;
            this.next = null;
        }
    }
    Node front;


    public void enqueue(int value) {
        Node newNode = new Node(value);
        if (front == null) {
            front = newNode;
        } else {
            Node current = front;
            while (current.next != null) {
                current = current.next;
            }
            current.next = newNode;
        }
    }

    public int dequeue() {
        if (front == null) {
            return -1; // or throw an exception
        }
        int dequeuedValue = front.val;
        front = front.next;
        return dequeuedValue;
    }

}

```

Time Complexity: O(n) for enqueue operation, O(1) for dequeue operation.
Space Complexity: O(n) for the queue linked list.