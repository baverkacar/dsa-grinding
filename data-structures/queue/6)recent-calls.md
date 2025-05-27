java code block
```java

class RecentCounter {
    private Deque<Integer> queue;

    public RecentCounter() {
        this.queue = new ArrayDeque<>();
    }
    
    public int ping(int t) {
        while(!queue.isEmpty() && queue.peekFirst() < t - 3000) {
            queue.poll();
        }
        queue.offerLast(t);
        return queue.size();
    }
}
```



