```java
    public boolean hasCycle(ListNode head) {
        if (head == null || head.next == null) {
            return false;
        } 

        ListNode slow = head;
        ListNode fast = head;

        while(fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) {
                return true;
            }
        }

        return false;
    }
```

## Big-O Notation
- Time Complexity: O(n) – because we traverse the list once.
- Space Complexity: O(1) – because we only use a constant amount of extra space.
