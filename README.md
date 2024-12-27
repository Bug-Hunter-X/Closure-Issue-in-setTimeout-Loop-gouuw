# JavaScript Closure Issue in setTimeout Loop

This repository demonstrates a common closure-related bug in JavaScript when using `setTimeout` within a loop.  The incorrect behavior stems from how closures capture variables from their surrounding scope.  The solution illustrates how to properly handle this using an immediately invoked function expression (IIFE) to create a new scope for each iteration of the loop.

## Bug
The original code iterates 10 times and you would expect the output to be 0, 1, 2...9. However, due to the asynchronous nature of `setTimeout` and how closures work, all the callbacks end up capturing the final value of `i`, which is 10, and thus 10 is printed 10 times.

## Solution
The solution uses an IIFE to create a new scope for each iteration. This ensures that each callback has its own copy of the current `i` value, preventing the closure issue and leading to the expected output of 0, 1, 2...9.