# Merge Two Sorted Lists

#### Problem Link: https://leetcode.com/problems/merge-two-sorted-lists/

## Approach 1 [Not Acceptable]

### Solution:

- The first thing to note is that this solution is unacceptable.
  - > The list should be made by splicing together the nodes of the first two lists.
  - Therefore, this approach of storing the solution in a list and then subsequently inserting it into a linked list is wrong.
  - However, it's a pretty good first step (for me) to understand the solution.
-

```py
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        linked_list = ListNode()
        dummy_head = linked_list
        res = []
        x = list1
        y = list2
        while x != None and y != None:
            if x.val <= y.val:
                res.append(x.val)
                x = x.next
            else:
                res.append(y.val)
                y = y.next

        while x is not None:
            res.append(x.val)
            x = x.next
        while y is not None:
            res.append(y.val)
            y = y.next

        # If the list is empty i.e, the linked list has no nodes.
        if not res:
            return None

        # Convert the list to a linked list by adding `ListNode`s for each element in the list.
        for i in range(len(res)):
            dummy_head.val = res[i]
            if i == len(res) - 1:
                dummy_head.next = None
            else:
                dummy_head.next = ListNode()
                dummy_head = dummy_head.next

        # Return the head of the linked_list that you constructed.
        return linked_list
```

### Time Complexity:

### Space Complexity:

<br>

## Approach 2

### Solution:

```py
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        dummy_head = result = ListNode()

        x = list1
        y = list2

        while x and y:
            if x.val <= y.val:
                dummy_head.next = x
                x = x.next
            else:
                dummy_head.next = y
                y = y.next

            dummy_head = dummy_head.next

        if x:
            dummy_head.next = x
        else:
            dummy_head.next = y

        return result.next
```

### Time Complexity:

### Space Complexity:
