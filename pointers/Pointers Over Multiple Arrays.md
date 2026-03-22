Sometimes you’ll need to work with multiple arrays where standard linear traversal isn’t possible because you can’t simply iterate from the beginning to the end of one array. In these cases, you can use multiple single pointers — one for each array.

## Example: Merging Two Sorted Arrays

**Task:** given two sorted arrays, merge them into a single sorted array.

```python
nums1 = [1, 2, 3]
nums2 = [2, 5, 6]
merged_array = [1, 2, 2, 3, 5, 6]
```

Since you can’t just iterate linearly from start to finish in either array (you don’t know which element is next in sorted order), index pointers are ideal.

## Defining the Pointers

- **pointer1**: Tracks the current position in `nums1` — the next element not yet added to `merged_array`.
- **pointer2**: Tracks the current position in `nums2` — the next element not yet added to `merged_array`.

Initially, both pointers start at index `0` of their respective arrays.

## Merging Process

1. Compare `nums1[pointer1]` and `nums2[pointer2]`.
2. Whichever element is smaller goes into `merged_array`, and the corresponding pointer is incremented.
3. Repeat until one pointer reaches the end of its array.
4. Append any remaining elements from the other array.

```python
pointer1 = 0
pointer2 = 0
merged_array = []

while pointer1 < len(nums1) and pointer2 < len(nums2):
    if nums1[pointer1] < nums2[pointer2]:
        merged_array.append(nums1[pointer1])
        pointer1 += 1
    else:
        merged_array.append(nums2[pointer2])
        pointer2 += 1

# Append remaining elements from nums1 or nums2.
while pointer1 < len(nums1):
    merged_array.append(nums1[pointer1])
    pointer1 += 1

while pointer2 < len(nums2):
    merged_array.append(nums2[pointer2])
    pointer2 += 1
```
