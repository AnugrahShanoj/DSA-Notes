# 📘 Linked List – 876. Middle of the Linked List

---

# 🧩 Problem Statement

Given the `head` of a singly linked list,

Return the middle node of the linked list.

If there are two middle nodes:

```text
Return the second middle node
```

---

# 🧠 Example 1

```text
1 → 2 → 3 → 4 → 5
```

Middle node:

```text
3
```

---

# 🧠 Example 2

```text
1 → 2 → 3 → 4 → 5 → 6
```

Two middle nodes:

```text
3 and 4
```

Return:

```text
4
```

(second middle node)

---

# 🚀 Approach 1 — Brute Force

---

# 🧠 Idea

1. Count total number of nodes
2. Find middle index
3. Traverse again until middle node

---

# 💻 Code (Brute Force)

```js
var middleNode = function(head) {

    let length = 0;
    let current = head;

    while(current !== null){
        length++;
        current = current.next;
    }

    let middle = Math.floor(length / 2);

    current = head;

    while(middle > 0){
        current = current.next;
        middle--;
    }

    return current;
};
```

---

# ⏱ Time Complexity

```text
O(n)
```

Two traversals.

---

# 📦 Space Complexity

```text
O(1)
```

---

# 🚀 Approach 2 — Fast & Slow Pointer (Optimal) ✅

---

# 🧠 Core Idea

Use two pointers:

| Pointer | Movement |
|---|---|
slow | moves 1 step |
fast | moves 2 steps |

---

# 🚨 Main Observation

When:

```text
fast reaches end
```

slow automatically reaches:

```text
middle node
```

---

# 💻 Code (Optimal)

```js
var middleNode = function(head) {

    let slow = head;
    let fast = head;

    while(fast !== null && fast.next !== null){
        slow = slow.next;
        fast = fast.next.next;
    }

    return slow;
};
```

---

# 🚨 Important Loop Condition

```js
while(fast !== null && fast.next !== null)
```

Why?

Because:

```js
fast = fast.next.next
```

requires:

- fast should exist
- fast.next should exist

Otherwise program crashes.

---

# 🧠 Dry Run — Odd Length List

Input:

```text
1 → 2 → 3 → 4 → 5
```

---

## Initial

| Slow | Fast |
|---|---|
1 | 1 |

---

## Iteration 1

| Slow | Fast |
|---|---|
2 | 3 |

---

## Iteration 2

| Slow | Fast |
|---|---|
3 | 5 |

---

## Next Loop Check

```text
fast.next = null
```

Loop stops.

Return:

```text
3
```

---

# 🧠 Dry Run — Even Length List

Input:

```text
1 → 2 → 3 → 4 → 5 → 6
```

---

## Initial

| Slow | Fast |
|---|---|
1 | 1 |

---

## Iteration 1

| Slow | Fast |
|---|---|
2 | 3 |

---

## Iteration 2

| Slow | Fast |
|---|---|
3 | 5 |

---

## Important Check

```text
fast = 5
fast.next = 6
```

Both exist.

So loop continues.

---

## Iteration 3

| Slow | Fast |
|---|---|
4 | null |

Loop stops.

Return:

```text
4
```

(second middle node)

---

# 🧠 Important Understanding

---

# Odd Length List

Fast pointer reaches:

```text
last node
```

Slow pointer reaches:

```text
exact middle
```

---

# Even Length List

Fast pointer crosses end and becomes:

```text
null
```

One extra iteration happens.

So slow pointer moves to:

```text
second middle node
```

---

# 🧠 Why Fast & Slow Works

Fast pointer moves twice as fast as slow pointer.

So:

```text
When fast completes full list,
slow completes half list.
```

Half list means:

```text
middle
```

---

# 🚨 Most Important Pattern Recognition

When question involves:

- middle node
- cycle detection
- half traversal
- kth node from end

Think:

```text
Fast & Slow Pointer Pattern
```

---

# 📊 Complexity Comparison

| Approach | Time | Space |
|---|---|---|
Brute Force | O(n) | O(1) |
Fast & Slow | O(n) | O(1) |

Fast & Slow is better because only one traversal is used.

---

# 🧠 Biggest Learning

This problem teaches:

```text
Different pointers can move at different speeds
```

This becomes foundation for many advanced Linked List problems.

---

# 🗣 Interview-Level Explanation

“I use two pointers: slow and fast. Slow moves one step at a time while fast moves two steps. When fast reaches the end of the linked list, slow naturally reaches the middle node.”