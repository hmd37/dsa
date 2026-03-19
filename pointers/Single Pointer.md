## Single Pointer

You’ve likely already used a single pointer without realizing it. A basic example is finding the index of the maximum value in an array:

```python
max_pointer = 0
for i in range(len(nums)):
    if nums[i] > nums[max_pointer]:
        max_pointer = i

print(f"The index of the maximum value is {max_pointer}")## Single Pointer

You’ve likely already used a single pointer without realizing it. A basic example is finding the index of the maximum value in an array:

```python
max_pointer = 0
for i in range(len(nums)):
    if nums[i] > nums[max_pointer]:
        max_pointer = i

print(f"The index of the maximum value is {max_pointer}")
```
Here, max_pointer stores the index of the currently most interesting element—in this case, the largest value so far. As the loop progresses, this pointer updates whenever a new maximum is found.
