# Objects

Objects are fundamental in JavaScript - they're used for everything from simple data storage to complex applications. They're reference types, mutable, and form the basis for more advanced concepts like classes and prototypes.

# Table of Contents

- [Creating Objects](#creating-objects)
    - [Accessing Object Properties](#accessing-object-properties)
    - [Adding and Modifying Properties](#adding-and-modifying-properties)
    - [Deleting Properties](#deleting-properties)
- [Methods in Objects](#methods-in-objects)
- [Object Destructuring](#object-destructuring)
- [Looping Through Objects](#looping-through-objects)
- [Object Methods](#object-methods)
    - [Computed Property Names](#computed-property-names)
    - [Object Copying](#object-copying)
    - [Checking Object Properties](#checking-object-properties)
- [Nested Objects](#nested-objects)
- [Object Shorthand](#object-shorthand)

# Creating Objects

```js
// Object literal (most common)
let person = {
    name: 'John',
    age: 30,
    city: 'New York'
};

// Object constructor
let person2 = new Object();
person2.name = 'Jane';
person2.age = 25;

// Object.create()
let person3 = Object.create(null); // Creates object with no prototype
person3.name = 'Bob';

// Constructor function
function Person(name, age) {
    this.name = name;
    this.age = age;
}
let person4 = new Person('Alice', 28);
```

# Accessing Object Properties

```js
let car = {
    brand: 'Toyota',
    model: 'Camry',
    year: 2020
};

// Dot notation
console.log(car.brand); // 'Toyota'

// Bracket notation
console.log(car['model']); // 'Camry'

// Dynamic property access
let prop = 'year';
console.log(car[prop]); // 2020
```

# Adding and Modifying Properties

```js
let person = {
    name: 'John',
    age: 30
};

// Adding new properties
person.city = 'Boston';
person['country'] = 'USA';

// Modifying existing properties
person.age = 31;
person['name'] = 'Jonathan';

console.log(person); // {name: 'Jonathan', age: 31, city: 'Boston', country: 'USA'}
```

# Deleting Properties

```js
let obj = {
    a: 1,
    b: 2,
    c: 3
};

delete obj.b;
console.log(obj); // {a: 1, c: 3}

// Check if property exists
console.log('b' in obj); // false
console.log(obj.hasOwnProperty('a')); // true
```

# Methods in Objects

```js
let calculator = {
    result: 0,
    
    add: function(x) {
        this.result += x;
        return this;
    },
    
    multiply(x) { // ES6 shorthand
        this.result *= x;
        return this;
    },
    
    // Arrow functions don't have their own 'this'
    getValue: () => this.result, // Don't use for methods
    
    reset() {
        this.result = 0;
        return this;
    }
};

calculator.add(5).multiply(2); // Method chaining
console.log(calculator.result); // 10
```

# Object Destructuring

```js
let person = {
    name: 'John',
    age: 30,
    city: 'New York',
    country: 'USA'
};

// Basic destructuring
let {name, age} = person;
console.log(name, age); // 'John', 30

// Renaming variables
let {name: fullName, age: years} = person;
console.log(fullName, years); // 'John', 30

// Default values
let {name, profession = 'Unknown'} = person;
console.log(profession); // 'Unknown'

// Rest operator
let {name, ...rest} = person;
console.log(rest); // {age: 30, city: 'New York', country: 'USA'}

// Nested destructuring
let user = {
    id: 1,
    profile: {
        name: 'Alice',
        email: 'alice@email.com'
    }
};
let {profile: {name, email}} = user;
```

# Looping Through Objects

```js
let person = {
    name: 'John',
    age: 30,
    city: 'New York'
};

// For...in loop
for (let key in person) {
    console.log(key, person[key]);
}

// Object.keys()
Object.keys(person).forEach(key => {
    console.log(key, person[key]);
});

// Object.entries()
Object.entries(person).forEach(([key, value]) => {
    console.log(key, value);
});

// Object.values()
Object.values(person).forEach(value => {
    console.log(value);
});
```

# Object Methods

```js
let obj1 = {a: 1, b: 2};
let obj2 = {c: 3, d: 4};

// Object.assign() - shallow copy and merge
let merged = Object.assign({}, obj1, obj2); // {a: 1, b: 2, c: 3, d: 4}

// Spread operator (modern approach)
let merged2 = {...obj1, ...obj2}; // {a: 1, b: 2, c: 3, d: 4}

// Object.keys(), Object.values(), Object.entries()
let person = {name: 'John', age: 30};
console.log(Object.keys(person)); // ['name', 'age']
console.log(Object.values(person)); // ['John', 30]
console.log(Object.entries(person)); // [['name', 'John'], ['age', 30]]

// Object.freeze() - prevent modifications
Object.freeze(person);
person.name = 'Jane'; // Won't work
console.log(person.name); // Still 'John'

// Object.seal() - prevent adding/deleting properties
let car = {brand: 'Toyota'};
Object.seal(car);
car.brand = 'Honda'; // This works
car.model = 'Civic'; // This won't work
```

# Computed Property Names

```js
let prop = 'name';
let value = 'John';

let obj = {
    [prop]: value,
    ['age']: 30,
    [`${prop}Length`]: value.length
};
console.log(obj); // {name: 'John', age: 30, nameLength: 4}
```

# Object Copying

```js
let original = {
    name: 'John',
    age: 30,
    hobbies: ['reading', 'gaming']
};

// Shallow copy
let shallowCopy = {...original};
let shallowCopy2 = Object.assign({}, original);

// Deep copy (for simple objects)
let deepCopy = JSON.parse(JSON.stringify(original));

// Note: JSON method doesn't work with functions, undefined, symbols
```

# Checking Object Properties

```js
let person = {name: 'John', age: 30};

// Check if property exists
console.log('name' in person); // true
console.log(person.hasOwnProperty('name')); // true
console.log(person.name !== undefined); // true

// Check if object is empty
function isEmpty(obj) {
    return Object.keys(obj).length === 0;
}
```

# Nested Objects

```js
let company = {
    name: 'Tech Corp',
    employees: {
        john: {
            position: 'Developer',
            salary: 80000,
            skills: ['JavaScript', 'Python']
        },
        jane: {
            position: 'Designer',
            salary: 70000,
            skills: ['Photoshop', 'Figma']
        }
    }
};

// Accessing nested properties
console.log(company.employees.john.skills[0]); // 'JavaScript'

// Optional chaining (ES2020)
console.log(company.employees?.bob?.salary); // undefined (no error)
```

# Object Shorthand

```js
let name = 'John';
let age = 30;

// Old way
let person1 = {
    name: name,
    age: age
};

// ES6 shorthand
let person2 = {
    name,
    age
};
```