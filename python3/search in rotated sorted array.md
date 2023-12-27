# Search in Rotated Sorted Array

#### Problem Link: https://leetcode.com/problems/search-in-rotated-sorted-array/

## Approach 1

### Solution:

```py
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums)
        while left < right:

            mid = (left+right) // 2

            if target < nums[0] < nums[mid]:
                left = mid + 1
            elif target >= nums[0] > nums[mid]:
                right = mid
            elif nums[mid] < target:
                left = mid + 1
            elif nums[mid] > target:
                right = mid
            else:
                return mid
        return -1
```

### Time Complexity:

### Space Complexity:

<br>
