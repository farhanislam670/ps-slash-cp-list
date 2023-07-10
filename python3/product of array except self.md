# Product of Array Except Self

#### Problem Link: https://leetcode.com/problems/product-of-array-except-self

## Approach 1 

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
