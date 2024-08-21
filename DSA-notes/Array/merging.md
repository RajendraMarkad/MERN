### Question: 
Given two sorted arrays `arr1` and `arr2`, write a function to merge them into a single sorted array. Solve this problem using various techniques in JavaScript.

```javascript
let arr1 = [1, 3, 5, 7];
let arr2 = [2, 4, 6, 8];
```

### 1. **Using Built-in Methods (ES6 Spread and Sort)**
```javascript
function mergeArraysBuiltIn(arr1, arr2) {
    return [...arr1, ...arr2].sort((a, b) => a - b);
}

console.log(mergeArraysBuiltIn(arr1, arr2));
// Output: [1, 2, 3, 4, 5, 6, 7, 8]
```

**Explanation**:  
- The spread operator (`...`) is used to combine both arrays.
- The `sort()` function sorts the combined array.

**Time Complexity**: O((n+m) * log(n+m)), where n and m are the lengths of `arr1` and `arr2`.

### 2. **Without Built-in Methods (Two-Pointer Technique)**
```javascript
function mergeArraysTwoPointers(arr1, arr2) {
    let mergedArray = [];
    let i = 0, j = 0;

    while (i < arr1.length && j < arr2.length) {
        if (arr1[i] < arr2[j]) {
            mergedArray.push(arr1[i]);
            i++;
        } else {
            mergedArray.push(arr2[j]);
            j++;
        }
    }

    // Add remaining elements from arr1 or arr2
    while (i < arr1.length) {
        mergedArray.push(arr1[i]);
        i++;
    }
    while (j < arr2.length) {
        mergedArray.push(arr2[j]);
        j++;
    }

    return mergedArray;
}

console.log(mergeArraysTwoPointers(arr1, arr2));
// Output: [1, 2, 3, 4, 5, 6, 7, 8]
```
```
function mergeArraysForLoop(arr1, arr2) {
    let mergedArray = [];
    let i = 0, j = 0;
    
    // Use a single loop to iterate over both arrays
    for (let k = 0; k < arr1.length + arr2.length; k++) {
        if (i < arr1.length && (j >= arr2.length || arr1[i] < arr2[j])) {
            mergedArray.push(arr1[i]);
            i++;
        } else {
            mergedArray.push(arr2[j]);
            j++;
        }
    }

    return mergedArray;
}

let arr1 = [1, 3, 5, 7];
let arr2 = [2, 4, 6, 8];

console.log(mergeArraysForLoop(arr1, arr2));
// Output: [1, 2, 3, 4, 5, 6, 7, 8]
```

**Explanation**:  
- Two pointers (`i` for `arr1` and `j` for `arr2`) are used to traverse the arrays.
- The smaller element is pushed into the `mergedArray`, and the corresponding pointer is incremented.
- After the main loop, any remaining elements are added to the `mergedArray`.

**Time Complexity**: O(n + m)

- **Best Optimized Approach**: The **Two-Pointer Technique** is the most efficient and widely used solution for merging two sorted arrays. It has a linear time complexity of **O(n + m)**, making it both time and space efficient.
