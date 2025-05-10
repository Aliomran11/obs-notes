# Logarithmic Complexity (O(log n))

## **Overview**
Logarithmic time complexity refers to algorithms where the problem size **reduces significantly** at each step, often by half. These algorithms are highly efficient for large inputs.

## **Key Concepts**
- The number of operations grows **logarithmically** with input size.
- Frequently used in **divide and conquer** strategies.
- Examples: **Binary Search, Tree Traversals, Heap Operations**.

## **Time & Space Complexity**
| Case          | Complexity |
|--------------|------------|
| Best Case    | O(1) |
| Worst Case   | O(log n) |
| Average Case | O(log n) |

## **Example Code (JavaScript)**
```javascript
// Binary Search (Logarithmic Complexity)
function binarySearch(arr, target) {
    let left = 0, right = arr.length - 1;

    while (left <= right) {
        let mid = Math.floor((left + right) / 2);

        if (arr[mid] === target) {
            return mid; // Target found
        } else if (arr[mid] < target) {
            left = mid + 1; // Search in right half
        } else {
            right = mid - 1; // Search in left half
        }
    }

    return -1; // Target not found
}

// Example usage
const arr = [1, 3, 5, 7, 9, 11];
console.log(binarySearch(arr, 5)); // Output: 2
