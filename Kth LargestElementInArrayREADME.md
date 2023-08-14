# leet-day31

# Kth Largest Element in an Array

## Problem Statement

You are given an integer array `nums` and an integer `k`. Your task is to find the kth largest element in the array.

## Example

### Input

```
nums = [3, 2, 1, 5, 6, 4]
k = 2
```

### Output

```
5
```

## Approach

To solve this problem, we can use a min-heap (priority queue) to keep track of the k largest elements encountered so far. As we iterate through the array, we'll add elements to the min-heap until its size reaches k. Once the size exceeds k, we'll compare the current element with the smallest element in the min-heap (which is at the top). If the current element is larger than the smallest element in the heap, we'll remove the smallest element and insert the current element into the heap.

By the end of the iteration, the min-heap will contain the k largest elements encountered, and the smallest of those k elements will be at the top of the heap, which is the kth largest element in the array.

## Algorithm

1. Create an empty min-heap (priority queue) `minHeap` that will hold the k largest elements.
2. Iterate through each element `num` in the input array `nums`.
   - If the size of `minHeap` is less than k, push the current element `num` into the `minHeap`.
   - If the size of `minHeap` is already k, compare the current element `num` with the smallest element in `minHeap` (which is at the top).
     - If `num` is larger than the top element of `minHeap`, pop the smallest element from `minHeap` and push the current element `num` into `minHeap`.
3. After iterating through the array, the top element of `minHeap` will be the kth largest element.

## Complexity Analysis

- Time complexity: O(n * log(k)), where n is the length of the array and k is the value given.
- Space complexity: O(k), as we are using a min-heap to store k elements.

## Conclusion

Finding the kth largest element in an array can be efficiently solved using a min-heap to track the k largest elements. The provided C++ solution follows this approach, providing an optimal solution to the problem.
