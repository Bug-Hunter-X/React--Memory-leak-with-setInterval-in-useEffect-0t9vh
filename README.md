# React setInterval memory leak
This example demonstrates a common mistake when using `setInterval` within a React component's `useEffect` hook, resulting in a memory leak. The `setInterval` call is not properly cleaned up when the component unmounts, leading to the interval continuing to run indefinitely even after the component is removed from the DOM.

## Bug
The bug lies in the `MyComponent` function.  The `useEffect` hook sets up an interval using `setInterval` to update the `count` state every second.  However, it fails to provide a cleanup function to `clearInterval` when the component is unmounted.

## Solution
The solution involves returning a cleanup function from the `useEffect` callback.  This function will be executed when the component unmounts, clearing the interval and preventing the memory leak.