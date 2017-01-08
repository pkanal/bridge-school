## Functional Programming (FP)

### Scope and Closure
* When you first start writing a program in JS, you are in the `Global Scope`. If we define a variable, it will be defined globally.
```javascript
  const number = 1;
```
We generally want to avoid globally scoped variables as you can very quickly run into namespacing issues.

* A local scope refers to any scope defined inside the global scope. Each function defined has its own local scope.
```javascript
  // scope 1: Global scope out here
  const myFunction = () => {
    // scope 2: Local scope in here
  };
```
Locally scoped items are not available to the global scope.

* When we define a function inside a function, the inner function has access to the scope of the outer function. But not the other way around. This is Closure! Thats all it is!!
```javascript
  // scope 1: Global scope out here
  const myFunction = () => {
    // scope 2
    const number = 1;
    const myOtherFunction = () => {
      // scope 3: `number` is accessible here!! We've created a closure because stuff defined in there isnt accessible outside of this function
    };
  };
```

### Pure Functions
* Idempotent: Given the same inputs, an idempotent function will always return the same output.

* Free from side-effects: Pure functions can be safely applied with no side-effects, meaning that they do not mutate any shared state or mutable arguments, and other than their return value, they don’t produce any observable output, including thrown exceptions, triggered events, I/O devices, network, console, display, logs, etc...

Ideally, in functional programming we should use pure functions as much as we can to create composable and reusable units of code.

## Immutability

An immutable value is one that never changes after it has been created. In JavaScript, strings and numbers are immutable by design.
```javascript
  const str = 'Hello world!';
  console.log(str.split(' ')); // ['Hello', 'world!']
  console.log(str) // should still return 'Hello world!' because strings are immutable
```

Objects and arrays (which is a type of object) are not immutable.
```javascript
  let arr = [];
  const newArr = arr.push(2);
  console.log(arr); // [2]
```
Out initial array's value has changed!

## Examples
1. Find all the odd numbers in an array and return a new array containing only those numbers.
**Imperatively**
```javascript
  function getOnlyOddNumbers(array) {
    let newArray = [];
    for(let i = 0; i++; i < array.length) {
      if (array[i] % 2 !== 0) {
        newArr.push(array[i]);
      }
    }

    return newArray;
  }
```

**Functionally**
```javascript
  Array.prototype.filter = (fn) => {
    // write the filter function
  }

  const isOdd = number => number % 2 !== 0;

  function getOnlyOddNumbers(array) {
    return array.filter(isOdd);
  }
```
