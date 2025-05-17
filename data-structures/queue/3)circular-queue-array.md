```java 
public class CircularQueueArrayDoublePointer {
    // Non circular queue
    int[] queue;
    int front;
    int rear;
    int size;

    public CircularQueueArrayDoublePointer(int size) {
        this.size = size;
        this.queue = new int[size];
        this.front = 0; // Queue is initially empty
        this.rear = 0;
    }

    public void enqueue(int val) {
        if (isFull()){
            return;
        }
        queue[rear] = val;
        rear = (rear + 1) % size;
    }

    public int dequeue() {
        if (isEmpty()) {
            return -1;
        }
        int dequeuedVal = queue[front];
        queue[front] = 0; // set default val
        front = (front + 1) % size;
        return dequeuedVal;
    }

    private boolean isFull() {
        return (rear + 1) % size == front;
    }

    private boolean isEmpty() {
        return front == rear;
    }
}

```

Time Complexity: O(1) for both enqueue and dequeue operations.
Space Complexity: O(n) for the queue array.