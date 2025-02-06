# React setInterval Memory Leak
This repository demonstrates a common error in React components involving the `setInterval` function within the `useEffect` hook.  Failing to properly clear the interval leads to memory leaks and unexpected behavior.

## Bug Description
The `MyComponent` uses `setInterval` to update a counter every second.  However, the returned function from `setInterval` (which is necessary to stop the interval) is not stored and subsequently never cleared. This results in the interval continuing to run indefinitely, even after the component is unmounted, leading to a memory leak.  The counter continues to increment even when you navigate away from the component.

## Solution
The solution involves storing the interval ID returned by `setInterval` and using it within the cleanup function of the `useEffect` hook. This ensures that the interval is stopped when the component unmounts or when the dependency array changes.