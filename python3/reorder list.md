# Reorder List

#### Problem Link: https://leetcode.com/problems/reorder-list/

## Approach 1

### Solution:

```py
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reorderList(self, head: Optional[ListNode]) -> None:
        """
        Do not return anything, modify head in-place instead.
        """
        slow = head
        fast = head.next

        while fast != None and fast.next != None:
            slow = slow.next
            fast = fast.next.next

        second_half = slow.next
        prev = slow.next = None

        while second_half:
            temp_node = second_half.next
            second_half.next = prev
            prev = second_half
            second_half = temp_node

        first, second = head, prev
        while second:
            temp1, temp2 = first.next, second.next
            first.next = second
            second.next = temp1
            first, second = temp1, temp2
```

### Time Complexity:

### Space Complexity:
