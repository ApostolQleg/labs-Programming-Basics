# Laboratory Work 3: Memoization and Cache Management

This repository contains the documentation and extracted implementation for the third laboratory work on the Fundamentals of Programming. The assignment topic is memoization and cache eviction behavior.

## Task Description

The objective of this laboratory work was to implement a memoization mechanism for pure functions, including cache storage, lookup by arguments, and cache pruning strategies.

The original academic task mentions multiple configurable policies (LRU, LFU, time-based expiry, custom eviction). In the integrated project implementation, the practical focus was placed on memoization with a bounded cache, TTL expiration, and LRU-style eviction behavior.

## Implementation Details

The implementation is directly copied from the QuizTime project and contains only the core module required for this lab:

### Memoization Utility (memoizer.js)

The `Memoizer` class provides memoization through a `memoize(fn, ttl, capacity)` method and stores per-function caches in a `WeakMap`.

Implemented behavior:

- Argument-based cache keying via JSON serialization of call arguments.
- Time-based expiration through TTL check (`Date.now()` against stored timestamp).
- Capacity-bound pruning by removing the oldest entry when capacity is reached.
- Access-order refresh for reused entries (delete + set), which provides LRU-style recency updates.
- Manual invalidation with `clear(fn, ...args)` and global reset with `clearAll()`.

## Where It Is Used in QuizTime

The copied implementation comes from this original module in QuizTime:

- `src/shared/libs/memoizer.js`

In the QuizTime application, this memoization layer is used in API retrieval modules (quizzes and results) to reduce redundant network requests and improve perceived UI responsiveness.

## Code Usage

To see the full application context where these modules are used, please visit:

<a href="https://github.com/ApostolQleg/QuizTime"><img src="https://github.com/user-attachments/assets/91c45428-997b-41a3-862a-63a269c5f81b" height="64" align="absmiddle" alt="QuizTime"></a>

## Author

**Oleg Bondarenko**

- **University:** Igor Sikorsky Kyiv Polytechnic Institute (KPI)
- **Faculty:** Faculty of Informatics and Computer Engineering (FICE)
- **Group:** IM-54
- **GitHub:** [@ApostolQleg](https://github.com/ApostolQleg)
