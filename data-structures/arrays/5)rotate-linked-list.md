```java 
    public ListNode rotateRight(ListNode head, int k) {
        if (head == null || head.next == null) {
            return head;
        }
        int size = 1;    
        ListNode tempTail = head;
        while (tempTail.next != null) {
            size++;
            tempTail = tempTail.next;
        }

        tempTail.next = head;
        k = k % size;
        ListNode newTail = head;
        
        for (int i = 1; i < size - k; i++) {
            newTail = newTail.next;
        }
        ListNode newHead = newTail.next;
        newTail.next = null;
        return newHead;
    }
```

Time Complexity: O(n) – because we traverse the list once to find the length and then again to find the new tail.
Space Complexity: O(1) – because we only use a constant amount of extra space.


