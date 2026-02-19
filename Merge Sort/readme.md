# 📘 Foundation – Question 9  
# 912. Sort an Array

---

## 🧩 Problem Statement

Given an integer array `nums`, sort the array in ascending order and return it.

You must solve the problem with:

- Time complexity: **O(n log n)**
- Space complexity: as efficient as possible

---

## Examples

Input:  
nums = [5,2,3,1]  
Output:  
[1,2,3,5]  

Input:  
nums = [5,1,1,2,0,0]  
Output:  
[0,0,1,1,2,5]  

---

# 🚀 Approach 1 — Built-in sort() (Not Preferred in Interviews)

## 💻 Code

```js
function sortArray(nums) {
    return nums.sort((a, b) => a - b);
}
```

---

### ⏱ Time Complexity

**O(n log n)** (engine dependent)

---

### 📦 Space Complexity

Depends on internal implementation.

---

⚠ In interviews, manual implementation of sorting algorithm is expected.

---

# 🚀 Approach 2 — Merge Sort (Divide & Conquer) ✅

---

## 💡 Idea

1. Divide array into two halves recursively.
2. Continue splitting until subarrays of size 1 are formed.
3. Merge sorted subarrays by comparing elements.
4. Continue merging until full array is sorted.

---

## 💻 Code (Merge Sort)

```js
function sortArray(nums) {
    if (nums.length <= 1) {
        return nums;
    }

    const mid = Math.floor(nums.length / 2);
    const left = sortArray(nums.slice(0, mid));
    const right = sortArray(nums.slice(mid));

    return merge(left, right);
}

function merge(left, right) {
    let result = [];
    let i = 0;
    let j = 0;

    while (i < left.length && j < right.length) {
        if (left[i] < right[j]) {
            result.push(left[i]);
            i++;
        } else {
            result.push(right[j]);
            j++;
        }
    }

    return result.concat(left.slice(i)).concat(right.slice(j));
}
```

---

### ⏱ Time Complexity

**O(n log n)**  

Reason:  
- Splitting happens log₂(n) times.  
- At each level, merging processes n elements.  
- Total work = n × log n.

---

### 📦 Space Complexity

**O(n)**  

Reason:  
- Extra array used during merge operation.  
- Recursion stack depth = O(log n).

---

# 🗣 Interview-Level Explanation

“I implemented Merge Sort using the divide and conquer strategy. The array is recursively split into halves until single-element subarrays are obtained, which are already sorted. Then, the merge function combines these sorted subarrays by comparing elements. This guarantees O(n log n) time complexity while using O(n) auxiliary space.”
