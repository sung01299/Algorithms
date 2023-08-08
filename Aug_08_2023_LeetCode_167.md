# 167. Two Sum II - Input Array Is Sorted

**Difficulty: Medium**

*Related Topics: Array, Two Pointers, Binary Search*

Given a 1-indexed array of integers numbers that is already sorted in non-decreasing order, find two numbers such that they add up to a specific target number. Let these two numbers be numbers[index1] and numbers[index2] where 1 <= index1 < index2 < numbers.length.

Return the indices of the two numbers, index1 and index2, added by one as an integer array [index1, index2] of length 2.

The tests are generated such that there is exactly one solution. You may not use the same element twice.

Your solution must use only constant extra space.

Example 1:

Input: numbers = [2,7,11,15], target = 9
Output: [1,2]
Explanation: The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return [1, 2].

Example 2:

Input: numbers = [2,3,4], target = 6
Output: [1,3]
Explanation: The sum of 2 and 4 is 6. Therefore index1 = 1, index2 = 3. We return [1, 3].

Example 3:

Input: numbers = [-1,0], target = -1
Output: [1,2]
Explanation: The sum of -1 and 0 is -1. Therefore index1 = 1, index2 = 2. We return [1, 2].

## Code 1: Hash Map Solution

```python
num = {}
for i in range(len(numbers)):
  if numbers[i] in num:
    return [num[numbers[i]]+1, i+1]
  else:
    num[target - numbers[i]] = i

```
## Code 2: Two Pointer Solution

```python
ptr1 = 0
ptr2 = len(numbers) - 1
while ptr1 < ptr2:
    if numbers[ptr1] + numbers[ptr2] == target:
        return [ptr1+1, ptr2+1]
    if numbers[ptr1] + numbers[ptr2] > target:
        ptr2 -= 1
    else:
                ptr1 += 1
```
