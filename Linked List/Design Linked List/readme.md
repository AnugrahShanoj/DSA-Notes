# 📘 Linked List – 707. Design Linked List

---

# 🧩 Problem Statement

Design your own Linked List class.

Implement the following operations:

| Function | Purpose |
|---|---|
get(index) | Get value at index |
addAtHead(val) | Insert node at beginning |
addAtTail(val) | Insert node at end |
addAtIndex(index, val) | Insert node at specific index |
deleteAtIndex(index) | Delete node at specific index |

---

# 🧠 Most Important Concept

There are TWO different structures:

| Structure | Purpose |
|---|---|
ListNode | Represents ONE node |
MyLinkedList | Represents ENTIRE linked list |

---

# 🧱 ListNode Structure

Each node contains:

- value
- reference to next node

---

# 💻 ListNode Code

```js
class ListNode {
    constructor(val) {
        this.val = val;
        this.next = null;
    }
}
```

---

# 🧠 Example Node

```js
new ListNode(10)
```

creates:

```text
{
   val: 10,
   next: null
}
```

---

# 🚂 MyLinkedList Structure

MyLinkedList manages the full linked list.

It stores only:

```js
this.head
```

which points to first node.

---

# 💻 MyLinkedList Constructor

```js
var MyLinkedList = function() {
    this.head = null;
};
```

---

# 🧠 Initial State

```text
head → null
```

Meaning:

```text
Empty linked list
```

---

# 🚨 Important Understanding

`head` does NOT store value.

It stores:

```text
reference/address of first node
```

---

# 🧠 Connection Between ListNode and MyLinkedList

MyLinkedList stores:

```js
this.head
```

which points to first ListNode.

Then nodes connect themselves using:

```js
next
```

---

# 🧠 Visualization

```text
MyLinkedList object
        |
        v
      head
        |
        v
   [10 | • ] → [20 | • ] → [30 | null]
```

---

# 🚀 Full Correct Code

```js
class ListNode {
    constructor(val) {
        this.val = val;
        this.next = null;
    }
}

var MyLinkedList = function() {
    this.head = null;
};

/** 
 * @param {number} index
 * @return {number}
 */
MyLinkedList.prototype.get = function(index) {
    let current = this.head;
    let count = 0;

    while (current !== null) {
        if (count === index) {
            return current.val;
        }

        current = current.next;
        count++;
    }

    return -1;
};

/** 
 * @param {number} val
 * @return {void}
 */
MyLinkedList.prototype.addAtHead = function(val) {
    let newNode = new ListNode(val);

    newNode.next = this.head;

    this.head = newNode;
};

/** 
 * @param {number} val
 * @return {void}
 */
MyLinkedList.prototype.addAtTail = function(val) {
    let newNode = new ListNode(val);

    if (this.head === null) {
        this.head = newNode;
        return;
    }

    let current = this.head;

    while (current.next !== null) {
        current = current.next;
    }

    current.next = newNode;
};

/** 
 * @param {number} index 
 * @param {number} val
 * @return {void}
 */
MyLinkedList.prototype.addAtIndex = function(index, val) {

    if (index === 0) {
        this.addAtHead(val);
        return;
    }

    let current = this.head;
    let count = 0;

    while (current !== null && count < index - 1) {
        current = current.next;
        count++;
    }

    if (current === null) {
        return;
    }

    let newNode = new ListNode(val);

    newNode.next = current.next;

    current.next = newNode;
};

/** 
 * @param {number} index
 * @return {void}
 */
MyLinkedList.prototype.deleteAtIndex = function(index) {

    if (this.head === null) {
        return;
    }

    if (index === 0) {
        this.head = this.head.next;
        return;
    }

    let current = this.head;
    let count = 0;

    while (current.next !== null && count < index - 1) {
        current = current.next;
        count++;
    }

    if (current.next === null) {
        return;
    }

    current.next = current.next.next;
};
```

---

# 🧠 Important Pointer Operations

## Insert Node

```js
newNode.next = current.next;
current.next = newNode;
```

Meaning:

```text
Insert new node between nodes
```

---

## Delete Node

```js
current.next = current.next.next;
```

Meaning:

```text
Skip current node and disconnect it
```

---

# 🚨 Most Important Beginner Understanding

Linked List is NOT magical.

It is simply:

```text
Objects connected using references
```

---

# 📊 Time Complexity Summary

| Operation | Time Complexity |
|---|---|
get | O(n) |
addAtHead | O(1) |
addAtTail | O(n) |
addAtIndex | O(n) |
deleteAtIndex | O(n) |

---

# 🗣 Interview-Level Explanation

“A linked list consists of nodes connected using references. The linked list object stores only the head reference, while each node stores data and reference to the next node. Operations are performed by manipulating pointers instead of shifting elements like arrays.”