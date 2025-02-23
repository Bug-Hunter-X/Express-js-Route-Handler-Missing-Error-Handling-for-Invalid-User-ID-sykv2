# Express.js Route Handler Missing Error Handling for Invalid User ID

This repository demonstrates a common error in Express.js route handlers: the lack of proper error handling for invalid input. Specifically, this example shows a route that fetches a user by ID. If the ID is not a valid number, the application will crash. The solution demonstrates how to properly handle such errors and return appropriate HTTP responses.

## Bug

The `bug.js` file contains the flawed code.  The route handler parses the `userId` from the request parameters as an integer using `parseInt()`, but doesn't check if the result is actually a valid number. If the `userId` is not a number (e.g., a string or undefined), `parseInt()` will return `NaN`, and the subsequent `users.find()` call will not find the user, resulting in an unexpected behavior or crash.

## Solution

The `bugSolution.js` file shows the corrected code.  It includes error handling to check if `parseInt(userId)` results in a valid number using `isNaN()`. If the ID is invalid, a 400 Bad Request response is returned.  If the user is not found, a 404 Not Found response is returned.