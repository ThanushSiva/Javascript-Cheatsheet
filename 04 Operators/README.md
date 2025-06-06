# Operators

JavaScript operators are symbols or keywords that perform operations on operands (values and variables). Here's a comprehensive overview of all operator types:

# Table of Contents

- [Arithmetic Operators](#arithmetic-operators)
- [Assignment Operators](#assignment-operators)
- [Comparison Operators](#comparison-operators)
- [Logical Operators](#logical-operators)
- [Conditional Operator](#conditional-operator)
- [Spread and Rest Operators](#spread-and-rest-operators)
- [Optional Chaining and Nullish Coalescing](#optional-chaining-and-nullish-coalescing)
- [Comma Operator](#comma-operator)
- [Operator Precedence](#operator-precedence)
- [Common Operator Patterns](#common-operator-patterns)
    - [Short-circuit Evaluation](#short-circuit-evaluation)
    - [Type Conversion Trick](#type-conversion-trick)
    - [Swapping Variables](#swapping-variables)





# Arithmetic Operators
Perform mathematical operations on numbers.

```js
let a = 10, b = 3;

// Basic arithmetic
console.log(a + b); // 13 (addition)
console.log(a - b); // 7 (subtraction)
console.log(a * b); // 30 (multiplication)
console.log(a / b); // 3.333... (division)
console.log(a % b); // 1 (modulus - remainder)
console.log(a ** b); // 1000 (exponentiation - ES2016)

// Unary operators
console.log(+a); // 10 (unary plus)
console.log(-a); // -10 (unary minus)
console.log(++a); // 11 (pre-increment)
console.log(a++); // 11 (post-increment, then a becomes 12)
console.log(--a); // 11 (pre-decrement)
console.log(a--); // 11 (post-decrement, then a becomes 10)
```

# Assignment Operators
Assign values to variables.

```js
let x = 10;

// Basic assignment
x = 20; // 20

// Compound assignment
x += 5; // x = x + 5 → 25
x -= 3; // x = x - 3 → 22
x *= 2; // x = x * 2 → 44
x /= 4; // x = x / 4 → 11
x %= 3; // x = x % 3 → 2
x **= 3; // x = x ** 3 → 8

// Bitwise compound assignment
x &= 5; // x = x & 5
x |= 3; // x = x | 3
x ^= 2; // x = x ^ 2
x <<= 1; // x = x << 1
x >>= 1; // x = x >> 1
x >>>= 1; // x = x >>> 1

// Logical assignment (ES2021)
x ||= 10; // x = x || 10 (assign if x is falsy)
x &&= 5; // x = x && 5 (assign if x is truthy)
x ??= 20; // x = x ?? 20 (assign if x is null/undefined)
```
# Comparison Operators
Compare values and return boolean results.

```js
let a = 5, b = "5", c = 10;

// Equality
console.log(a == b); // true (loose equality with type coercion)
console.log(a === b); // false (strict equality)
console.log(a != b); // false (loose inequality)
console.log(a !== b); // true (strict inequality)

// Relational
console.log(a < c); // true
console.log(a > c); // false
console.log(a <= c); // true
console.log(a >= c); // false

// String comparison
console.log("apple" < "banana"); // true (lexicographic)
console.log("10" < "9"); // true (string comparison, not numeric)
```

# Logical Operators
Perform logical operations and return boolean values (or the actual operand values).

```js
let a = true, b = false, c = 10, d = 0;

// Logical AND (&&)
console.log(a && b); // false
console.log(c && d); // 0 (returns last falsy or last truthy value)
console.log(c && "hello"); // "hello"

// Logical OR (||)
console.log(a || b); // true
console.log(d || c); // 10 (returns first truthy value)
console.log(d || b || "default"); // "default"

// Logical NOT (!)
console.log(!a); // false
console.log(!d); // true
console.log(!!d); // false (double negation converts to boolean)

// Nullish coalescing (??) - ES2020
let name = null;
console.log(name ?? "Anonymous"); // "Anonymous"
console.log("" ?? "default"); // "" (empty string is not null/undefined)
```

# Conditional Operator
Shorthand for if-else statements.

```js
let age = 18;
let status = age >= 18 ? "adult" : "minor";
console.log(status); // "adult"

// Nested ternary (use sparingly)
let score = 85;
let grade = score >= 90 ? "A" : score >= 80 ? "B" : score >= 70 ? "C" : "F";
console.log(grade); // "B"

// With functions
let max = (a, b) => a > b ? a : b;
console.log(max(10, 5)); // 10
```

# Spread and Rest Operators
Use three dots (...) for different purposes.

```js
// Spread operator - expands iterables
let arr1 = [1, 2, 3];
let arr2 = [4, 5, 6];
let combined = [...arr1, ...arr2]; // [1, 2, 3, 4, 5, 6]

let obj1 = { a: 1, b: 2 };
let obj2 = { c: 3, d: 4 };
let merged = { ...obj1, ...obj2 }; // { a: 1, b: 2, c: 3, d: 4 }

// Function calls
function sum(a, b, c) {
    return a + b + c;
}
console.log(sum(...arr1)); // 6

// Rest operator - collects multiple elements
function collectArgs(first, ...rest) {
    console.log(first); // 1
    console.log(rest); // [2, 3, 4, 5]
}
collectArgs(1, 2, 3, 4, 5);

// Destructuring with rest
let [head, ...tail] = [1, 2, 3, 4];
console.log(head); // 1
console.log(tail); // [2, 3, 4]
```

# Optional Chaining and Nullish Coalescing
Modern operators for safe property access.

```js
let user = {
    name: "John",
    address: {
        street: "Main St",
        city: "New York"
    }
};

// Optional chaining (?.) - ES2020
console.log(user.address?.street); // "Main St"
console.log(user.phone?.number); // undefined (no error)
console.log(user.getName?.()); // undefined (method doesn't exist)

// Array optional chaining
let users = [{ name: "John" }, { name: "Jane" }];
console.log(users?.[0]?.name); // "John"
console.log(users?.[10]?.name); // undefined

// Nullish coalescing assignment
let config = {};
config.timeout ??= 5000; // Only assign if undefined or null
console.log(config.timeout); // 5000
```

# Comma Operator
Evaluates multiple expressions and returns the last one.

```js
let a, b, c;

// Multiple assignments
a = 1, b = 2, c = 3;
console.log(a, b, c); // 1 2 3

// In for loops
for (let i = 0, j = 10; i < 5; i++, j--) {
    console.log(i, j); // 0,10 then 1,9 then 2,8 etc.
}

// Expression evaluation
let result = (console.log("first"), console.log("second"), 42);
console.log(result); // 42 (after logging "first" and "second")
```

# Operator Precedence
Operators have different precedence levels (higher number = higher precedence):

```js
// Example showing precedence
let result = 2 + 3 * 4; // 14, not 20 (multiplication first)
let withParens = (2 + 3) * 4; // 20

// Complex example
let a = 5, b = 10, c = 15;
let complex = a + b * c / 5 - 2; // 5 + (10 * 15 / 5) - 2 = 33

// Assignment has low precedence
let x = y = 5; // y = 5, then x = y (both become 5)
```

# Common Operator Patterns
# Short-circuit Evaluation

```js
// Logical AND for conditional execution
user.isAdmin && performAdminAction();

// Logical OR for default values
let name = user.name || "Anonymous";

// Nullish coalescing for null/undefined only
let timeout = config.timeout ?? 5000;
```

# Type Conversion Tricks

```js
// Convert to number
let num = +stringValue; // Unary plus
let num2 = stringValue * 1; // Multiplication by 1

// Convert to boolean
let bool = !!value; // Double negation
let bool2 = Boolean(value); // Explicit conversion

// Convert to string
let str = value + ""; // Concatenation with empty string
let str2 = String(value); // Explicit conversion
```

# Swapping Variables
```js
// Without temporary variable (using XOR)
let a = 5, b = 10;
a ^= b;
b ^= a;
a ^= b;
console.log(a, b); // 10, 5

// Modern way with destructuring
[a, b] = [b, a];
```
