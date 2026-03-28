# Frequency-Based Sliding Windows
So far, we’ve looked at summation-based sliding windows, where the state of the window is tracked by a single variable (the sum). Another common pattern is frequency-based sliding windows, where we track how many times each element (or character) appears in the window. Some examples include:

* Finding the longest substring with unique characters.
* Locating subarrays that have at most k distinct elements.
* Solving anagrams or frequency-based search problems.
Let's start with a classic example of finding the longest substring with unique characters.

Task: given a string, find the length of the longest substring in which all characters are unique.

For example, given the string "faangfaang", the longest substring with unique characters is "angf", which has a length of 4.

We can solve this with a dynamic sliding window and a set to keep track of the characters in the window. Often you would use a hash map to keep track of the frequency of each character in the window, but in this problem, we only need to know if a character is in the window or not. The general approach is:

1. "Expand" - move the right pointer and add the character to the set.
2. "Shrink" - if the character is already in the set, move the left pointer to the right until the character is no longer in the set.
3. At any moment, after the "Shrink" step, the set will contain only unique characters.
4. When expanding, update the maximum length of the substring with unique characters.

```python
def longest_unique_substring(s):
    char_set = set()
    left = 0
    max_len = 0

    for right in range(len(s)):
        # If the character at 'right' is already in our set,
        # remove chars from the left until it's safe to add the new one
        while s[right] in char_set:
            char_set.remove(s[left])
            left += 1

        # Add the new character and update max_len
        char_set.add(s[right])
        max_len = max(max_len, right - left + 1)

    return max_len

# Example usage
s = "abcabcbb"
print(longest_unique_substring(s))  # Output: 3 (e.g., "abc")
```

# The Calligraphy Contest
The apprentices of the Faangshui Temple are preparing for the annual Calligraphy Contest, where they must write elegant scrolls with only two different brushstrokes.

Each apprentice tries different writing styles, but some of their scrolls contain too many variations. The goal is to find the longest continuous section of a scroll that contains at most two distinct brushstrokes.

Your task is to write a function that, given a string representing an apprentice’s scroll, finds the length of the longest contiguous substring that contains at most two distinct characters.

### Example Input:
`scroll = "aabacbebebe"`

### Example Output:
`6`
### Explanation:
The longest substring with at most two distinct characters is "bebebe", which has a length of 6.

### Solution
```python
class Solution:
    def longest_two_stroke_scroll(self, scroll):
        left = 0
        char_count = {}
        max_length = 0

        for right in range(len(scroll)):
            # Add current character
            char = scroll[right]
            char_count[char] = char_count.get(char, 0) + 1

            # If more than 2 distinct characters → shrink window
            while len(char_count) > 2:
                left_char = scroll[left]
                char_count[left_char] -= 1

                if char_count[left_char] == 0:
                    del char_count[left_char]

                left += 1

            max_length = max(max_length, right - left + 1)

        return max_length
```
