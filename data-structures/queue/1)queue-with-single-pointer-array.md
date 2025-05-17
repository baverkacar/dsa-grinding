```java
public class QueueArraySinglePointer {
    int[]  queue;
    int rear;
    int size;

    public QueueArraySinglePointer(int size) {
        this.size = size;
        this.queue = new int[size];
        this.rear = -1; // Queue is initially empty
    }

    public void enqueue(int val) {
        if(isFull()) {
            return;
        }
        queue[++rear] = val;
    }

    public int dequeue() {
        if(isEmpty()) {
            return -1;
        }
        int dequeuedValue = queue[0];
        for (int i = 0; i < rear; i++) {
            queue[i] = queue[i + 1];
        }
        rear--;
        return dequeuedValue;
    }

    private boolean isFull() {
        return this.rear + 1 == this.size;
    }

    private boolean isEmpty() {
        return this.rear == -1;
    }
}
```

Time Complexity: O(n) for dequeue operation, O(1) for enqueue operation.
Space Complexity: O(n) for the queue array.