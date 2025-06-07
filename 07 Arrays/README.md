# Arrays

Arrays in JavaScript are dynamic, zero-indexed, and can hold any type of data. They're objects under the hood, which gives them their flexible properties and methods.

# Table of Contents

- [Creating Arrays](#creating-arrays)
- [Accessing and Modifying Elements](#accessing-and-modifying-elements)
- [Adding and Removing Elements](#adding-and-removing-elements)
- [Common Array Methods](#common-array-methods)
    - [Searching and Testing](#searching-and-testing)
    - [Transforming Arrays](#transforming-arrays)
    - [Combining Arrays](#combining-arrays)
- [Looping Through Arrays](#looping-through-arrays)
- [Multidimensional Arrays](#multidimensional-arrays)
- [Destructuring Arrays](#destructuring-arrays)

# Creating Arrays

```js
// Array literal (most common)
let arr1 = [1, 2, 3, 4, 5];
let arr2 = ['apple', 'banana', 'orange'];
let mixed = [1, 'hello', true, null];

// Array constructor
let arr3 = new Array(5); // Creates array with 5 empty slots
let arr4 = new Array(1, 2, 3); // Creates [1, 2, 3]

// Array.from()
let arr5 = Array.from('hello'); // ['h', 'e', 'l', 'l', 'o']
let arr6 = Array.from({length: 3}, (_, i) => i); // [0, 1, 2]
```

# Accessing and Modifying Elements

```js
let fruits = ['apple', 'banana', 'orange'];

// Accessing
console.log(fruits[0]); // 'apple'
console.log(fruits.length); // 3

// Modifying
fruits[1] = 'grape';
console.log(fruits); // ['apple', 'grape', 'orange']
```

# Adding and Removing Elements

```js
let arr = [1, 2, 3];

// Adding to end
arr.push(4); // [1, 2, 3, 4]
arr.push(5, 6); // [1, 2, 3, 4, 5, 6]

// Adding to beginning
arr.unshift(0); // [0, 1, 2, 3, 4, 5, 6]

// Removing from end
let last = arr.pop(); // Returns 6, arr becomes [0, 1, 2, 3, 4, 5]

// Removing from beginning
let first = arr.shift(); // Returns 0, arr becomes [1, 2, 3, 4, 5]

// Adding/removing at specific index
arr.splice(2, 1); // Remove 1 element at index 2: [1, 2, 4, 5]
arr.splice(2, 0, 3); // Insert 3 at index 2: [1, 2, 3, 4, 5]
arr.splice(1, 2, 'a', 'b'); // Replace 2 elements: [1, 'a', 'b', 4, 5]
```

# Common Array Methods

# Searching and Testing

```js
let numbers = [1, 2, 3, 4, 5];

numbers.indexOf(3); // 2
numbers.includes(4); // true
numbers.find(x => x > 3); // 4
numbers.findIndex(x => x > 3); // 3
numbers.some(x => x > 3); // true
numbers.every(x => x > 0); // true
```

# Transforming Arrays

```js
let numbers = [1, 2, 3, 4, 5];

// Map - transform each element
let doubled = numbers.map(x => x * 2); // [2, 4, 6, 8, 10]

// Filter - keep elements that pass test
let evens = numbers.filter(x => x % 2 === 0); // [2, 4]

// Reduce - reduce to single value
let sum = numbers.reduce((acc, curr) => acc + curr, 0); // 15

// Sort
let words = ['banana', 'apple', 'cherry'];
words.sort(); // ['apple', 'banana', 'cherry']
numbers.sort((a, b) => b - a); // [5, 4, 3, 2, 1] (descending)

// Reverse
numbers.reverse(); // [1, 2, 3, 4, 5]
```

# Combining Arrays

```js
let arr1 = [1, 2];
let arr2 = [3, 4];

// Concat
let combined = arr1.concat(arr2); // [1, 2, 3, 4]

// Spread operator (modern approach)
let combined2 = [...arr1, ...arr2]; // [1, 2, 3, 4]

// Join to string
let str = arr1.join('-'); // "1-2"
```

# Looping Through Arrays

```js
let fruits = ['apple', 'banana', 'orange'];

// For loop
for (let i = 0; i < fruits.length; i++) {
    console.log(fruits[i]);
}

// For...of (values)
for (let fruit of fruits) {
    console.log(fruit);
}

// For...in (indices)
for (let index in fruits) {
    console.log(index, fruits[index]);
}

// forEach
fruits.forEach((fruit, index) => {
    console.log(index, fruit);
});
```

# Multidimensional Arrays

```js
// 2D array
let matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];

console.log(matrix[1][2]); // 6

// Looping through 2D array
for (let row of matrix) {
    for (let cell of row) {
        console.log(cell);
    }
}
```

# Destructuring Arrays

```js
let arr = [1, 2, 3, 4, 5];

// Basic destructuring
let [first, second] = arr; // first = 1, second = 2

// Skip elements
let [a, , c] = arr; // a = 1, c = 3

// Rest operator
let [head, ...tail] = arr; // head = 1, tail = [2, 3, 4, 5]
```

