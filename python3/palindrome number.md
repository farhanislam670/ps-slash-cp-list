# Find the Prefix Common Array of Two Arrays

#### Problem Link: https://leetcode.com/problems/find-the-prefix-common-array-of-two-arrays/  


## Approach 1

### Solution:
* Nothing much to say here. Conver `x` into a string and then use two pointers to converge to the center of the `x`.

```py
class Solution:
    def isPalindrome(self, x: int) -> bool:
        num_string = str(x)
        l = 0
        r = len(num_string)-1
        while l < r:
            if num_string[l] != num_string[r]:
                return False
            l += 1
            r -= 1
        return True
```

### Time Complexity:
* The time complexity of this code is `O(n)`, where `n` is the number of digits in the given integer `x`

### Space Complexity:
* The space complexity of this code is `O(1)` because it uses a constant amount of extra space. 
<br>

## Approach 2

### Solution:
* A much cleaner approach (visually) where you compare the original string to its reverse.

```py
class Solution:
    def isPalindrome(self, x: int) -> bool:
        return True if str(x) == str(x)[::-1] else False
```

### Time Complexity:
* The time complexity of this code is `O(n)`, where `n` is the number of digits in the given integer `x`.
* The solution first converts the integer `x` into a string using `str(x)`, which takes `O(n)` time complexity, where `n` is the number of digits in `x`.
* Then, it creates a reversed version of the string using the slicing operation `str(x)[::-1]`. This operation also takes `O(n)` time complexity because it needs to iterate through all the characters in the string.
* Finally, the code compares the original string with the reversed string using the `==` operator, which compares the characters of the two strings in a pairwise manner. This comparison takes `O(n)` time complexity since it needs to compare each character.

### Space Complexity:
* The space complexity of this code is `O(n)`, where `n` is the number of digits in the given integer `x`.
* The creation of `str(x)` and `str(x)[::-1]` both take `O(n)` space.



