# Control Flow

Control flow in JavaScript refers to the order in which statements are executed in your code. Here are the main control flow structures:

# Table of Contents

- [Conditional Statements](#conditional-statements)
    - [if-else statements](#if-else-statements)
    - [switch statement](#switch-statement)
    - [Ternary operator](#ternary-operator)
- [Loops](#loops)
    - [for loop](#for-loop)
    - [while loop](#for-loop)
    - [do-while loop](#do-while-loop)
    - [for-in loop](#for-in-loop)
    - [for-of-loop](#for-of-loop)
    - [Control Flow Keywords](#control-flow-keywords)
        - [break](#break)
        - [continue](#continue)
        - [return](#return)
- [Exception Handling](#exception-handling)
    - [try-catch-finally](#try-catch-finally)
    - [throw](#throw)

# Conditional Statements

# if-else statements
Execute code based on conditions

```js
if (age >= 18) {
    console.log("You can vote");
} else if (age >= 16) {
    console.log("You can drive");
} else {
    console.log("You're still young");
}
```

# switch statement
Compare a value against multiple cases

```js
switch (day) {
    case 'monday':
        console.log("Start of work week");
        break;
    case 'friday':
        console.log("TGIF!");
        break;
    default:
        console.log("Regular day");
}
```

# Ternary operator
Shorthand for simple if/else

```js
const message = age >= 18 ? "Adult" : "Minor";
```

# Loops

# for loop
Repeat code a specific number of times

```js
for (let i = 0; i < 5; i++) {
    console.log(i);
}

output
0
1
2
3
4
```

# while loop
Repeat while a condition is true

```js
let count = 0;
while (count < 3) {
    console.log(count);
    count++;
}

output
0
1
2
```

# do-while loop
Execute at least once, then repeat while condition is true

```js
let num = 0;
do {
    console.log(num);
    num++;
} while (num < 3);

output
0
1
2
```
# for-in loop
Iterate over object properties

```js
const obj = {a: 1, b: 2, c: 3};
for (let key in obj) {
    console.log(key, obj[key]);
}

output
a 1
b 2
c 3
```

# for-of loop
Iterate over iterable values (arrays, strings, etc.)

```js
const arr = [1, 2, 3];
for (let value of arr) {
    console.log(value);
}

output
1
2
3
```

# Control Flow Keywords

# break
Exit a loop or switch statement early

```js
for (let i = 0; i < 10; i++) {
    if (i === 5) break;
    console.log(i); // Prints 0-4
}
```

# continue
Skip the current iteration and move to the next

```js
for (let i = 0; i < 5; i++) {
    if (i === 2) continue;
    console.log(i); // Prints 0, 1, 3, 4 (skips 2)
}
```

# return
Exit a function and optionally return a value

```js
function checkAge(age) {
    if (age < 0) return "Invalid age";
    if (age >= 18) return "Adult";
    return "Minor";
}
```

# Exception Handling

# try-catch-finally
Handle errors gracefully

```js
try {
    // Code that might throw an error
    let result = riskyOperation();
    console.log(result);
} catch (error) {
    console.log("An error occurred:", error.message);
} finally {
    console.log("This always runs");
}
```

# throw
Manually throw an exception

```js
function divide(a, b) {
    if (b === 0) {
        throw new Error("Division by zero");
    }
    return a / b;
}
```