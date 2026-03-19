## Single Pointer

You’ve likely already used a single pointer without realizing it. A basic example is finding the index of the maximum value in an array:

```python
max_pointer = 0
for i in range(len(nums)):
    if nums[i] > nums[max_pointer]:
        max_pointer = i

print(f"The index of the maximum value is {max_pointer}")## Single Pointer
```

Here, max_pointer stores the index of the currently most interesting element—in this case, the largest value so far. As the loop progresses, this pointer updates whenever a new maximum is found.

## Index of the Minimum

Your task is to write a function that returns the index of the minimum value in an array of weights. If there are multiple loads of the same minimum weight, return the index of the first one.

**Example Input:**
`[11, 3, 5, 7, 2, 8, 10]`

**Example Output:**
`4`

### Solution

```python
class Solution:
    def min_index(self, weights):
        if not weights:
            return -1 # Handle empty array case if necessary
            
        min_pointer = 0
        for i, weight in enumerate(weights):
            if weight < weights[min_pointer]:
                min_pointer = i
                
        return min_pointer
```
