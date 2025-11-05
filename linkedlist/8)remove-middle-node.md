# Question Link

https://leetcode.com/problems/remove-middle-node-of-linked-list/

# Code

```java
class Solution {
    public ListNode deleteMiddle(ListNode head) {
        if (head == null || head.next == null) {
            return null;
        }

        ListNode slow = new ListNode();
        ListNode fast = head;
        ListNode slow.next = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        
        slow.next = slow.next.next;
        return head;
    }
}
```

# Complexity Analysis
- Time Complexity: O(n), where n is the number of nodes in the linked list. We traverse the list once to find the middle node.
- Space Complexity: O(1), as we are using only a constant amount of extra space for pointers.

