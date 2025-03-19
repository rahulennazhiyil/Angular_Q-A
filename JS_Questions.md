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

Core JavaScript Concepts
------------------------
Variable Declaration:
=====================

Declare variables using var, let, and const. Explain their differences and when to use each.
Data Types:

Identify the different data types in JavaScript (numbers, strings, booleans, objects, arrays, null, undefined).
Explain the difference between primitive values and objects.
Operators:

Demonstrate understanding of arithmetic, comparison, logical, assignment, and ternary operators.
Write code examples using these operators.
Control Flow:

Implement if, else, else if, switch, for, while, and do...while statements.
Solve problems using these control flow constructs.
Functions:

Define and call functions with parameters and return values.
Explain the concept of closures and provide an example.
Objects:

Create objects using object literal notation and constructor functions.
Access and modify object properties.
Arrays:

Create and manipulate arrays using methods like push, pop, shift, unshift, slice, splice, concat, join, and reverse.
Implement array iteration using forEach, map, filter, and reduce.
DOM Manipulation
Selecting Elements:

Use getElementById, getElementsByTagName, getElementsByClassName, and querySelector to select elements.
Modifying Elements:

Change element attributes, content, and styles using JavaScript.
Event Handling:

Add event listeners to elements and handle events like clicks, mouseovers, and keypresses.
Asynchronous Programming
Callbacks:

Write code using callbacks to handle asynchronous operations.
Promises:

Create and use promises to manage asynchronous code.
Implement then, catch, and finally methods.
Async/Await:

Use async and await to write asynchronous code in a more synchronous-like manner.
Additional Topics
JSON:

Parse and stringify JSON data.
Regular Expressions:

Use regular expressions to match and manipulate text patterns.
Error Handling:

Implement try...catch blocks to handle errors.
Modules:

Use CommonJS or ES modules to organize code into separate files.

Array Operators
---------------
JavaScript provides a rich set of **array methods** (operators) that allow developers to manipulate arrays in various ways. Here's a categorized list of the most commonly used methods:

---

## 1. **Adding and Removing Elements**

### `push()`
Adds one or more elements to the **end** of an array.
```javascript
const arr = [1, 2, 3];
arr.push(4);
console.log(arr); // [1, 2, 3, 4]
```

### `pop()`
Removes the **last** element from an array and returns it.
```javascript
const arr = [1, 2, 3];
const removed = arr.pop();
console.log(removed); // 3
console.log(arr); // [1, 2]
```

### `unshift()`
Adds one or more elements to the **beginning** of an array.
```javascript
const arr = [2, 3];
arr.unshift(1);
console.log(arr); // [1, 2, 3]
```

### `shift()`
Removes the **first** element from an array and returns it.
```javascript
const arr = [1, 2, 3];
const removed = arr.shift();
console.log(removed); // 1
console.log(arr); // [2, 3]
```

### `splice()`
Adds or removes elements at a specific index.
```javascript
const arr = [1, 2, 3, 4];
arr.splice(1, 2, 99); // Remove 2 elements from index 1 and insert 99
console.log(arr); // [1, 99, 4]
```

---

## 2. **Iterating Over Arrays**

### `forEach()`
Executes a function for each element in the array.
```javascript
const arr = [1, 2, 3];
arr.forEach((num) => console.log(num * 2));
// Output: 2, 4, 6
```

---

## 3. **Searching and Filtering**

### `find()`
Finds the **first** element that matches a condition.
```javascript
const arr = [1, 2, 3, 4];
const found = arr.find(num => num > 2);
console.log(found); // 3
```

### `filter()`
Returns a new array with all elements that match a condition.
```javascript
const arr = [1, 2, 3, 4];
const filtered = arr.filter(num => num > 2);
console.log(filtered); // [3, 4]
```

### `includes()`
Checks if an array contains a specific value.
```javascript
const arr = [1, 2, 3];
console.log(arr.includes(2)); // true
console.log(arr.includes(4)); // false
```

### `indexOf()`
Finds the **first index** of a specific value (or `-1` if not found).
```javascript
const arr = [1, 2, 3, 2];
console.log(arr.indexOf(2)); // 1
```

### `lastIndexOf()`
Finds the **last index** of a specific value.
```javascript
const arr = [1, 2, 3, 2];
console.log(arr.lastIndexOf(2)); // 3
```

---

## 4. **Transforming Arrays**

### `map()`
Creates a new array by applying a function to each element.
```javascript
const arr = [1, 2, 3];
const squared = arr.map(num => num * num);
console.log(squared); // [1, 4, 9]
```

