# Add Two Numbers

#### Problem Link: https://leetcode.com/problems/add-two-numbers/

## Approach 1 [Naive Solution]

### Solution:

- This is a really elementary solution that doesn't leverage your understanding of pointers. The code is self-explanatory.

```py
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        num1_pointer, num2_pointer, num1, num2 = l1, l2, 0, 0

        i = 1
        while num1_pointer:
            num1 = num1 + num1_pointer.val * i
            i = i*10
            num1_pointer = num1_pointer.next

        i = 1
        while num2_pointer:
            num2 = num2 + num2_pointer.val * i
            i = i*10
            num2_pointer = num2_pointer.next

        result = str(num1+num2)

        head = ListNode()
        current = head
        for i in range(len(result) - 1, -1, -1):
            current.next = ListNode(result[i])
            current = current.next

        return head.next
```

### Time Complexity:

### Space Complexity:

<br>

## Approach B [Leveraging Linked List Properties]

### Solution:

```py
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        dummy = ListNode()
        cur = dummy

        carry = 0
        while l1 or l2 or carry:
            v1 = l1.val if l1 else 0
            v2 = l2.val if l2 else 0

            # new digit
            val = v1 + v2 + carry
            carry = val // 10
            val = val % 10
            cur.next = ListNode(val)

            # update ptrs
            cur = cur.next
            l1 = l1.next if l1 else None
            l2 = l2.next if l2 else None

        return dummy.next
```

### Time Complexity:

### Space Complexity:
