# Topic: Time Complexity & Space Complexity Foundations

---

## 1️⃣ Why Do We Study Complexity?

When solving problems, we don’t just care about correctness.  
We must care about:

- How fast the solution runs
- How much memory it uses
- Whether it works for large inputs

If input size increases from 10 to 100,000, some solutions become extremely slow.

Complexity helps us measure:

- How number of operations grow when input grows
- Whether solution is scalable

We measure growth rate, not exact seconds.

---

## 2️⃣ What is Time Complexity?

Time complexity measures:

How the number of operations increases as input size increases.

We use Big-O notation to represent this growth.

---

## 3️⃣ Important Big-O Types (Only These for Now)

### ✅ O(1) — Constant Time

**Definition:**  
The number of operations does not depend on input size.

**Example:**

```js
let x = arr[0];
```

No matter if array has 10 elements or 1 million elements,  
only one operation is performed.

**Key idea:**  
Time does not grow with n.

---

### ✅ O(n) — Linear Time

**Definition:**  
Operations grow proportionally with input size.

**Example:**

```js
for (let i = 0; i < n; i++) {
    console.log(i);
}
```

If n = 5 → runs 5 times  
If n = 100 → runs 100 times  

Growth is directly proportional to n.

**Key signal:**  
Single loop over n elements.

---

### ✅ O(n²) — Quadratic Time

**Definition:**  
Operations grow as square of input size.

**Example:**

```js
for (let i = 0; i < n; i++) {
    for (let j = 0; j < n; j++) {
        console.log(i, j);
    }
}
```

If n = 5 → 25 operations  
If n = 100 → 10,000 operations  

Very dangerous for large n.

**Key signal:**  
Nested loop over n.

---

### ✅ O(log n) — Logarithmic Time

**Definition:**  
Input size reduces by half each step.

**Example:**

```js
while (n > 1) {
    n = n / 2;
}
```

If n = 16:  
16 → 8 → 4 → 2 → 1  
Only 4 steps.

**Key signal:**  
Repeated division by 2.

---

## 4️⃣ Golden Rules of Big-O

### Rule 1: Drop Constants

2n → O(n)  
5n → O(n)  

**Why?**  
Because growth rate matters, not multiplier.

---

### Rule 2: Keep the Dominant Term

O(n + n²) → O(n²)  
O(n² + n³) → O(n³)  

Always keep highest growing term.

---

### Rule 3: Loops Determine Growth

- One loop → O(n)
- Nested loop → O(n²)
- Divide by 2 repeatedly → O(log n)

---

## 5️⃣ Practice Loop Analysis

### Example 1

```js
for (let i = 0; i < n; i++) {
    console.log(i);
}
```

Time Complexity: O(n)

Reason:  
Runs n times.

---

### Example 2

```js
for (let i = 0; i < n; i++) {
    console.log(i);
}

for (let j = 0; j < n; j++) {
    console.log(j);
}
```

Runs n + n = 2n times.

Drop constant → O(n)

---

### Example 3

```js
for (let i = 0; i < n; i++) {
    for (let j = 0; j < n; j++) {
        console.log(i, j);
    }
}
```

n × n = n²

Time Complexity: O(n²)

---

### Example 4

```js
for (let i = 0; i < n; i++) {
    for (let j = 0; j < i; j++) {
        console.log(i, j);
    }
}
```

Total operations roughly n² / 2.

Drop constant → O(n²)

---

### Example 5

```js
for (let i = 0; i < n; i++) {
    console.log(i);
}

for (let j = 0; j < n * n; j++) {
    console.log(j);
}
```

O(n) + O(n²)

Dominant term → O(n²)

---

## 6️⃣ What is Space Complexity?

Space complexity measures:

How much extra memory is used by the function.

Important:  
We do NOT count input array space.  
We only count additional memory created.

---

## 7️⃣ Space Complexity Types

### ✅ O(1) — Constant Space

Example:

```js
function sum(arr) {
    let total = 0;
    for (let i = 0; i < arr.length; i++) {
        total += arr[i];
    }
    return total;
}
```

Only few variables used.

Space does not grow with n.

Space Complexity: O(1)

---

### ✅ O(n) — Linear Space

Example:

```js
function copy(arr) {
    let newArr = [];
    for (let i = 0; i < arr.length; i++) {
        newArr.push(arr[i]);
    }
    return newArr;
}
```

New array grows with input size.

Space Complexity: O(n)

---

### ✅ Important Example

```js
function printPairs(arr) {
    for (let i = 0; i < arr.length; i++) {
        for (let j = 0; j < arr.length; j++) {
            console.log(arr[i], arr[j]);
        }
    }
}
```

Time Complexity: O(n²)  
Space Complexity: O(1)

Reason:  
No new memory created. Only printing.

---

## 8️⃣ Time vs Space Tradeoff

Sometimes we use extra memory to reduce time.

Example idea:

Nested loop → O(n²)

Use Map → O(n) time but O(n) space

This tradeoff is common in interviews.

---

## 9️⃣ Interview Thinking Summary

When solving problems:

First estimate time complexity.

If nested loops exist → check if optimization possible.

Ask:

Can I store previous results?

Can I avoid repeated work?

Check space usage.
