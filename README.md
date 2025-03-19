# Array Union Function with Deep Equality

A JavaScript utility function that performs a union operation on two arrays while handling deep equality comparisons for complex objects.

## Features

- Combines two arrays into a single array with unique elements
- Supports primitive values (numbers, strings, etc.)
- Handles nested objects and arrays through deep equality comparison
- Preserves the original data types of elements
- Maintains the order of elements (first occurrence is kept)

## Installation

```bash
npm install 
```

## Usage

```javascript
import union from "./union.js";

// Basic usage with numbers
union([1, 2, 3], [2, 3, 4]);
// Output: [1, 2, 3, 4]

// With strings
union(["a"], ["b"]);
// Output: ['a', 'b']

// Mixed types
union([1], ["1", 1]);
// Output: [1, '1']

// Complex objects
union([{ a: { b: 10 } }], [{ c: { d: 20 } }]);
// Output: [{ a: { b: 10 } }, { c: { d: 20 } }]

// Nested objects with arrays
union(
  [{ b: 10, c: { z: { t: 5, _t: 5 }, f: [4] } }, 2],
  [{ b: 10, c: { z: { t: 5, _t: 5 }, f: [4] } }, "2"]
);
// Output: [{ b: 10, c: { z: { t: 5, _t: 5 }, f: [4] } }, 2, '2']
```

## How It Works

The implementation consists of two main functions:

### 1. deepEqual(obj1, obj2)

This helper function performs a deep equality comparison between two values:

- Handles primitive types through direct comparison
- Recursively compares nested objects and arrays
- Checks for structural equality of objects
- Considers null values and type differences

### 2. union(arr1, arr2)

The main function that:

1. Takes two arrays as input
2. Combines them into a single array
3. Removes duplicates using deep equality comparison
4. Preserves the order of elements (first occurrence)
5. Returns the resulting unique array

