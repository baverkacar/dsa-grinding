```java
    public ListNode reverseList(ListNode head) {
    ListNode prev = null;
    ListNode curr = head;

    while (curr != null) {
        ListNode next = curr.next; // store the next node before breaking the link
        curr.next = prev;          // reverse the link
        prev = curr;               // move prev one step forward
        curr = next;               // move curr one step forward
    }

    return prev;
}

```


## Big-O Notation
Time Complexity: O(n) – because we traverse the list once.
Space Complexity: O(1) – because we only use a constant amount of extra space.

