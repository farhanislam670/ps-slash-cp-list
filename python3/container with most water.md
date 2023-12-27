# Container With Most Water

#### Problem Link: https://leetcode.com/problems/container-with-most-water/

## Approach 1A

### Solution:

- The solution starts by initializing two pointers.
- Now where do I initialize the pointers?
  - Since I want to find the maximum area, wouldn't the most sensible thing to do is to start at both ends and then keep converging to the middle?
  - That's precisely what we do.
    - Inialize `left = 0` and `right = len(nums) - 1`.

```py
class Solution:
    def maxArea(self, height: List[int]) -> int:
        left, right, max_area = 0, len(height) - 1, 0

        while left < right:
            max_area = max((max_area), (right - left) * min(height[right], height[left]))
            if (height[right] > height[left]):
                left += 1
            elif height[right] <= height[left]:
                right -= 1

        return max_area
```

### Time Complexity:

> The time complexity of the given code is `O(n)`, where `n` is the number of elements in the `height` list.

### Space Complexity:

> The space complexity of the given code is `O(1)`.

<br>

#

#### Problem Link:

## Approach 1B [Runtime Optimization]

### Solution:

```py
class Solution:
    def maxArea(self, height: List[int]) -> int:
        left, right = 0, len(height) - 1
        max_area = 0
        max_height = max(height)

        while left < right:

            print("LeftIndex: ", left, "    RightIndex: ", right, "   LeftVal: ", height[left], "    RightVal: ", height[right], "    MaxArea: ", max_area)  # For debugging purpose.

            max_area = max((max_area), (right - left) * min(height[right], height[left]))
            if (height[right] > height[left]):
                left += 1
            elif height[right] <= height[left]:
                right -= 1

            if (right-left) * max_height <= max_area: # The optimization.
                break

        return max_area
```

### Time Complexity:

> The time complexity of the given code is `O(n)`, where `n` is the number of elements in the `height` list.

### Space Complexity:

> The space complexity of the given code is `O(1)`.
