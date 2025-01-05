# Unexpected State Updates in React's useState Hook

This repository demonstrates a subtle bug in React related to multiple synchronous updates within a single event handler using the `useState` hook.  The issue arises when calling `setCount` multiple times within `handleClick` before the state is re-rendered.  This can result in the state not updating as expected.

The `bug.js` file contains the buggy code. The `bugSolution.js` file shows a solution to address the problem.

## Problem Description

The `handleClick` function in `bug.js` attempts to increment the count by two by calling `setCount` twice in quick succession. However, because React batches state updates, only the final value is applied resulting in an increment of 1 instead of 2. This behavior can be easily overlooked, leading to unexpected behavior in more complex scenarios.

## Solution

The solution involves using the functional update form of `useState` to ensure that the previous state value is always considered when calculating the next state value, thus resolving the unintended behavior caused by synchronous state update overwrites. Refer to `bugSolution.js` for the corrected code.