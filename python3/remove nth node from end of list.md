# Remove Nth Node From End of List

#### Problem Link: https://leetcode.com/problems/remove-nth-node-from-end-of-list/

## Approach 1

### Solution:

```py
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        count = 0
        nodeCounter, temp = head, head

        while nodeCounter:
            count += 1
            nodeCounter = nodeCounter.next

        for i in range(count - n - 1):
            temp = temp.next

        if n != count:
            if temp.next.next:
                temp.next = temp.next.next
            else:
                temp.next = None
        else:
            return head.next

        return head
```

### Time Complexity:

### Space Complexity:

<br>