### `reduce()`
Reduces the array to a single value by applying a function.
```javascript
const arr = [1, 2, 3, 4];
const sum = arr.reduce((acc, num) => acc + num, 0);
console.log(sum); // 10
```

### `flat()`
Flattens nested arrays to a specified depth.
```javascript
const arr = [1, [2, [3, [4]]]];
console.log(arr.flat(2)); // [1, 2, 3, [4]]
```

### `flatMap()`
Combines `map()` and `flat()` in one step.
```javascript
const arr = [1, 2, 3];
const result = arr.flatMap(num => [num, num * 2]);
console.log(result); // [1, 2, 2, 4, 3, 6]
```

---

## 5. **Sorting and Reversing**

### `sort()`
Sorts the array (modifies the original array).
```javascript
const arr = [3, 1, 4, 1];
arr.sort();
console.log(arr); // [1, 1, 3, 4]
```
> **Tip**: Use a compare function for numeric sorting.

### `reverse()`
Reverses the order of elements in the array.
```javascript
const arr = [1, 2, 3];
arr.reverse();
console.log(arr); // [3, 2, 1]
```

---

## 6. **Creating and Copying Arrays**

### `slice()`
Returns a shallow copy of a portion of an array.
```javascript
const arr = [1, 2, 3, 4];
const sliced = arr.slice(1, 3);
console.log(sliced); // [2, 3]
```

### `concat()`
Merges two or more arrays into a new array.
```javascript
const arr1 = [1, 2];
const arr2 = [3, 4];
const merged = arr1.concat(arr2);
console.log(merged); // [1, 2, 3, 4]
```

### `from()`
Creates a new array from an iterable or array-like object.
```javascript
const str = "hello";
const arr = Array.from(str);
console.log(arr); // ['h', 'e', 'l', 'l', 'o']
```

### `of()`
Creates an array from a set of arguments.
```javascript
const arr = Array.of(1, 2, 3);
console.log(arr); // [1, 2, 3]
```

---

## 7. **Checking Arrays**

### `isArray()`
Checks if a value is an array.
```javascript
console.log(Array.isArray([1, 2, 3])); // true
console.log(Array.isArray("hello")); // false
```

---

## 8. **Joining Arrays**

### `join()`
Joins array elements into a string.
```javascript
const arr = [1, 2, 3];
const str = arr.join("-");
console.log(str); // "1-2-3"
```

---

### Summary Table of Array Methods:
| Category             | Methods                                                              |
|----------------------|----------------------------------------------------------------------|
| **Adding/Removing**  | `push`, `pop`, `unshift`, `shift`, `splice`                         |
| **Iterating**        | `forEach`                                                           |
| **Searching**        | `find`, `filter`, `includes`, `indexOf`, `lastIndexOf`             |
| **Transforming**     | `map`, `reduce`, `flat`, `flatMap`                                  |
| **Sorting/Reversing**| `sort`, `reverse`                                                   |
| **Creating/Copying** | `slice`, `concat`, `from`, `of`                                     |
| **Checking**         | `isArray`                                                          |
| **Joining**          | `join`                                                             |



## Basic JavaScript Questions
**1. Check if a string is a palindrome**

javascript
Copy
Edit
function isPalindrome(str) {
    const reversed = str.split('').reverse().join('');
    return str === reversed;
}
console.log(isPalindrome("madam")); // true
console.log(isPalindrome("hello")); // false

**2. Difference between var, let, and const**
var is function-scoped and can be redeclared.
let is block-scoped and cannot be redeclared.
const is block-scoped but cannot be reassigned.
Example:

javascript
Copy
Edit
var a = 10;
let b = 20;
const c = 30;

**3. Sort an array of numbers in ascending order**
javascript
Copy
Edit
const numbers = [5, 3, 8, 1];
numbers.sort((a, b) => a - b);
console.log(numbers); // [1, 3, 5, 8]

**4. Remove duplicates from an array**
javascript
Copy
Edit
const removeDuplicates = (arr) => [...new Set(arr)];
console.log(removeDuplicates([1, 2, 3, 2, 4, 1, 5])); // [1, 2, 3, 4, 5]

## Intermediate JavaScript Questions

**5. Factorial using recursion**
javascript
Copy
Edit
function factorial(n) {
    return n === 0 ? 1 : n * factorial(n - 1);
}
console.log(factorial(5)); // 120

**6. Flatten a nested array**
javascript
Copy
Edit
function flattenArray(arr) {
    return arr.flat(Infinity);
}
console.log(flattenArray([1, [2, [3, [4]]]])); // [1, 2, 3, 4]
