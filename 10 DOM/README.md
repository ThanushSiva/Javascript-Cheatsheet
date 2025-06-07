# DOM

The Document Object Model (DOM) is a programming interface that represents HTML and XML documents as a structured tree of objects. It provides a way for programs (like JavaScript) to access and manipulate the content, structure, and styling of web documents.

# Table of Contents

- [DOM Tree Structure](#dom-tree-structure)
- [Node Types](#node-types)
- [Selecting Elements](#selecting-elements)
  - [Single Element Selection](#single-element-selection)
  - [Multiple Element Selection](#multiple-element-selection)
  - [Difference HTMLCollection vs NodeList](#difference-htmlcollection-vs-nodelist)
- [Element Properties and Methods](#element-properties-and-methods)
  - [Content Manipulation](#content-manipulation)
  - [Attribute Manipulation](#attribute-manipulation)
  - [CSS and Styling](#css-and-styling)
- [Creating and Manipulating Elements](#creating-and-manipulating-elements)
  - [Creating Elements](#creating-elements)
  - [Adding Elements to DOM](#adding-elements-to-dom)
  - [Removing Elements](#removing-elements)
- [DOM Navigation](#dom-navigation)
  - [Parent Navigation](#parent-navigation)
  - [Child Navigation](#child-navigation)
  - [Sibling Navigation](#sibling-navigation)
- [Events and Event Handling](#events-and-event-handling)
  - [Adding Event Listeners](#adding-event-listeners)
  - [Event Types](#event-types)
  - [Event Object](#event-object)
  - [Event Delegation](#event-delegation)
  - [Custom Events](#custom-events)
- [Form Handling](#form-handling)
  - [Form Elements](#form-elements)
  - [Form Validation](#form-validation)
- [Document Properties and Methods](#document-properties-and-methods)
  - [Document Information](#document-information)
  - [Document Methods](#document-methods)
- [Window Object and BOM](#window-object-and-bom)
  - [Window Properties](#window-properties)
  - [Window Methods](#window-methods)
- [Performance and Best Practices](#performance-and-best-practices)
  - [Efficient DOM Manipulation](#efficient-dom-manipulation)
  - [Caching DOM References](#caching-dom-references)
  - [Event Delegation](#event-delegation)

# DOM Tree Structure

The DOM represents documents as a hierarchical tree where:
- **Document** is the root node
- **Elements** are HTML tags (div, p, h1, etc.)
- **Text nodes** contain the actual text content
- **Attributes** are properties of elements
- **Comments** are also nodes in the tree

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Page</title>
  </head>
  <body>
    <div id="container">
      <p class="text">Hello World</p>
      <!-- This is a comment -->
    </div>
  </body>
</html>
```

# Node Types

The DOM defines several types of nodes:

```javascript
// Common node types
Node.ELEMENT_NODE // 1 - HTML elements
Node.TEXT_NODE // 3 - Text content
Node.COMMENT_NODE // 8 - Comments
Node.DOCUMENT_NODE // 9 - Document itself

// Check node type
if (element.nodeType === Node.ELEMENT_NODE) {
    console.log('This is an element');
}
```

# Selecting Elements

# Single Element Selection
```javascript
// By ID (returns single element or null)
const element = document.getElementById('myId');

// CSS selector (returns first match or null)
const element = document.querySelector('.myClass');
const element = document.querySelector('#myId');
const element = document.querySelector('div.container p');
```

# Multiple Element Selection
```javascript
// By class name (returns HTMLCollection)
const elements = document.getElementsByClassName('myClass');

// By tag name (returns HTMLCollection)
const paragraphs = document.getElementsByTagName('p');

// By name attribute (returns NodeList)
const inputs = document.getElementsByName('username');

// CSS selector all (returns NodeList)
const elements = document.querySelectorAll('.myClass');
const divs = document.querySelectorAll('div');
```

# Difference HTMLCollection vs NodeList
```javascript
// HTMLCollection - live collection, updates automatically
const liveCollection = document.getElementsByClassName('myClass');

// NodeList - can be live or static depending on method
const staticList = document.querySelectorAll('.myClass'); // static
const liveList = document.childNodes; // live

// Convert to array for easier manipulation
const elementsArray = Array.from(elements);
const elementsArray2 = [...elements];
```

# Element Properties and Methods

# Content Manipulation
```javascript
const element = document.getElementById('myDiv');

// Text content (ignores HTML tags)
element.textContent = 'Plain text';
console.log(element.textContent);

// HTML content (parses HTML)
element.innerHTML = '<strong>Bold text</strong>';
console.log(element.innerHTML);

// Outer HTML (includes the element itself)
console.log(element.outerHTML);

// Inner text (respects styling, like hidden elements)
element.innerText = 'Visible text only';
```

# Attribute Manipulation
```javascript
// Get attribute
const value = element.getAttribute('class');

// Set attribute
element.setAttribute('class', 'newClass');
element.setAttribute('data-id', '123');

// Remove attribute
element.removeAttribute('class');

// Check if attribute exists
if (element.hasAttribute('data-id')) {
    console.log('Has data-id attribute');
}

// Direct property access (for standard attributes)
element.id = 'newId';
element.className = 'newClass';
element.src = 'image.jpg';
```

# CSS and Styling
```javascript
// Inline styles
element.style.color = 'red';
element.style.backgroundColor = 'blue';
element.style.fontSize = '16px';

// CSS text (entire style attribute)
element.style.cssText = 'color: red; background: blue;';

// Computed styles (read-only)
const computedStyle = window.getComputedStyle(element);
console.log(computedStyle.color);
console.log(computedStyle.getPropertyValue('font-size'));

// Class manipulation
element.classList.add('newClass');
element.classList.remove('oldClass');
element.classList.toggle('active');
element.classList.contains('myClass'); // returns boolean
element.classList.replace('oldClass', 'newClass');
```

# Creating and Manipulating Elements

# Creating Elements
```javascript
// Create element
const newDiv = document.createElement('div');
const newText = document.createTextNode('Hello');
const newComment = document.createComment('This is a comment');

// Create element with content
const paragraph = document.createElement('p');
paragraph.textContent = 'New paragraph';
paragraph.className = 'highlight';

// Clone elements
const clone = element.cloneNode(true); // true for deep clone
const shallowClone = element.cloneNode(false);
```

# Adding Elements to DOM
```javascript
const parent = document.getElementById('container');
const newElement = document.createElement('div');

// Append as last child
parent.appendChild(newElement);

// Insert at specific position
parent.insertBefore(newElement, parent.firstChild);

// Modern methods (IE not supported)
parent.append(newElement); // can append multiple nodes/strings
parent.prepend(newElement); // insert at beginning
element.before(newElement); // insert before element
element.after(newElement); // insert after element
element.replaceWith(newElement); // replace element

// Insert adjacent HTML
element.insertAdjacentHTML('beforebegin', '<div>Before</div>');
element.insertAdjacentHTML('afterbegin', '<div>Start</div>');
element.insertAdjacentHTML('beforeend', '<div>End</div>');
element.insertAdjacentHTML('afterend', '<div>After</div>');
```

# Removing Elements
```javascript
// Modern way
element.remove();

// Traditional way
parent.removeChild(element);

// Remove all children
element.innerHTML = '';
// or
while (element.firstChild) {
    element.removeChild(element.firstChild);
}
```

# DOM Navigation

# Parent Navigation
```javascript
// Direct parent
const parent = element.parentNode;
const parentElement = element.parentElement; // same but only elements

// Closest ancestor matching selector
const ancestor = element.closest('.container');
```

# Child Navigation
```javascript
// All children (including text nodes)
const children = element.childNodes;

// Only element children
const elementChildren = element.children;

// First and last
const first = element.firstChild; // might be text node
const firstElement = element.firstElementChild;
const last = element.lastChild;
const lastElement = element.lastElementChild;
```

# Sibling Navigation
```javascript
// Next and previous (including text nodes)
const next = element.nextSibling;
const previous = element.previousSibling;

// Next and previous elements only
const nextElement = element.nextElementSibling;
const previousElement = element.previousElementSibling;
```

# Events and Event Handling

# Adding Event Listeners
```javascript
// Modern way (recommended)
element.addEventListener('click', function(event) {
    console.log('Clicked!', event);
});

// Arrow function
element.addEventListener('click', (event) => {
    console.log('Clicked!', event);
});

// Named function (easier to remove)
function handleClick(event) {
    console.log('Clicked!', event);
}
element.addEventListener('click', handleClick);

// With options
element.addEventListener('click', handleClick, {
    once: true, // execute only once
    passive: true, // never calls preventDefault
    capture: true // capture phase
});
```

# Event Types
```javascript
// Mouse events
element.addEventListener('click', handler);
element.addEventListener('dblclick', handler);
element.addEventListener('mousedown', handler);
element.addEventListener('mouseup', handler);
element.addEventListener('mouseover', handler);
element.addEventListener('mouseout', handler);
element.addEventListener('mousemove', handler);

// Keyboard events
document.addEventListener('keydown', handler);
document.addEventListener('keyup', handler);
document.addEventListener('keypress', handler); // deprecated

// Form events
form.addEventListener('submit', handler);
input.addEventListener('change', handler);
input.addEventListener('input', handler);
input.addEventListener('focus', handler);
input.addEventListener('blur', handler);

// Window events
window.addEventListener('load', handler);
window.addEventListener('resize', handler);
window.addEventListener('scroll', handler);
document.addEventListener('DOMContentLoaded', handler);
```

# Event Object
```javascript
element.addEventListener('click', function(event) {
    // Prevent default behavior
    event.preventDefault();
    
    // Stop event bubbling
    event.stopPropagation();
    
    // Event properties
    console.log(event.type); // 'click'
    console.log(event.target); // element that triggered event
    console.log(event.currentTarget); // element with listener
    console.log(event.clientX, event.clientY); // mouse coordinates
    console.log(event.key); // for keyboard events
    
    // Custom event data
    console.log(event.detail);
});
```

# Event Delegation
```javascript
// Instead of adding listeners to many elements
document.getElementById('container').addEventListener('click', function(event) {
    if (event.target.classList.contains('button')) {
        console.log('Button clicked:', event.target.textContent);
    }
});
```

# Custom Events
```javascript
// Create custom event
const customEvent = new CustomEvent('myEvent', {
    detail: { message: 'Hello' },
    bubbles: true,
    cancelable: true
});

// Dispatch event
element.dispatchEvent(customEvent);

// Listen for custom event
element.addEventListener('myEvent', function(event) {
    console.log(event.detail.message);
});
```

# Form Handling

# Form Elements
```javascript
const form = document.getElementById('myForm');
const input = document.getElementById('myInput');
const select = document.getElementById('mySelect');
const checkbox = document.getElementById('myCheckbox');

// Get/set values
console.log(input.value);
input.value = 'new value';

console.log(checkbox.checked);
checkbox.checked = true;

console.log(select.selectedIndex);
console.log(select.options[select.selectedIndex].text);

// Form data
const formData = new FormData(form);
for (let [key, value] of formData.entries()) {
    console.log(key, value);
}
```

# Form Validation
```javascript
// HTML5 validation
input.setCustomValidity('Custom error message');
console.log(input.validity.valid);
console.log(input.validationMessage);

// Form submission
form.addEventListener('submit', function(event) {
    event.preventDefault(); // Prevent default submission
    
    if (form.checkValidity()) {
        // Form is valid
        console.log('Form is valid');
    } else {
        // Form is invalid
        console.log('Form has errors');
    }
});
```

# Document Properties and Methods

### Document Information
```javascript
// Document properties
console.log(document.title);
console.log(document.URL);
console.log(document.domain);
console.log(document.referrer);
console.log(document.lastModified);

// Document state
console.log(document.readyState); // loading, interactive, complete

// Document elements
console.log(document.documentElement); // <html>
console.log(document.head);
console.log(document.body);
```

# Document Methods
```javascript
// Write to document (overwrites existing content)
document.write('<h1>Hello</h1>');

// Create document fragment (for performance)
const fragment = document.createDocumentFragment();
for (let i = 0; i < 1000; i++) {
    const div = document.createElement('div');
    div.textContent = `Item ${i}`;
    fragment.appendChild(div);
}
document.body.appendChild(fragment); // Single DOM update
```

# Window Object and BOM

### Window Properties
```javascript
// Window size
console.log(window.innerWidth, window.innerHeight);
console.log(window.outerWidth, window.outerHeight);

// Screen information
console.log(screen.width, screen.height);
console.log(screen.availWidth, screen.availHeight);

// Location
console.log(window.location.href);
console.log(location.pathname);
console.log(location.search);
console.log(location.hash);
```

# Window Methods
```javascript
// Navigation
window.history.back();
window.history.forward();
window.history.go(-2);

// Popup windows
const popup = window.open('page.html', 'popup', 'width=400,height=300');
popup.close();

// Timers
const timeoutId = setTimeout(() => console.log('Delayed'), 1000);
clearTimeout(timeoutId);

const intervalId = setInterval(() => console.log('Repeating'), 1000);
clearInterval(intervalId);
```

# Performance and Best Practices

# Efficient DOM Manipulation
```javascript
// Bad: Multiple DOM updates
for (let i = 0; i < 1000; i++) {
    const div = document.createElement('div');
    div.textContent = `Item ${i}`;
    document.body.appendChild(div); // 1000 DOM updates
}

// Good: Batch DOM updates
const fragment = document.createDocumentFragment();
for (let i = 0; i < 1000; i++) {
    const div = document.createElement('div');
    div.textContent = `Item ${i}`;
    fragment.appendChild(div);
}
document.body.appendChild(fragment); // 1 DOM update

// Good: Build HTML string
let html = '';
for (let i = 0; i < 1000; i++) {
    html += `<div>Item ${i}</div>`;
}
document.body.innerHTML = html;
```

# Caching DOM References
```javascript
// Bad: Repeated queries
for (let i = 0; i < 100; i++) {
    document.getElementById('myDiv').style.left = i + 'px';
}

// Good: Cache reference
const myDiv = document.getElementById('myDiv');
for (let i = 0; i < 100; i++) {
    myDiv.style.left = i + 'px';
}
```

# Event Delegation
```javascript
// Bad: Multiple event listeners
const buttons = document.querySelectorAll('.button');
buttons.forEach(button => {
    button.addEventListener('click', handleClick);
});

// Good: Single event listener with delegation
document.body.addEventListener('click', function(event) {
    if (event.target.classList.contains('button')) {
        handleClick(event);
    }
});
```