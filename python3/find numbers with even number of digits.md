# Find Numbers with Even Number of Digits

#### Problem Link: https://leetcode.com/problems/find-numbers-with-even-number-of-digits/

## Approach 1 [Brute Force]

### Solution:
* For each element in the list, initialise a counter that counts how many times dividing the number by 10 makes that number become 0.
* Notice that `num //= 10` denotes floor division which means that once the the last digit of a `num` has been reached, the next step will make it turn to 0, thereby avoiding an infinite loop.

```py
class Solution:
    def findNumbers(self, nums: List[int]) -> int:
        res = 0
        for num in nums: #O(n)
            cnt = 0
            while num > 0: #O(d)
                num //= 10
                cnt += 1
            if(cnt%2 == 0):
                res += 1
        return res
```

### Time Complexity:
* The time complexity of this code is `O(n*d)`, where `n` is the number of elements in the `nums` list, and `d` is the average number of digits in an element of `nums`.

### Space Complexity:
* The space complexity of this solution is `O(1)`.

<br>

## Approach 1B [Optimizing 1A]

### Solution:
* Instead of counting the number of digits in each number present in the list, just convert all of the numbers to strings and simply count the number of characters in each string.

```py
class Solution:
    def findNumbers(self, nums: List[int]) -> int:
        res = 0
        nums = [str(x) for x in nums]
        for num in nums:
            if len(num)%2 == 0:
                res +=1 
        return res
```

### Time Complexity:
* The time complexity of this code is `O(n)`, where n is the number of elements in the `nums` list.
* Converting each of the numbers in the list to the strings takes `O(1)` time, and traversing the entire list takes `O(n)` time.
* Again, traversing the entire list takes `O(n)` time.


### Space Complexity:
* The space complexity of this code is `O(1)`.


