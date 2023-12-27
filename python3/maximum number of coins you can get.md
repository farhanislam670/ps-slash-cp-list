# Maximum Number of Coins You Can Get

#### Problem Link: https://leetcode.com/problems/maximum-number-of-coins-you-can-get/

## Approach 1

### Solution:

<p align="center" width="100%">
    <img src="images/maximum number of coins you can get 1.png">
</p>
<br>

- The intuition is that I will always pick the second highest number of coins in any triplet.

```py
class Solution:
    def maxCoins(self, piles: List[int]) -> int:
        piles.sort()
        sum,i = 0, len(piles)-2
        num_piles = (len(piles)//3)
        while num_piles > 0:
                sum += piles[i]
                i -= 2
                num_piles -= 1
        return sum
```

### Time Complexity:

> The time complexity of this code is `O(Nlog(N))`, where `N` is the length of the piles list.

- Note: I'm using `N` here because the length of the piles is here is denoted as `3n` so it would cause a confusion.
- The first operation, `piles.sort()`, has a time complexity of `O(Nlog(N))`.
- The while loop iterates `num_piles` times, where `num_piles` is equal to `len(piles)//3` i.e., it loops `n` times as there are `3n` piles. Here, `n = num_piles`

### Space Complexity:

> The space complexity of this code is `O(1)`, which means it uses a constant amount of additional space that does not depend on the input size.

<br>
