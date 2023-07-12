# Two Sum II - Input Array Is Sorted

#### Problem Link: https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/


## Approach 1

### Solution:

```py
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        l = 0
        r = len(numbers) - 1
        while l < r:
            if numbers[l] + numbers[r] == target:
                return [l+1, r+1]
            elif numbers[r] > target and numbers[l] + numbers[r] > target:
                r -= 1
            elif numbers[l] + numbers[r] > target:
                r -= 1
            else:
                l += 1  
```

### Time Complexity:

### Space Complexity:

<br>

## Approach 2A [Evolving my 1]

### Solution:

```py
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        l = 0
        r = len(numbers) - 1
        while l < r:
            if numbers[l] + numbers[r] == target:
                return [l+1, r+1]
            elif numbers[l] + numbers[r] > target:
                r -= 1
            elif numbers[l] + numbers[r] < target:
                l += 1  
```

### Time Complexity:

### Space Complexity:

<br>

## Approach 2B [GOATED]

### Solution:

```py
class Solution:
  def twoSum(self, numbers: List[int], target: int) -> List[int]:

    left, right = 0, len(numbers) - 1
    while left < right:
      total = numbers[left] + numbers[right]
      if total < target:
        left += 1
      elif total > target:
        right -= 1
      else:
        return [left+1, right+1]
    return []
```

### Time Complexity:

### Space Complexity:

