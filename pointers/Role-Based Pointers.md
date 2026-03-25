# Role-Based Pointers
Role-Based Pointers is a technique where each pointer has a specific task or role, allowing you to address different parts of a problem at the same time. Unlike other pointer techniques where pointers often depend on one another, in this approach each pointer operates independently based on its assigned role.

### Example: Rearranging Even/Odd Elements by Index
Task: rearrange an array so that even indices hold even numbers and odd indices hold odd numbers. Assume the array has an equal number of even and odd elements.

```
nums = [3, 1, 2, 4]
result = [2, 3, 4, 1]
```

### Solution Using Role-Based Pointers
Let's define two pointers:

`even_idx`: Tracks the next even index where an even number should go.
`odd_idx`: Tracks the next odd index where an odd number should go.
Here is how the code looks:
```
even_idx = 0
odd_idx = 1

while even_idx < len(nums) and odd_idx < len(nums):
    if nums[even_idx] % 2 == 0:
        even_idx += 2  # Even number is in the correct position
    elif nums[odd_idx] % 2 == 1:
        odd_idx += 2  # Odd number is in the correct position
    else:
        swap(nums[even_idx], nums[odd_idx])
```

Each pointer has a specific role:

`even_idx`: Ensures even numbers are at even indices, moving forward only when the condition is met.
`odd_idx`: Ensures odd numbers are at odd indices, moving forward only when the condition is met. If each pointer finds a number at the wrong index, a swap corrects both simultaneously.
By assigning each pointer its own job, this problem becomes a series of straightforward checks and swaps rather than a single pointer juggling multiple conditions.

# Sorting the Three Realms
The Faangshui apprentices are tasked with arranging the temple’s ceremonial stones into three categories: stones marked with 0, 1, and 2. Master Qu insists that the sorting be done swiftly and without using additional storage.

Write a function to sort an array containing only 0s, 1s, and 2s in-place, ensuring the stones are perfectly ordered.

### Example Input:
`stones = [0, 2, 1, 2, 0, 1]`

### Example Output:
`[0, 0, 1, 1, 2, 2]`

### Solution
```python
class Solution:
    def sort_three_realms(self, stones):
        low = 0
        mid = 0
        high = len(stones) - 1

        while mid <= high:
            if stones[mid] == 0:
                stones[low], stones[mid] = stones[mid], stones[low]
                low += 1
                mid += 1

            elif stones[mid] == 1:
                mid += 1

            else:  # stones[mid] == 2
                stones[mid], stones[high] = stones[high], stones[mid]
                high -= 1

        return stones
```
