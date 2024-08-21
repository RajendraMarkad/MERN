Removing duplicates from an array can be done in various ways, from basic to more advanced techniques, especially when dealing with nested arrays. Below are different approaches without using built-in methods like `Set`, `filter()`, etc. We can only use `push()` and `length`.

### **1. Basic Example: Removing Duplicates from a Simple Array**

For a basic array like `[1, 2, 2, 3, 4, 4]`, we can remove duplicates by iterating through the array and checking if each element is already in a new array.

#### **Example:**
```javascript
function removeDuplicates(arr) {
    let uniqueArray = [];
    // 1. Iterate all element of array
    for (let i = 0; i < arr.length; i++) {
        // 2. check for the element same present in uniqueArray or not. if present make isDuplicate true otherwise keep it false.
        let isDuplicate = false;
        for (let j = 0; j < uniqueArray.length; j++) {
            if (arr[i] === uniqueArray[j]) {
                isDuplicate = true;
                break;
            }
        }
        // 3. if similar element is not present in uniqueArray then push it. note: !false= true
        if (!isDuplicate) {
            uniqueArray.push(arr[i]);
        }
    }
    return uniqueArray;
}

let arr = [1, 2, 2, 3, 4, 4, 5];
console.log(removeDuplicates(arr)); // Output: [1, 2, 3, 4, 5]
```

### **2. Removing Duplicates from a deeply Nested Array**

```
function removeDuplicatesDeep(arr) {
    let uniqueElements = new Set(); // Using a Set to track unique elements

    // Helper function to flatten and collect unique elements
    function processArray(array) {
        for (let i = 0; i < array.length; i++) {
            if (Array.isArray(array[i])) {
                processArray(array[i]); // Recurse into nested arrays
            } else {
                uniqueElements.add(array[i]); // Add element to Set
            }
        }
    }

    processArray(arr); // Start processing the array

    // Convert the Set to an array and return it
    return Array.from(uniqueElements);
}

const deeplyNestedArr = [1, [2, [3, 4, [5, 6]]], [2, [3, 4]], 7];
console.log(removeDuplicatesDeep(deeplyNestedArr)); // Output: [1, 2, 3, 4, 5, 6, 7]

```

### **3.Removing Duplicates from a Deeply Nested Array without using set()**

For deeply nested arrays like `[1, [2, [3, 4, [5, 6]]], [2, [3, 4]], 7]`, you need to recursively flatten the array, remove duplicates, and then rebuild it.

#### **Example:**
```javascript
function flattenArray(arr) {
    let flatArray = [];
    for (let i = 0; i < arr.length; i++) {
        if (Array.isArray(arr[i])) {
            let subArray = flattenArray(arr[i]);
            for (let j = 0; j < subArray.length; j++) {
                flatArray.push(subArray[j]);
            }
        } else {
            flatArray.push(arr[i]);
        }
    }
    return flatArray;
}

function removeDuplicatesAdvanced(arr) {
    let flattenedArray = flattenArray(arr);

    // Remove duplicates from the flattened array
    let uniqueArray = [];
    for (let i = 0; i < flattenedArray.length; i++) {
        let isDuplicate = false;
        for (let j = 0; j < uniqueArray.length; j++) {
            if (flattenedArray[i] === uniqueArray[j]) {
                isDuplicate = true;
                break;
            }
        }
        if (!isDuplicate) {
            uniqueArray.push(flattenedArray[i]);
        }
    }
    
    return uniqueArray;
}

let deeplyNestedArr = [1, [2, [3, 4, [5, 6]]], [2, [3, 4]], 7];
console.log(removeDuplicatesAdvanced(deeplyNestedArr)); // Output: [1, 2, 3, 4, 5, 6, 7]
```

### **Summary:**
- **Basic Approach:** Iterate through the array and push unique elements into a new array.
- **Nested Array (One Level):** Flatten the array first, then remove duplicates.
- **Deeply Nested Array:** Recursively flatten the array, remove duplicates, and return the result.

These approaches give you full control over how the array is processed without relying on built-in methods, except for `push()` and `length`.
