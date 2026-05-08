# Laboratory Work 7: Reactive Communication with Observables and EventEmitters

This repository contains the documentation and extracted implementations for the seventh laboratory work on the Fundamentals of Programming. The assignment topic is reactive patterns for event-driven programming using EventEmitters and custom Observable-like patterns.

## Task Description

The objective of this laboratory work was to understand and implement event-driven communication patterns in JavaScript, including:

- Understanding the Observer pattern and EventEmitter from `node:events`.
- Implementing `emit()`, `on()`, `off()`, and `once()` methods for event subscription.
- Creating custom Observable-like patterns with `subscribe()` and `unsubscribe()` methods.
- Managing multiple event listeners and handling concurrent subscriptions.
- Implementing event-driven request/response patterns for real-time communication.

## Implementation Details

The QuizTime project demonstrates both Node.js EventEmitter usage and a custom client-side Observable pattern.

### 1. Node.js EventEmitter (Backend)

The `EventSSE` is a centralized EventEmitter used throughout the QuizTime backend to broadcast real-time events.

**Features:**

- **Event Broadcasting:** Uses `.emit()` to send events to all registered listeners.
- **Event Types:** Handles `SSE_EVENT` events containing formatted event-stream-protocol messages.
- **Listener Management:** Automatically manages listeners (added via `.on()` in other modules).
- **Ping Mechanism:** Implements a periodic ping every 20 seconds to keep SSE connections alive.
- **Type-Specific Emitters:** Provides convenience functions (`emitCreateQuizSSE`, `emitUpdateQuizSSE`, `emitDeleteQuizSSE`) that format and emit domain-specific events.

This demonstrates the Observer pattern at the backend level, where one centralized emitter sends events to many subscribers.

### 2. Custom Observable Pattern (Frontend)

The `SSEClient` is a custom observable-like pattern implemented on the frontend for managing browser-based EventSource subscriptions.

**Features:**

- **Singleton Pattern:** Uses `getInstance()` for a single shared instance across the app.
- **Connection Management:** Handles `connect()` and `disconnect()` for the EventSource lifecycle.
- **Subscription API:** Provides `.subscribe(eventType, callback)` returning an unsubscriber function.
- **Event Parsing:** Automatically parses JSON event data and handles errors.
- **Lazy Listener Registration:** Only registers actual EventSource listeners when `.connect()` is called.
- **Multiple Subscriptions:** Uses a `Map` of `Set`s to support multiple callbacks per event type.

This pattern combines reactive principles (observables) with the browser's EventSource API, providing a clean functional interface with automatic cleanup via unsubscriber functions.

## Implementation in QuizTime

The original implementations are located in the QuizTime repository:

- **Backend:** `src/modules/events/services/observer.js`
    - Exports `EventSSE` (EventEmitter instance)
    - Provides convenience functions: `emitCreateQuizSSE()`, `emitUpdateQuizSSE()`, `emitDeleteQuizSSE()`
    - Maintains a ping mechanism to keep SSE connections alive

- **Frontend:** `src/shared/api/sseClient.js`
    - Exports `sseClient` (singleton instance of SSEClient)
    - Used in `src/app/initEvents.js` to subscribe to quiz events

**Backend Flow:**

1. Database transaction completes (quiz created/updated/deleted)
2. Route handler calls `emitCreateQuizSSE(quiz)` or similar
3. `EventSSE` broadcasts formatted SSE message to all listeners
4. Event stream continues until client disconnects

**Frontend Flow:**

1. App initialization calls `sseClient.connect()` (via `initGlobalEvents()`)
2. Components subscribe: `sseClient.subscribe("CREATE_QUIZ", handleQuizCreated)`
3. When event arrives, callback is invoked with parsed quiz data
4. Component can unsubscribe by calling the returned unsubscriber function

**Real-Time Effect:** When any user creates a quiz:

- Backend emits event → SSE stream → All connected clients receive data simultaneously
- Frontend observable triggers callbacks → UI updates instantly for all users
- This creates a live, synchronized experience across all sessions

## Code Usage

To see the complete application where these event-driven patterns are integrated, please visit:

<a href="https://github.com/ApostolQleg/QuizTime"><img src="https://github.com/user-attachments/assets/91c45428-997b-41a3-862a-63a269c5f81b" height="64" align="absmiddle" alt="QuizTime"></a>

## Author

**Oleg Bondarenko**

- **University:** Igor Sikorsky Kyiv Polytechnic Institute (KPI)
- **Faculty:** Faculty of Informatics and Computer Engineering (FICE)
- **Group:** IM-54
- **GitHub:** [@ApostolQleg](https://github.com/ApostolQleg)
