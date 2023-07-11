# Ransom Note

#### Problem Link: https://leetcode.com/problems/ransom-note/

## Approach 1 

### Solution:
* Since the ransomNote is made from the magazine, the magazine should contain a frequency equal or greater for each character in the ransomNote.

```py
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        dict_ransom_note = collections.Counter(ransomNote)
        dict_magazine = collections.Counter(magazine)
        for key, value in dict_ransom_note.items():
            if key not in dict_magazine.keys():
                 return False
            elif value > dict_magazine[key]:
                    return False
        return True
```

### Time Complexity:
> The time complexity of the provided code is `O(N+M)`, where `N` is the length of the `ransomNote` string and `M` is the length of the `magazine` string.

### Space Complexity:
> The space complexity of the provided code is also `O(N+M)`
