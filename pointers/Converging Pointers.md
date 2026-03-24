## Converging Pointers

The **converging pointers technique** places two pointers at opposite ends of an array and moves them toward each other based on specific conditions. It’s commonly used for problems involving comparisons, finding pairs, or narrowing search spaces in a sorted array.

### Example: Two-Sum in a Sorted Array

**Task:** Given a sorted array and a target sum, find two numbers that add up to the target.

```python
left = 0
right = len(nums) - 1

while left < right:
    current_sum = nums[left] + nums[right]
    
    if current_sum == target:
        return [left, right]
    elif current_sum < target:
        left += 1
    else:
        right -= 1
```

### How it works

1. **Initialize pointers**  
   Set `left` at the start and `right` at the end of the array.

2. **Evaluate and adjust**
   - If `nums[left] + nums[right]` equals the target → solution found.
   - If the sum is too small → move `left` to the right (increase sum).
   - If the sum is too large → move `right` to the left (decrease sum).

3. **Stop condition**  
   Continue until the pointers meet or a valid pair is found.

### Complexity

Because the array is sorted, each pointer move eliminates part of the search space.  
Each element is visited at most once, resulting in:

- **Time Complexity:** `O(n)`
- **Space Complexity:** `O(1)`

## The Mirror of Words

In the temple's Hall of Reflections, the apprentices are tasked with identifying "perfect phrases" that read the same forward and backward when viewed in the mirror of the mind. The challenge? Ignore any distractions like punctuation or spaces.

Write a function to determine if a given string is a palindrome, ignoring non-alphanumeric characters and considering case insensitivity. If it is a palindrome, return `"Palindrome!"`. Otherwise, return `"Not a Palindrome!"`.

### Example Input:
s = "A man, a plan, a canal: Panama"

### Example Output:
"Palindrome!"

### Solution
```python
class Solution:
    def is_palindrome(self, s: str) -> str:
        left, right = 0, len(s) - 1

        while left < right:
            if not s[left].isalnum():
                left += 1
                continue
            
            if not s[right].isalnum():
                right -= 1
                continue

            if s[left].lower() != s[right].lower():
                return "Not a Palindrome!"
            
            left += 1
            right -= 1

        return "Palindrome!"
```
