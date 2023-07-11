# Product of Array Except Self

#### Problem Link: https://leetcode.com/problems/product-of-array-except-self

## Approach 1 []

### Solution:
* 

```py
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        n = len(nums)
        left_product, right_product, res = [1] * n, [1] * n, []

        for i in range(1, n):
            left_product[i] = left_product[i-1] * nums[i-1]
        for i in range(n-2, -1, -1):
            right_product[i] = right_product[i+1] * nums[i+1]
        for i in range(n):
            res.append(left_product[i] * right_product[i])
        return res
```

### Time Complexity:
* 

### Space Complexity:
* 

<br>

## Approach 2A [Using Prefix and Postfix Arrays]

### Solution:
* 

```py
# The edge cases are the beginning and end indexes of the prefix, postfix and res arrays so we handle that explicitly. 
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        n = len(nums)
        prefix, postfix, res = [1] * n, [1] * n, [1] * n

        prefix[0] = 1 * nums[0] 
        postfix[n-1] = nums[n-1] * 1

        for i in range(1, n):
            prefix[i] = prefix[i-1] * nums[i]
        for i in range(n-2, -1, -1):
            postfix[i] = postfix[i+1] * nums[i]

        res[0] = 1 * postfix[1]
        res[n-1] = prefix[n-2] * 1

        for i in range(1, n-1):
            res[i] = prefix[i-1] * postfix[i+1]
        return res
```

### Time Complexity:
* 

### Space Complexity:
* 

<br>

## Approach 2B [Optimizing 2A]

### Solution:
* 

```py
# The edge cases are the beginning and end indexes of the prefix, postfix and res arrays. 
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        n = len(nums)
        prefix, postfix, res = [1] * n, [1] * n, [1] * n

        prefix[0] = 1 * nums[0] 
        postfix[n-1] = nums[n-1] * 1

        for i in range(1, n):
            prefix[i] = prefix[i-1] * nums[i]
        for i in range(n-2, -1, -1):
            postfix[i] = postfix[i+1] * nums[i]

        res[0] = 1 * postfix[1]
        res[n-1] = prefix[n-2] * 1

        for i in range(1, n-1):
            res[i] = prefix[i-1] * postfix[i+1]
        return res
```

### Time Complexity:
* 

### Space Complexity:
* 