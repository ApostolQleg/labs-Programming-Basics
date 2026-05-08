# Laboratory Work 6: Asynchronous Iterators and Generators

This repository contains the documentation and extracted implementations for the sixth laboratory work on the Fundamentals of Programming. The assignment topic is asynchronous iterators, generators, and async generators for handling continuous data streams.

## Task Description

The objective of this laboratory work was to understand and implement advanced iteration patterns in JavaScript, including:

- Understanding generators and the `function*` syntax with the `yield` keyword.
- Implementing synchronous iterators for producing sequences of values on demand.
- Understanding async generators with `async function*` for asynchronous value streams.
- Using `for...of` and `for await...of` loops to consume iterators and async generators.
- Implementing long-lived streams with backpressure handling and cancellation via `AbortSignal`.

## Implementation Details

The QuizTime project demonstrates two important use cases of generators and async generators.

### 1. Synchronous Generator

The `generateNickname()` function in QuizTime is a synchronous generator that yields random user nicknames indefinitely.

**Features:**

- **Infinite Sequence:** Uses `while(true)` to produce values on demand forever.
- **Random Generation:** Combines adjectives and nouns with random numbers.
- **Easter Eggs:** Includes special behavior for rare random values (IDs ≤100 or ≥9900).
- **Lazy Evaluation:** Values are only computed when `.next()` is called, not upfront.

This pattern is useful for on-demand generation of unique identifiers or usernames without storing all values in memory.

### 2. Async Generator with Streaming

The `eventsGenerator()` function in QuizTime is an async generator that handles Server-Sent Events (SSE) streaming with support for cancellation.

**Features:**

- **Async Iteration:** Uses `for await...of` to consume async events.
- **Event-Driven:** Wraps Node.js `EventEmitter` using the `on()` helper from `node:events`.
- **Cancellation Support:** Accepts an `AbortSignal` for graceful cleanup.
- **Error Handling:** Distinguishes between intentional aborts and actual errors.
- **Infinite Stream:** Yields events as they arrive from the EventEmitter.

This pattern enables real-time data streaming from event sources while maintaining clean resource cleanup via the AbortController.

## Implementation in QuizTime

The original implementations are located in the QuizTime repository:

- **Backend (Sync Generator):** `src/shared/utils/nicknameGen.js`
    - Used in `src/modules/users/services/nickname.js` to generate unique usernames
    - Provides automatic username generation for new users during registration

- **Backend (Async Generator):** `src/modules/events/services/eventGenerator.js`
    - Used in `src/modules/events/events.controller.js` to stream live quiz updates to connected clients
    - Powers real-time updates: when a quiz is created, updated, or deleted, all connected clients receive the update instantly

## Code Usage

To see the complete application where these iterator patterns are integrated, please visit:

<a href="https://github.com/ApostolQleg/QuizTime"><img src="https://github.com/user-attachments/assets/91c45428-997b-41a3-862a-63a269c5f81b" height="64" align="absmiddle" alt="QuizTime"></a>

## Author

**Oleg Bondarenko**

- **University:** Igor Sikorsky Kyiv Polytechnic Institute (KPI)
- **Faculty:** Faculty of Informatics and Computer Engineering (FICE)
- **Group:** IM-54
- **GitHub:** [@ApostolQleg](https://github.com/ApostolQleg)
