# Find Matching Object Property

You can implement the `findMatchingObjectProperty` function to recursively search through the object and its nested properties to find a matching property value. Here's how you can do it:

```javascript
const findMatchingObjectProperty = (obj, keys) => {
  // Base case: if obj is null or undefined, return false
  if (obj === null || typeof obj !== "object") {
    return false;
  }

  // Check if obj has the specified key
  if (keys.includes(Object.keys(obj)[0])) {
    // If the value of the key matches, return true
    if (Object.values(obj)[0] === keys[1]) {
      return true;
    }
  }

  // Recursively search through nested properties
  for (const key in obj) {
    if (findMatchingObjectProperty(obj[key], keys)) {
      return true;
    }
  }

  // If no matching property is found, return false
  return false;
};

// Example object
const obj = {
  a: 1,
  b: {
    c: [{ d: "d" }, { e: "e1" }],
    m: "m",
  },
};

// Test the function
console.log(findMatchingObjectProperty(obj, ["e", "e1"])); // Output: true
```

In this implementation:

- The `findMatchingObjectProperty` function takes an object `obj` and an array `keys` as arguments.
- It checks if the object has the specified key (`keys[0]`) and if its value matches the second element of the `keys` array (`keys[1]`).
- If a matching property is found, it returns `true`.
- If no matching property is found in the current object, it recursively searches through nested properties.
- If no matching property is found in the object and its nested properties, it returns `false`.
- The example object `obj` is provided, and the function is tested with the `['e', 'e1']` keys, which should return `true` as there is a property with key `'e'` and value `'e1'` in the nested structure of the object.
