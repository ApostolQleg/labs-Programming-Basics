# Laboratory Work 4: Queue-Based Data Flow

This repository contains the documentation and extracted implementation for the fourth laboratory work on the Fundamentals of Programming. The assignment topic is priority queue behavior and retrieval order.

## Task Description

The objective of this laboratory work was to implement a bi-directional priority queue capable of retrieving elements by highest/lowest priority and by insertion order (oldest/newest).

In the integrated project implementation, the practical scope was focused on queue-based insertion-order processing. The extracted lab implementation keeps only the core queue data structure.

## Implementation Details

The implementation is directly copied from the QuizTime project and contains only the core module required for this lab:

### Queue Utility (queue.js)

The `Queue` class implements a classic FIFO structure using an array and provides:

- `enqueue(item)` for insertion.
- `dequeue()` for removal from the head.
- `peek()` for reading the head element.
- `size`, `isEmpty()`, and `toArray()` helpers.

This utility gives deterministic insertion-order handling and a clean base for queue-driven workflows.

## Where It Is Used in QuizTime

The copied implementation comes from this original module in QuizTime:

- `src/shared/libs/queue.js`

In the QuizTime application, this queue is used in the toast notification flow to preserve insertion order.

## Code Usage

To see the complete application where this queue-backed flow is used, please visit:

<a href="https://github.com/ApostolQleg/QuizTime"><img src="https://github.com/user-attachments/assets/91c45428-997b-41a3-862a-63a269c5f81b" height="64" align="absmiddle" alt="QuizTime"></a>

## Author

**Oleg Bondarenko**

- **University:** Igor Sikorsky Kyiv Polytechnic Institute (KPI)
- **Faculty:** Faculty of Informatics and Computer Engineering (FICE)
- **Group:** IM-54
- **GitHub:** [@ApostolQleg](https://github.com/ApostolQleg)
