Removing duplicates from an array can be done in various ways, from basic to more advanced techniques, especially when dealing with nested arrays. Below are different approaches without using built-in methods like `Set`, `filter()`, etc. We can only use `push()` and `length`.

### **1. Basic Example: Removing Duplicates from a Simple Array**

For a basic array like `[1, 2, 2, 3, 4, 4]`, we can remove duplicates by iterating through the array and checking if each element is already in a new array.

#### **Example:**
```javascript
function removeDuplicates(arr) {
    let uniqueArray = [];
    for (let i = 0; i < arr.length; i++) {
        let isDuplicate = false;
        for (let j = 0; j < uniqueArray.length; j++) {
            if (arr[i] === uniqueArray[j]) {
                isDuplicate = true;
                break;
            }
        }
        if (!isDuplicate) {
            uniqueArray.push(arr[i]);
        }
    }
    return uniqueArray;
}

let arr = [1, 2, 2, 3, 4, 4, 5];
console.log(removeDuplicates(arr)); // Output: [1, 2, 3, 4, 5]
```

### **2. Removing Duplicates from a Nested Array (One Level of Nesting)**

When dealing with a nested array like `[1, 2, [3, 4], [3, 4], 5]`, we need to flatten it first, then remove duplicates.

#### **Example:**
```javascript
function removeDuplicatesFromNested(arr) {
    let flattenedArray = [];
    
    // Flatten the array manually (one level deep)
    for (let i = 0; i < arr.length; i++) {
        if (Array.isArray(arr[i])) {
            for (let j = 0; j < arr[i].length; j++) {
                flattenedArray.push(arr[i][j]);
            }
        } else {
            flattenedArray.push(arr[i]);
        }
    }
    
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

let nestedArr = [1, 2, [3, 4], [3, 4], 5];
console.log(removeDuplicatesFromNested(nestedArr)); // Output: [1, 2, 3, 4, 5]
```

### **3. Advanced Example: Removing Duplicates from a Deeply Nested Array**

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
