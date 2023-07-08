# Group Anagrams

#### Problem Link: https://leetcode.com/problems/group-anagrams/

## Approach 1 

### Solution:

```py
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        ans = collections.defaultdict(list)

        for s in strs:
            count = [0] * 26
            for c in s:
                count[ord(c) - ord("a")] += 1
            ans[tuple(count)].append(s)
        return list(ans.values())
```

### Time Complexity:

### Space Complexity:
<br>

## Approach 2

### Solution:

```py
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        result = {}

        for word in strs:
            sorted_word = ''.join(sorted(word))

            if sorted_word in result:
                result[sorted_word].append(word)
            else:
                result[sorted_word] = [word]
        
        return list(result.values())
```

### Time Complexity:

### Space Complexity: