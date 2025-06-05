# Variables and Constant
# Table of Content

- [Variables and Constants](#variables-and-constants)
    - [Difference between var, let and const](difference-between-var,-let-and-const)
    - [Usecase](#usecase)
    - [Variable naming rules](#variable-naming-rules)
- [Scope](#scope)
    - [Types](#types)
        - [Global Scope](#global-scope)
        - [Function Scope](#function-scope)
        - [Block Scope](#block-scope)
    - [Scope Chain and Lexical Scope](#scope-chain-and-lexical-Scope)
- [Hoisting](#hosting)
    - [Var](#var)
    - [Function Declarations](#function-declarations)
    - [let and const Declarations](#let-and-const-declarations)
    - [Temporal Dead Zone](#temporal-dead-zone)


# Variables and Constants

variables are containers that store data values, while constants are variables whose values cannot be changed after they're declared.

There are three ways to declare variables :

```js
var a = 20
let b = "Alex"
const c = 10000
```

# Difference between var, let and const

| var | let | const |
| :- | :- | :- | 
| Function/Global scoped | Block scoped | Block scoped |
| can be redeclared and updated | can be updated but not redclared in same scope | cannot be updated or redeclared |
| Hoisted | Hoisted but not initialized | Hoisted but not initialized |

# Usecase

- Use <kbd>const</kbd> by default for values that won't be reassigned
- Use <kbd>let</kbd> when you need to reassign the variable
- Avoid <kbd>var</kbd> in modern JavaScript due to its confusing scoping rules

# Variable naming rules

- Valid Characters
    - Must start with: letter (a-z, A-Z), underscore (_), or dollar sign ($)
    - Can contain: letters, numbers (0-9), underscores, dollar signs
    - Cannot start with a number
    ```js
    // Valid
    let name;
    let _private;
    let $element;
    let user123;
    let userName;

    // Invalid
    let 123user; // Error: starts with number
    let user-name; // Error: contains hyphen
    let user name; // Error: contains space
    ```
- JavaScript is case-sensitive
    ```js
    let name = "John";
    let Name = "Jane";
    let NAME = "Bob";
    // All three are different variables
    ```
- Reserved Words
    ```js
    // Invalid - these are reserved words
    let function; // Error
    let class; // Error
    let return; // Error
    let if; // Error
    let for; // Error
    ```

# Note

While <kbd>const</kbd> prevents reassignment, <strong>objects</strong> and <strong>arrays</strong> declared with const can still have their contents modified

# Scope
JavaScript scope determines where variables can be accessed in your code.

# Types

# Global Scope
Variables declared outside any function or block have global scope and can be accessed from anywhere in the program.

```js
var globalVar = "I'm global";
let globalLet = "Also global";
const GLOBAL_CONST = "Global constant";

function testFunction() {
    console.log(globalVar); // Accessible
    console.log(globalLet); // Accessible
    console.log(GLOBAL_CONST); // Accessible
}

console.log(globalVar); // Accessible everywhere
```

# Function Scope
Variables declared inside a function are only accessible within that function.

```js
function myFunction() {
    var functionScoped = "Only inside function";
    let alsoFunctionScoped = "Also only inside";
    
    console.log(functionScoped); // Works
    console.log(alsoFunctionScoped); // Works
}

myFunction();
// console.log(functionScoped); // Error: not defined
// console.log(alsoFunctionScoped); // Error: not defined
```

# Block Scope
Variables declared with <kbd>let</kbd> and <kbd>const</kbd> inside a block {} are only accessible within that block.

```js
if (true) {
    var varVariable = "Function scoped";
    let letVariable = "Block scoped";
    const constVariable = "Also block scoped";
    
    console.log(varVariable); // Works
    console.log(letVariable); // Works
    console.log(constVariable); // Works
}

console.log(varVariable); // Works (var is function-scoped)
// console.log(letVariable); // Error: not defined
// console.log(constVariable); // Error: not defined
```

# Scope Chain and Lexical Scope
JavaScript uses lexical scoping, meaning inner functions have access to variables in their outer scope.

```js
function outerFunction() {
    let outerVariable = "I'm outer";
    
    function innerFunction() {
        let innerVariable = "I'm inner";
        
        console.log(outerVariable); // Can access outer scope
        console.log(innerVariable); // Can access own scope
        
        function deeperFunction() {
            console.log(outerVariable); // Can access outer scopes
            console.log(innerVariable); // Can access parent scope
        }
        
        deeperFunction();
    }
    
    innerFunction();
    // console.log(innerVariable); // Error: can't access inner scope
}

outerFunction();
```

# Hositing
Hoisting is a JavaScript behavior where variable and function declarations are moved to the top of their containing scope during the compilation phase, before the code is executed.

# var
<kbd>var</kbd> declarations are hoisted and initialized with <kbd>undefined</kbd>.

```js
console.log(myVar); // undefined (not an error)
var myVar = 5;
console.log(myVar); // 5

// Above code behaves like this:
var myVar; // Hoisted to top, initialized with undefined
console.log(myVar); // undefined
myVar = 5; // Assignment happens here
console.log(myVar); // 5
```

# Function Declarations

```js
sayHello(); // "Hello!" - works before declaration

function sayHello() {
    console.log("Hello!");
}

// Above code behaves like this:
function sayHello() { // Entire function is hoisted
    console.log("Hello!");
}
sayHello(); // "Hello!"
```

# let and const Declarations
<kbd>let</kbd> and <kbd>const</kbd> are hoisted but NOT initialized - they're in the "Temporal Dead Zone".

# Temporal Dead Zone

TDZ, The period between entering scope and the actual declaration where <kbd>let</kbd> and <kbd>const</kbd> variables cannot be accessed.

```js
function example() {
    // TDZ starts here for 'x'
    console.log(x); // ReferenceError
    console.log(y); // ReferenceError
    
    let x = 1; // TDZ ends for 'x'
    const y = 2; // TDZ ends for 'y'
    
    console.log(x); // 1
    console.log(y); // 2
}
```