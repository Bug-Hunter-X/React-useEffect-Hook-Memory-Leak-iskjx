# React useEffect Hook Memory Leak

This repository demonstrates a common mistake in React's `useEffect` hook that can lead to memory leaks.  The example uses `setInterval` without proper cleanup, resulting in the interval continuing to run even after the component unmounts. This can cause performance issues and memory leaks, especially in applications with many components or frequent component updates.

## Bug Description
The `MyComponent` uses the `useEffect` hook to start an interval that updates a counter every second. However, it fails to include a cleanup function to stop the interval when the component is unmounted. This leads to a memory leak, because the interval continues running indefinitely even when the component is no longer needed.

## Bug Solution
The solution is simple; add a cleanup function to `useEffect` hook that stops the interval when the component is unmounted. This function should return a function that will be executed when the component is unmounted. This function clears the interval using `clearInterval`.