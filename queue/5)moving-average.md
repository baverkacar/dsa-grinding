java code block
```java 

class MovingAverage {
    double total = 0;
    Deque<Integer> queue = new ArrayDeque<>();
    int windowSize;
    public MovingAverage(int size) {
        this.windowSize = size;
    }
    
    public double next(int val) {
        if (queue.size() == windowSize) {
            total -= queue.poll();  
        }
        queue.add(val);
        total += val;
        
        return total / queue.size(); 
    }
}
```

Time Complexity: O(1) for each call to `next()`.
Space Complexity: O(n) for the queue.