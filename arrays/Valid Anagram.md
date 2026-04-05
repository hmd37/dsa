# Valid Anagram

Given two strings `s` and `t`, return `true` if the two strings are anagrams of each other, otherwise return `false`.

An anagram is a string that contains the exact same characters as another string, but the order of the characters can be different.

### Example 1:
```
Input: s = "racecar", t = "carrace"
Output: true
```

### Solution:
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        hash_s, hash_t = {}, {}

        for i in range(len(s)):
            hash_s[s[i]] = hash_s.get(s[i], 0) + 1
            hash_t[t[i]] = hash_t.get(t[i], 0) + 1

        for s in hash_s:
            if hash_t.get(s) != hash_s[s]:
                return False
        
        return True
```
