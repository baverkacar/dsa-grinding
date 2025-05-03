```java

    public ListNode middleNode(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;

    }

```

## Big-O Notation
Time Complexity: O(n) – because we traverse the list once.
Space Complexity: O(1) – because we only use a constant amount of extra space.