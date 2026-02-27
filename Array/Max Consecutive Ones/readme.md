# 📘 Arrays – Question 7  
# 485. Max Consecutive Ones

---

## 🧩 Problem Statement

Given a binary array `nums` (containing only 0s and 1s),  
return the maximum number of consecutive `1`s in the array.

---

## Examples

Input:  
nums = [1,1,0,1,1,1]  

Output:  
3  

Explanation:  
The longest consecutive 1s is [1,1,1].

---

# 🚀 Approach 1 — Brute Force

## 💡 Idea

For every index:

1. If element is 1, start counting consecutive 1s.
2. Continue until 0 appears.
3. Track maximum count.
4. Repeat for all indices.

---

## 💻 Code (Brute Force)

```js
function findMaxConsecutiveOnes(nums) {
    let maxCount = 0;

    for (let i = 0; i < nums.length; i++) {
        if (nums[i] === 1) {
            let count = 0;
            let j = i;

            while (j < nums.length && nums[j] === 1) {
                count++;
                j++;
            }

            if (count > maxCount) {
                maxCount = count;
            }
        }
    }

    return maxCount;
}
```

---

### ⏱ Time Complexity

**O(n²)**  

Reason:  
Nested traversal in worst case.

---

### 📦 Space Complexity

**O(1)**  

No extra memory used.

---

⚠ Not optimal.

---

# 🚀 Approach 2 — Optimized (Single Pass / Sliding Window) ✅

## 💡 Idea

Maintain:

- `currentCount` → current streak of 1s  
- `maxCount` → maximum streak seen so far  

If element is 1 → increment counter.  
If element is 0 → reset counter.  
Update maximum at every step.

---

## 💻 Code (Optimized)

```js
function findMaxConsecutiveOnes(nums) {
    let currentCount = 0;
    let maxCount = 0;

    for (let i = 0; i < nums.length; i++) {
        if (nums[i] === 1) {
            currentCount++;
            if (currentCount > maxCount) {
                maxCount = currentCount;
            }
        } else {
            currentCount = 0;
        }
    }

    return maxCount;
}
```

---

### ⏱ Time Complexity

**O(n)**  

Reason:  
Single pass through array.

---

### 📦 Space Complexity

**O(1)**  

Reason:  
Only two variables used.

---

# 🗣 Interview-Level Explanation

“I maintain a counter to track consecutive 1s while traversing the array. When a 0 appears, I reset the counter. At each step, I update the maximum streak found so far. This gives an O(n) time and O(1) space solution.”