# Reverse Linked List

#### Problem Link: https://leetcode.com/problems/reverse-linked-list/

## Approach 1

### Solution:

- It's quite simple, initialize `previous` to `None` as this will now be the `None` that the last node of the reversed list points towards.
- There's two steps:
  1. You want the current node to point towards the previous node. [Reversing the link]. So you simply do a
     > `current.next = previous`
  2. You then update `previous` and `current` to point towards their respective next nodes in order to just repeat this process until you reach the last node (`while current`), where current will be referencing the original `None` that was present in the original linked list. This is done by a simple
     - `previous = previous.next`
     - `current = current.next`
  - But you don't really have a `previous.next` here. So you simply just point it towards `current` node by
    > `previous = current`
  - The real problem is with `current = current.next`. You've done `current.next = previous` to reverse the link in the previous step, so you've lost the initial node that `current.next` was initially pointing towards. So you have to keep a reference to that by creating a temporary variable to point towards the node you want to point `current` towards in the ext iteration. You do this simply by:
    > `temp = current.next`
  - So the previous `current = current.next` now becomes:
    > `current = temp`

```py
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        previous = None
        current = head

        while current:
           temp = current.next
           current.next = previous
           previous = current
           current = temp
        return prev_node
```

### Time Complexity:

> The time complexity of this code is `O(n)`, where `n` is the number of nodes in the linked list.

- The `while` loop iterates through all the nodes in the linked list once, reversing the direction of the next pointers.

### Space Complexity:

> The space complexity of this code is `O(1)`.

- It uses a constant amount of extra space, regardless of the size of the input linked list. The variables previous, current, and temp are used to perform the reversal in-place, and their memory usage does not depend on the input size.
