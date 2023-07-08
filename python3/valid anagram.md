# Valid Anagram

#### Problem Link: https://leetcode.com/problems/valid-anagram/

## Approach 1 

### Solution:
* If the lengths do not match, immediately return false.
* Sort both the strings. When sorted, if they match, they are anagrams.

```py
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        sSorted = sorted (s)
        tSorted = sorted (t)
        if sSorted == tSorted:
            return True
        return False
```

### Time Complexity:
* The time complexity of this code is `O(nlog(n))`, where `n` is the length of the input strings `s` and `t`.
* Sorting the strings `s` and `t` using the `sorted()` function has a time complexity of `O(nlog(n))` for each string. Sorting a string of length `n` takes `O(nlog(n))` time complexity.
* The comparison sSorted == tSorted takes O(n) time complexity. It compares each character in the sorted strings, which requires iterating over both strings once.

### Space Complexity:
* The space complexity of the code is `O(n)`.
* The `sorted()` function creates new lists with the sorted characters from the input strings `s` and `t`. The space required for each sorted string is proportional to the length of the input string, which is `O(n)`.
* The variables `sSorted` and `tSorted` each require `O(n)` space to store the sorted strings.
<br>

## Approach 2 

### Solution:
* Instead of sorting the strings, create dictionaries that store their characters and their respective frequencies. If they match, they're anagrams.

```py
class Solution:
    from collections import Counter
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        if Counter(s) == Counter(t):
            return True
        return False
```

### Time Complexity:
* The time complexity of this code is `O(n)`, where `n` is the length of either string `s` or `t` [It doesn;t matter which, since we are checking their length in the beginning anyway]. 


### Space Complexity:
* The space complexity is also `O(n)` due to the creation of the `Counter` objects.
* `Counter(s)` and `Counter(t)` create `Counter` objects that store the counts of characters in the strings. The space required for each `Counter` object is proportional to the number of unique characters, which can be at most the length of the input strings i.e., `n`.