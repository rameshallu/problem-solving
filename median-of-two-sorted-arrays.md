# Median of Two Sorted Arrays

To find the median of two sorted arrays, you can use the merge approach where you merge both arrays into one sorted array and then find the median. Here's a JavaScript solution:

```javascript
function findMedianSortedArrays(nums1, nums2) {
  const mergedArray = mergeSortedArrays(nums1, nums2);
  const n = mergedArray.length;

  if (n % 2 === 0) {
    // If the length of the merged array is even, return the average of the middle two elements
    return (mergedArray[n / 2 - 1] + mergedArray[n / 2]) / 2;
  } else {
    // If the length of the merged array is odd, return the middle element
    return mergedArray[Math.floor(n / 2)];
  }
}

function mergeSortedArrays(nums1, nums2) {
  const merged = [];
  let i = 0,
    j = 0;

  while (i < nums1.length && j < nums2.length) {
    if (nums1[i] < nums2[j]) {
      merged.push(nums1[i]);
      i++;
    } else {
      merged.push(nums2[j]);
      j++;
    }
  }

  // Add remaining elements from nums1, if any
  while (i < nums1.length) {
    merged.push(nums1[i]);
    i++;
  }

  // Add remaining elements from nums2, if any
  while (j < nums2.length) {
    merged.push(nums2[j]);
    j++;
  }

  return merged;
}

// Example usage:
console.log(findMedianSortedArrays([1, 3], [2])); // Output: 2.0
console.log(findMedianSortedArrays([1, 2], [3, 4])); // Output: 2.5
console.log(findMedianSortedArrays([0, 0], [0, 0])); // Output: 0.0
console.log(findMedianSortedArrays([], [1])); // Output: 1.0
```

In this solution:

- We first merge the two sorted arrays `nums1` and `nums2` into one sorted array using the `mergeSortedArrays` function.
- Then, we calculate the median based on whether the length of the merged array is even or odd.
- The time complexity of this solution is O(m + n), where m and n are the lengths of `nums1` and `nums2`, respectively, as we traverse both arrays once during the merge operation.
