# Laboratory Work 5: Asynchronous Programming with Promises

This repository contains the documentation and extracted implementation for the fifth laboratory work on the Fundamentals of Programming. The assignment topic is asynchronous programming and the effective use of promises for managing concurrent operations.

## Task Description

The objective of this laboratory work was to understand and implement asynchronous patterns using JavaScript promises, including:

- Understanding the Promise API: `then()`, `catch()`, and `finally()` methods.
- Implementing promise chaining for sequential asynchronous operations.
- Managing multiple concurrent promises with `Promise.all()`, `Promise.race()`, and `Promise.allSettled()`.
- Deduplicating redundant promise-based requests to avoid unnecessary network calls.
- Error handling in asynchronous contexts with proper fallback mechanisms.

## Implementation Details

The QuizTime project demonstrates a real-world pattern for promise-based request deduplication in its authentication store.

### Promise Deduplication Pattern

The `useAuthStore` from the QuizTime application implements an efficient promise deduplication mechanism to prevent multiple simultaneous API calls for the same operation. This is a practical solution to a common asynchronous challenge.

**Key Features:**

- **Promise Caching:** Uses a module-level `sessionCheckPromise` variable to store the current pending promise.
- **Promise Chaining:** Implements `.then()`, `.catch()`, and `.finally()` for proper error handling and state management.
- **Request Deduplication:** When a session check is already in progress, subsequent calls return the existing promise instead of making new API requests.
- **State Synchronization:** Ensures that data remains consistent even when multiple concurrent operations are pending.
- **Cleanup:** The `.finally()` block clears the cached promise once the request completes.

The pattern demonstrates how to chain promises, handle multiple outcomes (success/error), and manage shared state during async operations—all essential concepts in modern JavaScript development.

## Implementation in QuizTime

The original implementation is located in the QuizTime repository:

- **Backend:** `src/features/auth/stores/authStore.js`

The `checkSession()` method uses a module-level `sessionCheckPromise` variable to cache the current verification request. When multiple components or UI actions trigger session verification simultaneously, only one actual API request is made. All concurrent calls return the same promise, improving performance and reducing server load.

**Key Code Pattern:**

```javascript
let sessionCheckPromise = null;

// Check if verification is already in progress
if (sessionCheckPromise) return sessionCheckPromise;

// Create the promise chain with cleanup
const currentPromise = verifySession()
	.then((data) => {
		/* success */
	})
	.catch((error) => {
		/* error */
	})
	.finally(() => {
		sessionCheckPromise = null; // Clear for next check
	});

sessionCheckPromise = currentPromise;
return currentPromise;
```

## Code Usage

To see the complete application where this promise-based pattern is integrated, please visit:

<a href="https://github.com/ApostolQleg/QuizTime"><img src="https://github.com/user-attachments/assets/91c45428-997b-41a3-862a-63a269c5f81b" height="64" align="absmiddle" alt="QuizTime"></a>

## Author

**Oleg Bondarenko**

- **University:** Igor Sikorsky Kyiv Polytechnic Institute (KPI)
- **Faculty:** Faculty of Informatics and Computer Engineering (FICE)
- **Group:** IM-54
- **GitHub:** [@ApostolQleg](https://github.com/ApostolQleg)
