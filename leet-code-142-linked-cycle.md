> Given a linked list, return the node where the cycle begins. If there is no cycle, return null.

> Note: Do not modify the linked list.

> ##answer
```
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def detectCycle(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if head is None or head.next is None:
            return None
        slow = fast = head
        while fast and fast.next:
            slow, fast = slow.next, fast.next.next
            if slow == fast:
                break
        if slow != fast:
            return None
        fast = head
        while fast != slow:
            fast, slow = fast.next, slow.next
        return fast
```
