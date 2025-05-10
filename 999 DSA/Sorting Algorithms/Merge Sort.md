# Merge Sort

## **Overview**
- Explain what this concept is.
		-   Merge Sort is a **divide-and-conquer** sorting algorithm that works by recursively splitting an array into smaller subarrays, sorting them, and then merging them back together in sorted order. It has a time complexity of **O(n log n)** in all cases (best, average, worst), making it very efficient for large datasets.
- Why is it important?

## **Key Concepts**
- ✨ Important points about this topic.

## **Time & Space Complexity**
| Case         | Complexity |
| ------------ | ---------- |
| Best Case    | TBD        |
| Worst Case   | TBD        |
| Average Case | TBD        |
|              |            |
## Visual Comparison

| Feature              | Algorithm 1 (Conceptual) | Algorithm 2 (Practical) |
| -------------------- | ------------------------ | ----------------------- |
| Space Complexity     | O(n) per recursion level | O(n) total              |
| Memory Usage         | High (many arrays)       | Optimized               |
| Code Readability     | More intuitive++         | More complex            |
| Practical Efficiency | Slower                   | Faster                  |
| Implementation Style | Functional               | Imperative              |
## **Example Code**
```js
# Example implementation of Merge Sort.md in js
function conceptualMergeSort(array) {
    // Base case: single element is already sorted
    if (array.length <= 1) return array;
    
    // 1. DIVIDE: Split the array into two halves
    const middle = Math.floor(array.length / 2);
    const leftHalf = array.slice(0, middle);
    const rightHalf = array.slice(middle);
    
    // 2. CONQUER: Recursively sort each half
    const sortedLeft = conceptualMergeSort(leftHalf);
    const sortedRight = conceptualMergeSort(rightHalf);
    
    // 3. COMBINE: Merge the two sorted halves
    return conceptualMerge(sortedLeft, sortedRight);
}

function conceptualMerge(left, right) {
    let result = [];
    let leftIndex = 0, rightIndex = 0;
    
    // Compare elements and merge
    while (leftIndex < left.length && rightIndex < right.length) {
        if (left[leftIndex] < right[rightIndex]) {
            result.push(left[leftIndex]);
            leftIndex++;
        } else {
            result.push(right[rightIndex]);
            rightIndex++;
        }
    }
    
    // Add remaining elements
    return result.concat(left.slice(leftIndex)).concat(right.slice(rightIndex));
}

function practicalMergeSort(array, start = 0, end = array.length - 1, temp = []) {
    if (start < end) {
        const middle = Math.floor((start + end) / 2);
        
        // Sort first and second halves
        practicalMergeSort(array, start, middle, temp);
        practicalMergeSort(array, middle + 1, end, temp);
        
        // Merge the sorted halves
        practicalMerge(array, start, middle, end, temp);
    }
    return array;
}

function practicalMerge(array, start, middle, end, temp) {
    let left = start;
    let right = middle + 1;
    let tempIndex = 0;
    
    // Merge two subarrays in sorted order
    while (left <= middle && right <= end) {
        if (array[left] <= array[right]) {
            temp[tempIndex++] = array[left++];
        } else {
            temp[tempIndex++] = array[right++];
        }
    }
    
    // Copy remaining left elements
    while (left <= middle) {
        temp[tempIndex++] = array[left++];
    }
    
    // Copy remaining right elements
    while (right <= end) {
        temp[tempIndex++] = array[right++];
    }
    
    // Copy back from temp to original array
    for (let i = start; i <= end; i++) {
        array[i] = temp[i - start];
    }
}
