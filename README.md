# React useEffect Cleanup Function Not Called on Quick Unmount

This repository demonstrates a subtle bug in React's `useEffect` hook where the cleanup function might not be called if the component unmounts too quickly before an asynchronous operation within the effect completes.  This can lead to memory leaks or other unexpected behavior.

## The Bug
The provided `bug.js` file contains a React component that uses `useEffect` to log the current count and performs a cleanup action (logging a cleanup message). If the component is unmounted rapidly (for example, by navigating away from the page very fast), the cleanup function might not be executed, leading to missed cleanup actions.

## The Solution
The `bugSolution.js` file offers a solution to address the problem by using a flag or a mechanism to prevent the cleanup from running if the component is already unmounted or prevents asynchronous operations from updating already unmounted components.

## How to Reproduce
1. Clone this repository.
2. Run `npm install` to install dependencies.
3. Run `npm start` to start the development server.
4. Observe that the cleanup message is logged on every render and only when the component is unmounted gracefully.
5. Try to quickly navigate away from the page to reproduce the issue.

## How to fix
The provided fix should prevent the cleanup function from running if the component is unmounted. Consider using a flag or similar methods to deal with asynchronous operations in the useEffect hook.