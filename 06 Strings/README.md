# Strings

In JavaScript, strings are sequences of characters used to represent text

# Table of Contents

- [Creating Strings](#creating-strings)
- [Properties and Methods](#properties-and-methods)
    - [Length](#length)
    - [Common Methods](#common-methods)
    - [Template Literals](#template-literals)
    - [String Immutability](#string-immutability)
    - [Escape Characters](#escape-characters)

# Creating Strings

```js
// Single quotes
let str1 = 'Hello world';

// Double quotes
let str2 = "Hello world";

// Template literals (backticks) - allow for interpolation
let name = 'Alice';
let str3 = `Hello ${name}`;

// String constructor (rarely used)
let str4 = new String('Hello world');
```

# Properties and Methods

# Length

```js
let text = "Hello";
console.log(text.length); // 5
```

# Common Methods

```js
let str = "Hello World";

// Case conversion
str.toLowerCase();     // "hello world"
str.toUpperCase();     // "HELLO WORLD"

// Searching
str.indexOf('o');      // 4 (first occurrence)
str.lastIndexOf('o');  // 7 (last occurrence)
str.includes('World'); // true
str.startsWith('Hello'); // true
str.endsWith('World');   // true

// Extracting parts
str.slice(0, 5);       // "Hello"
str.substring(6, 11);  // "World"
str.charAt(0);         // "H"

// Replacing
str.replace('World', 'JavaScript'); // "Hello JavaScript"
str.replaceAll('l', 'x'); // "Hexxo Worxd"

// Splitting and joining
str.split(' ');        // ["Hello", "World"]
str.trim();            // removes whitespace from both ends
```

# Template Literals

Template literals (backticks) are particularly powerful

```js
let name = 'John';
let age = 30;

// Multi-line strings
let message = `Hello ${name},
You are ${age} years old.
Welcome to JavaScript!`;

// Expression evaluation
let result = `The sum is: ${10 + 20}`;
```

# String Immutability

Strings in JavaScript are immutable - methods return new strings rather than modifying the original

```js
let original = "Hello";
let modified = original.toUpperCase();
console.log(original); // "Hello" (unchanged)
console.log(modified); // "HELLO"
```

# Escape Characters

```js
let str = "She said, \"Hello!\""; // Escaped quotes
let path = "C:\\Users\\Name";      // Escaped backslashes
let newline = "Line 1\nLine 2";    // Newline character
```