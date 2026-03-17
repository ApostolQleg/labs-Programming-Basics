# Laboratory Work 1: Generators and Iterators

This repository contains the solution for the first laboratory work on the Fundamentals of Programming. The assignment focuses on understanding and implementing JavaScript generators to produce an infinite sequence of values, and iterators to consume those values within a bounded timeframe.

## Task Description

The objective of this laboratory work is to create two distinct functions:
1. **Generator Function:** Produces an infinite sequence of values.
2. **Timeout Iterator Function:** Consumes the generator's iterator for a strictly limited amount of time.

## Implementation Details

The solution consists of two main modules tailored for a front-end React environment:

### 1. The Generator (`generator.js`)
The file contains an infinite generator function that yields random integer values between 0 and 360. These values represent the hue component in the HSL color model. This fulfills the requirement of creating a random number generator that yields a continuous stream of values.

### 2. The Timeout Iterator (`iterator.js`)
The `startColorAnimation` function serves as the bounded iterator consumer. It accepts an iterator (from the generator), a timeout duration (in milliseconds), and callback functions to update the UI state (`onUpdateReactState` and `onFinishReactState`). 

Instead of a blocking `while` loop, it utilizes `requestAnimationFrame` to non-blockingly consume the iterator over the specified duration. Every 100 milliseconds, it pulls the next hue value from the generator, constructs an HSL string, and triggers a state update to "flash" the color. Once the duration elapses, it pulls one final value, sets the final state, and terminates. It also returns a cleanup function to cancel the animation frame if needed.

## Code Usage

To see how this code is used and integrated into a complete application, please visit:

<a href="https://github.com/ApostolQleg/QuizTime"><img src="https://github.com/user-attachments/assets/91c45428-997b-41a3-862a-63a269c5f81b" height="64" align="absmiddle" alt="QuizTime"></a>

## Author

**Oleg Bondarenko**

- **University:** Igor Sikorsky Kyiv Polytechnic Institute (KPI)
- **Faculty:** Faculty of Informatics and Computer Engineering (FICE)
- **Group:** IM-54
- **GitHub:** [@ApostolQleg](https://github.com/ApostolQleg)
