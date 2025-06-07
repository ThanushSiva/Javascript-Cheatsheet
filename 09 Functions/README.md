# Functions

A function in JavaScript is a reusable block of code designed to perform a specific task.

# Table of Contents - JavaScript Functions

- [Function Declaration](#function-declaration)
- [Function Expression](#function-expression)
- [Arrow Functions](#arrow-functions)
- [Function Parameters](#function-parameters)
   - [Default Parameters](#default-parameters)
   - [Rest Parameters](#rest-parameters)
   - [Destructuring Parameters](#destructuring-parameters)
- [Higher-Order Functions](#higher-order-functions)
- [Immediately Invoked Function Expression (IIFE)](#immediately-invoked-function-expression-iife)
- [Callback Functions](#callback-functions)
- [Function Methods](#function-methods)
   - [call()](#call)
   - [apply()](#apply)
   - [bind()](#bind)
- [Async Functions](#async-functions)
- [Function Scope and Closures](#function-scope-and-closures)
- [Common Array Methods with Functions](#common-array-methods-with-functions)
- [Best Practices](#best-practices)

# Function Declaration

```javascript
function functionName(parameters) {
    // function body
    return value; // optional
}

// Example
function greet(name) {
    return `Hello, ${name}!`;
}
```

# Function Expression

```javascript
const functionName = function(parameters) {
    // function body
    return value;
};

// Example
const add = function(a, b) {
    return a + b;
};
```

# Arrow Functions

```javascript
// Basic syntax
const functionName = (parameters) => {
    // function body
    return value;
};

// Single parameter (parentheses optional)
const square = x => x * x;

// Multiple parameters
const multiply = (a, b) => a * b;

// No parameters
const sayHello = () => console.log("Hello!");

// Example
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map(num => num * 2);
```

# Function Parameters

# Default Parameters
```javascript
function greet(name = "World") {
    return `Hello, ${name}!`;
}

greet(); // "Hello, World!"
greet("Alice"); // "Hello, Alice!"
```

# Rest Parameters
```javascript
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}

sum(1, 2, 3, 4); // 10
```

# Destructuring Parameters
```javascript
function createUser({name, age, email}) {
    return {
        name,
        age,
        email,
        createdAt: new Date()
    };
}

const user = createUser({
    name: "John",
    age: 30,
    email: "john@example.com"
});
```

# Higher-Order Functions

Functions that take other functions as arguments or return functions

```javascript
// Function that takes another function as parameter
function processArray(arr, callback) {
    return arr.map(callback);
}

const numbers = [1, 2, 3, 4];
const squared = processArray(numbers, x => x * x);

// Function that returns another function
function createMultiplier(factor) {
    return function(number) {
        return number * factor;
    };
}

const double = createMultiplier(2);
const triple = createMultiplier(3);
```

# Immediately Invoked Function Expression (IIFE)

```javascript
(function() {
    console.log("This runs immediately!");
})();

// With parameters
(function(name) {
    console.log(`Hello, ${name}!`);
})("World");

// Arrow function IIFE
(() => {
    console.log("Arrow IIFE");
})();
```

# Callback Functions

```javascript
function fetchData(callback) {
    setTimeout(() => {
        const data = { id: 1, name: "John" };
        callback(data);
    }, 1000);
}

fetchData(function(data) {
    console.log("Received data:", data);
});
```

# Function Methods

# call()
```javascript
function introduce() {
    return `Hi, I'm ${this.name}`;
}

const person = { name: "Alice" };
introduce.call(person); // "Hi, I'm Alice"
```

# apply()
```javascript
function sum(a, b, c) {
    return a + b + c;
}

const numbers = [1, 2, 3];
sum.apply(null, numbers); // 6
```

# bind()
```javascript
function greet() {
    return `Hello, ${this.name}!`;
}

const person = { name: "Bob" };
const boundGreet = greet.bind(person);
boundGreet(); // "Hello, Bob!"
```

# Async Functions

```javascript
// Promise-based function
function fetchUser(id) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (id > 0) {
                resolve({ id, name: "User" + id });
            } else {
                reject(new Error("Invalid ID"));
            }
        }, 1000);
    });
}

// Async/await
async function getUser(id) {
    try {
        const user = await fetchUser(id);
        return user;
    } catch (error) {
        console.error("Error:", error.message);
    }
}
```

# Function Scope and Closures

```javascript
function outerFunction(x) {
    // Outer scope
    
    function innerFunction(y) {
        // Inner scope - has access to outer scope
        return x + y;
    }
    
    return innerFunction;
}

const addFive = outerFunction(5);
addFive(3); // 8
```

# Common Array Methods with Functions

```javascript
const numbers = [1, 2, 3, 4, 5];

// map - transform each element
const doubled = numbers.map(n => n * 2);

// filter - select elements based on condition
const evens = numbers.filter(n => n % 2 === 0);

// reduce - accumulate values
const sum = numbers.reduce((acc, n) => acc + n, 0);

// forEach - execute function for each element
numbers.forEach(n => console.log(n));

// find - find first element matching condition
const found = numbers.find(n => n > 3);

// some - check if any element matches condition
const hasEven = numbers.some(n => n % 2 === 0);

// every - check if all elements match condition
const allPositive = numbers.every(n => n > 0);
```

# Best Practices

- Use arrow functions for short, simple functions
- Use function declarations for main functions that might be hoisted
- Prefer `const` for function expressions to prevent reassignment
- Use descriptive function names
- Keep functions small and focused on a single task
- Use default parameters instead of checking for undefined
- Consider using async/await instead of promise chains for better readability