Core JavaScript Concepts

Question 1: What is the difference between var, let, and const?
* var: Function-scoped, can be re-declared and re-assigned.
* let: Block-scoped, cannot be re-declared, can be re-assigned.
* const: Block-scoped, cannot be re-declared or re-assigned.

Question 2: Explain the concept of hoisting in JavaScript.
* Hoisting is a JavaScript mechanism that moves declarations to the top of their scope. Function declarations are hoisted before variable declarations.

Question 3: What is the difference between == and ===?
* performs type coercion before comparison.
* performs strict comparison, checking both value and type.

Question 4: What is a closure in JavaScript?
*  A closure is a function that has access to variables from its outer (lexical) scope, even after the outer function has finished executing.

Question 5: What is the purpose of the this keyword in JavaScript?
* The this keyword refers to the object that is executing the current function. Its value depends on how the function is called.

JavaScript Objects and Arrays
------------------------------
Question 6: How do you create an object in JavaScript?
* You can create an object using object literal syntax or the new Object() constructor.

Question 7: What is the difference between a primitive value and an object in JavaScript?
* Primitive values are immutable and stored on the stack. Objects are mutable and stored on the heap.

Question 8: How do you iterate over an array in JavaScript?
* You can use a for loop, for...of loop, forEach method, or map method to iterate over an array.

JavaScript Functions and Scope
------------------------------
Question 9: What is a higher-order function in JavaScript?
* A higher-order function is a function that takes one or more functions as arguments or returns a function as a result.   

Question 10: What is the difference between a function declaration and a function expression?
* Function declaration: Hoisted, can be used before declaration.
* Function expression: Not hoisted, cannot be used before declaration.

JavaScript Asynchronous Programming
-----------------------------------
Question 11: What is the difference between synchronous and asynchronous code execution?
* Synchronous code executes line by line, blocking the execution of subsequent code until it finishes.
* Asynchronous code executes non-blocking operations, allowing other code to run while the asynchronous operation is in progress.

Question 12: What is a promise in JavaScript?
*  A promise represents the eventual completion (or failure) of an asynchronous operation and its resulting value.

Question 13: What is the difference between Promise.resolve and Promise.reject?
* Promise.resolve creates a resolved promise.
* Promise.reject creates a rejected promise.

JavaScript DOM Manipulation
---------------------------
Question 14: How do you select an element by its ID in JavaScript?
*  Use the getElementById method.

Question 15: How do you add event listeners to elements in JavaScript?
*  Use the addEventListener method.

Core Array Methods
-------------------

Question 1: What is the difference between forEach, map, filter, and reduce?
* forEach: Iterates over an array, performing a callback function on each element.
* map: Creates a new array by applying a callback function to each element of the original array.
* filter: Creates a new array containing elements from the original array that pass a test implemented by a provided function.
* reduce: Applies a function to an accumulator and each element in the array to reduce it to a single value.

Question 2: How do you create a new array from an existing array without modifying the original array?
*  Use the slice or concat method.

Question 3: How do you reverse the order of elements in an array?
*  Use the reverse method.

Question 4: How do you find the index of a specific element in an array?
*  Use the indexOf method.

Question 5: How do you sort an array in ascending or descending order?
* Use the sort method with a custom comparison function.

Advanced Array Methods
----------------------

Question 6: What is the some method used for?
*  The some method tests whether at least one element in the array passes a test implemented by a provided function.

Question 7: What is the every method used for?
*  The every method tests whether all elements in the array pass a test implemented by a provided function.

Question 8: How do you find the maximum or minimum value in an array?
*  Use the reduce method with a comparison function.

Question 9: What is the find method used for?
*  The find method returns the first element in the array that passes a test implemented by a provided function.

Question 10: What is the findIndex method used for?
*  The findIndex method returns the index of the first element in the array that passes a test implemented by a provided function.
