# Two Sum

The Two Sum problem involves finding two numbers in an array that add up to a specific target sum. Here's a JavaScript solution using a hash map for efficient lookup:

```javascript
function twoSum(nums, target) {
  const map = {}; // Hash map to store number-index pairs

  for (let i = 0; i < nums.length; i++) {
    const complement = target - nums[i]; // Calculate the complement

    // If the complement exists in the map, return its index and current index
    if (map[complement] !== undefined) {
      return [map[complement], i];
    }

    // Store the current number and its index in the map
    map[nums[i]] = i;
  }

  // If no solution is found, return an empty array
  return [];
}

// Example usage:
const nums = [2, 7, 11, 15];
const target = 9;
console.log(twoSum(nums, target)); // Output: [0, 1] (because nums[0] + nums[1] = 2 + 7 = 9)
```

This solution has a time complexity of O(n), where n is the number of elements in the array, because we iterate through the array only once. The space complexity is also O(n) due to the hash map used to store number-index pairs.
