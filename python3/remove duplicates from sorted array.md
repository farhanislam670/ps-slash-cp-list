# Remove Duplicates from Sorted Array

#### Problem Link: https://leetcode.com/problems/remove-duplicates-from-sorted-array/

## Approach 1 [Brute Force]

### Solution:

- The problem requires us to return how many distinct elements are in the array all the while making

```py
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        n = len(nums)
        my_set = set()
        i = 0
        for num in nums:
            my_set.add(num)
        sorted_list = sorted(my_set)
        for num in sorted_list:
            nums[i] = num
            i += 1
        return len(sorted_list)
```

### Time Complexity:

### Space Complexity:

<br>

## Approach 1

### Solution:

```py
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        nums[:] = sorted(set(nums))
        return len(nums)
```

### Time Complexity:

### Space Complexity:
