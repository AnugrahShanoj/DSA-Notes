# 📘 Linked List Operations — Insertions & Deletions

---

# 🧠 Core Rule of Linked Lists

In linked lists:

```text
We do NOT move data.
We change links.
```

Linked Lists work by manipulating node references.

---

# 🧠 Current Linked List

```text
head
 ↓
10 → 20 → 30 → null
```

Internally:

```text
[10 | • ] → [20 | • ] → [30 | null]
```

---

# 🚀 Operation 1 — Insert At Beginning

---

## 🎯 Goal

Insert:

```text
5
```

at beginning.

Result:

```text
5 → 10 → 20 → 30
```

---

# 🧠 Core Idea

1. New node points to current head.
2. Move head to new node.

---

# 💻 Code

```js
function insertAtBeginning(head, val) {
    let newNode = new ListNode(val);

    newNode.next = head;

    head = newNode;

    return head;
}
```

---

# ⏱ Time Complexity

```text
O(1)
```

No traversal required.

---

# 🚀 Operation 2 — Insert At End

---

## 🎯 Goal

Insert:

```text
40
```

at end.

Result:

```text
10 → 20 → 30 → 40
```

---

# 🧠 Core Idea

Traverse until:

```text
current.next === null
```

Then connect new node.

---

# 💻 Code

```js
function insertAtEnd(head, val) {
    let newNode = new ListNode(val);

    if (head === null) {
        return newNode;
    }

    let current = head;

    while (current.next !== null) {
        current = current.next;
    }

    current.next = newNode;

    return head;
}
```

---

# ⏱ Time Complexity

```text
O(n)
```

Traversal required.

---

# 🚀 Operation 3 — Delete First Node

---

## 🎯 Goal

Delete first node from:

```text
10 → 20 → 30
```

Result:

```text
20 → 30
```

---

# 🧠 Core Idea

Move head to second node.

---

# 💻 Code

```js
function deleteFirst(head) {
    if (head === null) {
        return null;
    }

    head = head.next;

    return head;
}
```

---

# ⏱ Time Complexity

```text
O(1)
```

No traversal required.

---

# 🚀 Operation 4 — Delete Last Node

---

## 🎯 Goal

Delete last node from:

```text
10 → 20 → 30
```

Result:

```text
10 → 20
```

---

# 🧠 Core Idea

Need node before last node.

Why?

Because previous node stores reference to last node.

Set:

```js
current.next = null
```

to disconnect last node.

---

# 💻 Code

```js
function deleteLast(head) {
    if (head === null || head.next === null) {
        return null;
    }

    let current = head;

    while (current.next.next !== null) {
        current = current.next;
    }

    current.next = null;

    return head;
}
```

---

# ⏱ Time Complexity

```text
O(n)
```

Traversal required.

---

# 🧠 Most Important Linked List Understanding

Arrays:

```text
Modify values
```

Linked Lists:

```text
Modify references/links
```

---

# 🧠 Important Traversal Line

```js
current = current.next;
```

Meaning:

```text
Move current pointer to next node
```

Not:

```text
Increase value
```

---

# 📊 Complexity Summary

| Operation | Time Complexity |
|---|---|
Insert at beginning | O(1) |
Insert at end | O(n) |
Delete first | O(1) |
Delete last | O(n) |

---

# 🗣 Interview-Level Explanation

“In linked lists, operations are performed by manipulating node references instead of shifting elements like arrays. Efficient operations happen when required nodes are directly accessible.”