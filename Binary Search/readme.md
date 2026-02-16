# 📘 Foundation – Question 8  
# 704. Binary Search

---

## 🧩 Problem Statement

Given a **sorted array of integers** `nums` and an integer `target`,  
return the index of `target` if it exists in the array.

Otherwise, return `-1`.

You must write an algorithm with **O(log n)** time complexity.

---

## Examples

Input:  
nums = [-1,0,3,5,9,12], target = 9  
Output: 4  

Input:  
nums = [-1,0,3,5,9,12], target = 2  
Output: -1  

---

# 🚀 Approach 1 — Linear Search (Brute Force)

## 💡 Idea

Traverse the array and compare each element with the target.

---

## 💻 Code

```js
function search(nums, target) {
    for (let i = 0; i < nums.length; i++) {
        if (nums[i] === target) {
            return i;
        }
    }
    return -1;
}
```

---

### ⏱ Time Complexity

**O(n)**  

Reason:  
Worst case, we check every element.

---

### 📦 Space Complexity

**O(1)**  

Reason:  
Only loop variable used.

---

⚠ This does NOT satisfy required O(log n) complexity.

---

# 🚀 Approach 2 — Binary Search (Optimized)

## 💡 Idea

Since the array is sorted:

1. Find middle element.
2. If target equals middle → return index.
3. If target is smaller → search left half.
4. If target is larger → search right half.
5. Repeat until found or search space becomes empty.

---

## 💻 Code (Iterative)

```js
function search(nums, target) {
    let left = 0;
    let right = nums.length - 1;

    while (left <= right) {
        let mid = Math.floor((left + right) / 2);

        if (nums[mid] === target) {
            return mid;
        }

        if (nums[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }

    return -1;
}
```

---

### ⏱ Time Complexity

**O(log n)**  

Reason:  
Each iteration halves the search space.

---

### 📦 Space Complexity

**O(1)**  

Reason:  
Only pointer variables (`left`, `right`, `mid`) are used.

---

# 🗣 Interview-Level Explanation

“Since the array is sorted, I apply Binary Search. I maintain two pointers representing the current search space. At each step, I check the middle element and eliminate half of the array based on comparison with the target. This reduces time complexity to O(log n) while maintaining constant space usage.”


