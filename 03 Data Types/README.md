# Data Types
# Table of Contents

- [Primitive Data Types](#primitive-data-types)
    - [Number](#number)
    - [String](#string)
    - [Boolean](#boolean)
    - [Undefined](#undefined)
    - [Null](#null)
    - [Symbol](#symbol)
- [Non-Primitive Types](#non-primitive-types)
    - [Object](#object)
    - [Array](#array)
    - [Function](#function)
- [Type Checking](#type-checking)
- [Type Coercion](#type-coercion)
    - [Implicit Coercion](#implicit-coercion)
    - [Explicit Coercion](#explicit-coercion)
- [Falsy and Truthy Values](#falsy-and-truthy-values)
    - [Falsy Values](#falsy-values)
    - [Truthy Values](#truthy-values)
- [Equality Comparison](#equality-comparison)
    - [Types of Equality Comparison](#types-of-equality-comparison)
        - [Loose Equality](#loose-equality)
        - [Strict Equality](#strict-equality)
        - [Loose Inequality](#loose-inequality)
        - [Strict Inequality](#strict-inequality)


JavaScript has several data types that can be categorized into two main groups: Primitive Types and Non-Primitive (Reference) Types.

# Primitive Data Types
Primitive types are immutable and stored by value.

# Number
Represents both integers and floating-point numbers.

```js
let integer = 42;
let float = 3.14159;
let negative = -100;
let scientific = 2.5e6; // 2,500,000
let infinity = 1/0; // Infinity
let negInfinity = -1/0; // -Infinity
let notANumber = "hello" / 2; // NaN (Not a Number)

console.log(typeof 42); // "number"
console.log(Number.MAX_VALUE); // Largest possible number
console.log(Number.MIN_VALUE); // Smallest possible positive number
```
# String
Represents textual data.

```js
let singleQuotes = 'Hello World';
let doubleQuotes = "JavaScript";
let templateLiteral = `Template string with ${singleQuotes}`;
let multiline = `This is a
multiline string`;
let escaped = "She said \"Hello\"";

console.log(typeof "hello"); // "string"
console.log("hello".length); // 5
```

# Boolean
Represents true or false values.

```js
let isTrue = true;
let isFalse = false;
let boolFromComparison = 5 > 3; // true
let boolFromFunction = Boolean(1); // true

console.log(typeof true); // "boolean"
```

# Undefined
Represents a variable that has been declared but not assigned a value.

```js
let notAssigned;
console.log(notAssigned); // undefined
console.log(typeof undefined); // "undefined"

function noReturn() {
    // doesn't return anything
}
console.log(noReturn()); // undefined
```

# Null
Represents an intentional absence of value.

```js
let emptyValue = null;
console.log(emptyValue); // null
console.log(typeof null); // "object" (this is a known bug in JavaScript)
```

# Symbol
Represents a unique identifier.

```js
let sym1 = Symbol();
let sym2 = Symbol("description");
let sym3 = Symbol("description");

console.log(sym2 === sym3); // false (each symbol is unique)
console.log(typeof sym1); // "symbol"

// Symbols as object keys
let obj = {};
obj[sym1] = "value for sym1";
```

# Non-Primitive Types
Non-primitive types are mutable and stored by reference.

# Object
Collection of key-value pairs.

```js
let person = {
    name: "John",
    age: 30,
    isStudent: false,
    address: {
        city: "New York",
        country: "USA"
    }
};

console.log(typeof person); // "object"
console.log(person.name); // "John"
console.log(person["age"]); // 30
```

# Array
Ordered list of values (special type of object).

```js
let numbers = [1, 2, 3, 4, 5];
let mixed = [1, "hello", true, null, {name: "John"}];
let empty = [];

console.log(typeof numbers); // "object"
console.log(Array.isArray(numbers)); // true
console.log(numbers.length); // 5
console.log(numbers[0]); // 1
```

# Function
Reusable blocks of code (special type of object).

```js
function regularFunction() {
    return "Hello";
}

let functionExpression = function() {
    return "World";
};

let arrowFunction = () => "Arrow";

console.log(typeof regularFunction); // "function"
console.log(regularFunction()); // "Hello"
```

# Type Checking

<kbd>typeof</kbd> operator

```js
console.log(typeof 42); // "number"
console.log(typeof "hello"); // "string"
console.log(typeof true); // "boolean"
console.log(typeof undefined); // "undefined"
console.log(typeof null); // "object" (bug)
console.log(typeof Symbol()); // "symbol"
console.log(typeof 123n); // "bigint"
console.log(typeof {}); // "object"
console.log(typeof []); // "object"
console.log(typeof function(){}); // "function"
```

# Type Coercion
JavaScript automatically converts types in certain situations.

# Implicit Coercion
```js
// String coercion
console.log("5" + 3); // "53" (number to string)
console.log("5" - 3); // 2 (string to number)

// Boolean coercion
console.log(Boolean(0)); // false
console.log(Boolean("")); // false
console.log(Boolean(null)); // false
console.log(Boolean(undefined)); // false
console.log(Boolean(NaN)); // false

// Truthy values
console.log(Boolean(1)); // true
console.log(Boolean("hello")); // true
console.log(Boolean([])); // true
console.log(Boolean({})); // true
```

# Explicit Coercion
```js
// To number
let num1 = Number("123"); // 123
let num2 = parseInt("123px"); // 123
let num3 = parseFloat("123.45"); // 123.45
let num4 = +"123"; // 123 (unary plus)

// To string
let str1 = String(123); // "123"
let str2 = (123).toString(); // "123"
let str3 = 123 + ""; // "123"

// To boolean
let bool1 = Boolean(1); // true
let bool2 = !!1; // true (double negation)
```

# Falsy and Truthy Values
# Falsy Values

```js
// These all evaluate to false in boolean context
false
0
-0
0n (BigInt zero)
"" (empty string)
null
undefined
NaN
```

# Truthy Values

```js
true
1, -1, 3.14 (any non-zero number)
"hello", "0", "false" (any non-empty string)
[], {} (arrays and objects, even empty ones)
function(){} (functions)
```

# Equality Comparison
JavaScript has several ways to compare values for equality, each with different behaviors and use cases. Understanding these differences is crucial for writing reliable code.

# Types of Equality Comparison

# Loose Equality
Performs type coercion before comparison.

```js
// Basic examples
console.log(5 == "5"); // true (string converted to number)
console.log(true == 1); // true (boolean converted to number)
console.log(false == 0); // true
console.log(null == undefined); // true (special case)

// More complex examples
console.log("" == 0); // true (empty string to number)
console.log(" " == 0); // true (whitespace string to number)
console.log([] == 0); // true (empty array to number)
console.log([1] == 1); // true (array with one element)
```

# Strict Equality
No type coercion - both value and type must match.

```js
// Type and value must match
console.log(5 === "5"); // false (different types)
console.log(true === 1); // false (different types)
console.log(null === undefined); // false (different types)

// Same type and value
console.log(5 === 5); // true
console.log("hello" === "hello"); // true
console.log(true === true); // true
```

# Loose Inequality
Opposite of <kbd>==</kbd> with type coercion.

```js
console.log(5 != "5"); // false (they are equal after coercion)
console.log(5 != "6"); // true
console.log(null != undefined); // false (they are equal)
```

# Strict Inequality
Opposite of <kbd>===</kbd> without type coercion.

```js
console.log(5 !== "5"); // true (different types)
console.log(5 !== 5); // false (same type and value)
console.log(null !== undefined); // true (different types)
```