# LCQ
My personal LeetCode practice questions &amp; solutions.

# Insertion Sort List

This repository contains a Java solution for sorting a singly linked list using the insertion sort algorithm.

## Problem Description

Given the head of a singly linked list, sort the list using insertion sort, and return the sorted list's head.

### Insertion Sort Algorithm:

- Insertion sort iterates, consuming one input element each repetition and growing a sorted output list.
- At each iteration, insertion sort removes one element from the input data, finds the location it belongs within the sorted list, and inserts it there.
- It repeats until no input elements remain.

![Insertion Sort Example](insertion_sort.png)

## Examples

### Example 1:

**Input:**
```
head = [4,2,1,3]
```
**Output:**
```
[1,2,3,4]
```

### Example 2:

**Input:**
```
head = [-1,5,3,4,0]
```
**Output:**
```
[-1,0,3,4,5]
```

## Constraints

- The number of nodes in the list is in the range [1, 5000].
- Node values are in the range [-5000, 5000].

## Implementation

The Java solution for this problem is implemented in `Solution.java`. It includes the `insertionSortList` method which sorts the linked list using the insertion sort algorithm.

```java
// Example Java implementation
public class Solution {
    public ListNode insertionSortList(ListNode head) {
        // Your implementation here
    }
}
```

## Testing

To test the solution, you can use the provided examples or additional test cases.

## Author

- Your Name
- Contact Information (optional)

