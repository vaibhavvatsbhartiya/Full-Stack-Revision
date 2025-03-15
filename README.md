# Full Stack Interview Questions

## HTML5 Questions

### 1. What are the new semantic elements introduced in HTML5? Why are they important?

HTML5 introduced several semantic elements that describe their meaning to both browsers and developers:

- `<header>`: Contains introductory content or navigation
- `<nav>`: Contains navigation links
- `<main>`: Specifies the main content area
- `<section>`: Defines a section in a document
- `<article>`: Defines independent, self-contained content
- `<aside>`: Contains content related to surrounding content
- `<footer>`: Contains footer information

These elements are important because they:
- Improve accessibility for screen readers
- Make code more readable and maintainable
- Help search engines understand page structure
- Create a more consistent HTML structure across websites

### 2. What is the purpose of the `<canvas>` element? Have you used it in any projects?

The `<canvas>` element creates a drawing area on a webpage where you can draw graphics using JavaScript. It's like a blank rectangle where you can draw anything programmatically.

Common uses include:
- Creating graphs and charts
- Building games
- Generating dynamic images
- Creating animations

Example:
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');
ctx.fillStyle = 'blue';
ctx.fillRect(10, 10, 100, 100); // Draw a blue square
```

### 3. Describe the difference between `sessionStorage` and `localStorage`.

Both are web storage options that let you store data in the browser, but they differ in persistence and scope:

**localStorage:**
- Persists even after the browser is closed
- Has no expiration time
- Available across browser tabs and windows
- Storage limit of about 5MB
- Data is never sent to the server

**sessionStorage:**
- Data is cleared when the browser tab is closed
- Available only within the same tab
- Storage limit of about 5MB
- Data is never sent to the server

Example usage:
```javascript
// localStorage
localStorage.setItem('username', 'John');
const username = localStorage.getItem('username');

// sessionStorage
sessionStorage.setItem('tempData', 'value');
const tempData = sessionStorage.getItem('tempData');
```

### 4. How do you handle video and audio embedding in HTML5? What attributes are important to consider?

HTML5 provides dedicated `<video>` and `<audio>` elements for embedding media:

**Video embedding:**
```html
<video width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.webm" type="video/webm">
  Your browser does not support the video tag.
</video>
```

**Audio embedding:**
```html
<audio controls>
  <source src="song.mp3" type="audio/mpeg">
  <source src="song.ogg" type="audio/ogg">
  Your browser does not support the audio element.
</audio>
```

Important attributes:
- `controls`: Shows play/pause buttons
- `autoplay`: Starts playing automatically (use with caution)
- `loop`: Repeats the media
- `muted`: Starts with no sound
- `preload`: Hints how much to load before playing
- `poster`: Shows an image before video plays

### 5. What is the `<figure>` and `<figcaption>` tag and when should it be used?

The `<figure>` and `<figcaption>` elements are used to group and provide a caption for self-contained content like images, diagrams, or code snippets.

```html
<figure>
  <img src="chart.jpg" alt="Sales chart">
  <figcaption>Fig.1 - Company sales in Q1 2023</figcaption>
</figure>
```

Use these elements when:
- The content is referenced from the main text
- The content could be moved to an appendix without affecting the flow
- You need to associate a caption with visual content
- You want to improve accessibility by connecting images with their descriptions

### 6. How does HTML5 handle accessibility? What ARIA attributes have you used?

HTML5 improves accessibility through:

1. Semantic elements that clearly describe content purpose
2. Built-in form validation
3. Support for ARIA (Accessible Rich Internet Applications) attributes

Common ARIA attributes:
- `aria-label`: Provides a label for objects that can be read by screen readers
- `aria-labelledby`: Identifies an element that labels the current element
- `aria-hidden`: Hides content from screen readers
- `aria-expanded`: Indicates if a collapsible element is expanded
- `aria-required`: Indicates a field is required
- `role`: Defines the purpose of an element

Example:
```html
<button aria-label="Close" aria-describedby="descriptionClose">X</button>
<div id="descriptionClose">Closes the dialog</div>
```

### 7. Explain the role of Web Workers in HTML5. When would you use them?

Web Workers allow you to run JavaScript in background threads, separate from the main UI thread. They enable true multi-threading in JavaScript.

Use Web Workers when:
- You need to perform CPU-intensive calculations
- You want to keep the UI responsive during heavy processing
- You're handling large data sets
- You need to make complex API calls without freezing the interface

Example:
```javascript
// Main script
const worker = new Worker('worker.js');
worker.onmessage = function(e) {
  console.log('Worker result:', e.data);
};
worker.postMessage({data: 'start calculation'});

// worker.js
onmessage = function(e) {
  // Do heavy calculation
  const result = e.data.data + ' processed';
  postMessage(result);
};
```

### 8. What are the advantages of using the `<picture>` element for responsive images?

The `<picture>` element provides more flexibility for responsive images by allowing you to specify multiple sources based on different conditions:

```html
<picture>
  <source media="(min-width: 1024px)" srcset="large.jpg">
  <source media="(min-width: 768px)" srcset="medium.jpg">
  <img src="small.jpg" alt="Description">
</picture>
```

Advantages:
- Art direction: Show different images based on screen size
- Format flexibility: Provide modern formats (WebP, AVIF) with fallbacks
- Resolution switching: Serve appropriate image sizes for different devices
- Saves bandwidth by loading only the appropriate image
- Improves page load times on mobile devices

### 9. How can you validate HTML5 code?

You can validate HTML5 code using:

1. W3C Markup Validation Service (https://validator.w3.org/)
2. Browser developer tools (look for errors in the console)
3. HTML linters in code editors (ESLint, HTMLHint)
4. Browser extensions for validation
5. Node.js validation tools like `html-validator`

Validation helps:
- Ensure proper rendering across browsers
- Improve accessibility
- Catch syntax errors early
- Maintain standards compliance

### 10. What are some of the new CSS3 features that you find most useful?

CSS3 introduced many powerful features:

- **Flexbox**: For creating flexible layouts
- **Grid**: For complex two-dimensional layouts
- **Animations and Transitions**: For smooth visual effects
- **Media Queries**: For responsive design
- **Custom Properties (Variables)**: For reusable values
- **Gradients**: For smooth color transitions
- **Box Shadow & Text Shadow**: For depth effects
- **Border Radius**: For rounded corners
- **Multiple Backgrounds**: For layered background images
- **Transforms**: For rotating, scaling, and moving elements

Example of border radius and box shadow:
```css
.card {
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}
```

## CSS3 Questions

### 11. Explain the concept of the CSS Box Model.

The CSS Box Model describes how elements are rendered as rectangular boxes. Each box has:

- **Content**: The actual text, image, or other media
- **Padding**: Space between the content and the border
- **Border**: A line around the padding
- **Margin**: Space outside the border

The total width calculation depends on the `box-sizing` property:
- `content-box` (default): width = content width only
- `border-box`: width = content + padding + border

Example:
```css
.box {
  width: 200px;
  padding: 20px;
  border: 5px solid black;
  margin: 10px;
  box-sizing: border-box; /* Width includes padding and border */
}
```

### 12. What is the difference between `display: inline`, `display: block`, and `display: inline-block`?

These display values control how elements behave in the document flow:

**display: block**
- Takes up the full width available
- Creates a new line before and after
- Can have width, height, margin, and padding on all sides
- Examples: `<div>`, `<p>`, `<h1>`

**display: inline**
- Takes only as much width as needed
- Does not create new lines
- Cannot have width, height, or vertical margins
- Examples: `<span>`, `<a>`, `<strong>`

**display: inline-block**
- Combines features of both
- Does not create new lines (like inline)
- Can have width, height, and all margins/padding (like block)
- Examples: `<button>`, `<input>`, `<select>`

### 13. What are media queries, and how are they used in responsive design?

Media queries allow you to apply CSS styles based on device characteristics like screen width, height, or orientation. They're the foundation of responsive design.

Syntax:
```css
@media screen and (max-width: 768px) {
  /* Styles for screens up to 768px wide */
  .container {
    width: 100%;
  }
}
```

Common breakpoints:
- Mobile: up to 600px
- Tablet: 601px to 768px
- Desktop: 769px and above

You can test for:
- Width and height
- Device orientation
- Display type
- Color capability
- Pointer type (touch vs. mouse)

Example of a responsive layout:
```css
.container {
  width: 1200px; /* Desktop default */
}

@media (max-width: 1024px) {
  .container {
    width: 90%; /* Tablet */
  }
}

@media (max-width: 600px) {
  .container {
    width: 100%; /* Mobile */
  }
}
```

### 14. Explain the use of Flexbox and Grid for layout. What are their strengths and weaknesses?

**Flexbox:**
- One-dimensional layout system (row OR column)
- Great for:
  - Navigation menus
  - Card layouts
  - Centering elements
  - Distributing space between items

Example:
```css
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

**Grid:**
- Two-dimensional layout system (rows AND columns)
- Great for:
  - Page layouts
  - Complex grid systems
  - Areas that align both horizontally and vertically

Example:
```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 20px;
}
```

**Strengths/Weaknesses:**

Flexbox:
- ✅ Simple to use for one-dimensional layouts
- ✅ Good browser support
- ❌ Not ideal for complex grid layouts
- ❌ Less control over two-dimensional positioning

Grid:
- ✅ Powerful for complex layouts
- ✅ Better for overall page structure
- ❌ Slightly more complex to learn
- ❌ May require more fallbacks for older browsers

### 15. What is specificity in CSS? How does it affect the styles applied to an element?

Specificity determines which CSS rule applies when multiple rules target the same element. It's calculated as a score based on the selector type:

1. Inline styles (`style` attribute): 1000 points
2. IDs (`#id`): 100 points
3. Classes (`.class`), attributes (`[type="text"]`), and pseudo-classes (`:hover`): 10 points
4. Elements (`div`) and pseudo-elements (`::before`): 1 point

When styles conflict, the one with higher specificity wins. If specificity is equal, the last rule in the CSS file applies.

Examples (from lowest to highest specificity):
```css
div { color: blue; }                    /* Specificity: 1 */
.container p { color: red; }            /* Specificity: 11 */
#sidebar .widget { color: green; }      /* Specificity: 110 */
<div style="color: yellow;">            /* Specificity: 1000 */
```

### 16. Have you used CSS preprocessors like Sass or Less? What are the benefits?

CSS preprocessors extend CSS with programming features. Benefits include:

1. **Variables**: Store colors, fonts, and other values for reuse
   ```scss
   $primary-color: #3498db;
   .button { background: $primary-color; }
   ```

2. **Nesting**: Write cleaner, more organized code
   ```scss
   .navbar {
     background: black;
     ul {
       margin: 0;
       li { display: inline-block; }
     }
   }
   ```

3. **Mixins**: Reuse blocks of styles
   ```scss
   @mixin border-radius($radius) {
     border-radius: $radius;
   }
   .button { @include border-radius(5px); }
   ```

4. **Functions**: Perform calculations and operations
   ```scss
   @function double($value) {
     @return $value * 2;
   }
   .element { width: double(10px); }
   ```

5. **Partials and imports**: Split code into organized files
6. **Extends**: Share styles between selectors
7. **Operators**: Perform math operations

### 17. What are CSS custom properties (variables), and how can they improve code maintainability?

CSS custom properties (also called CSS variables) allow you to store and reuse values throughout your stylesheet:

```css
:root {
  --primary-color: #3498db;
  --secondary-color: #2ecc71;
  --font-size-base: 16px;
}

.button {
  background-color: var(--primary-color);
  font-size: var(--font-size-base);
}
```

Benefits for maintainability:
1. **Centralized values**: Change a value once, it updates everywhere
2. **Theming**: Easily switch between themes
3. **Responsive design**: Update variables with media queries
4. **Consistency**: Maintain uniform colors, spacing, and typography
5. **Readability**: More descriptive than hardcoded values

They're also dynamic - you can change them with JavaScript:
```javascript
document.documentElement.style.setProperty('--primary-color', '#ff0000');
```

### 18. Explain the concept of CSS modules.

CSS Modules are a way to locally scope CSS classes by automatically creating unique class names when you import the CSS file. This prevents style conflicts in large applications.

How it works:
1. You write regular CSS in a `.module.css` file
2. When imported, class names are transformed to be unique
3. You apply these classes using the imported references

Example:
```css
/* Button.module.css */
.button {
  background: blue;
  color: white;
}
```

```javascript
// Button.js
import styles from './Button.module.css';

function Button() {
  return <button className={styles.button}>Click me</button>;
}
```

In the browser, this renders as:
```html
<button class="Button_button_xk7p2">Click me</button>
```

Benefits:
- Prevents class name collisions
- Encapsulates styles with components
- Makes large codebases more maintainable
- Enables easier refactoring

### 19. What are the performance considerations when writing CSS?

Important CSS performance considerations:

1. **Selector Efficiency**:
   - Avoid deeply nested selectors
   - Limit universal selectors (`*`)
   - Be specific but not overly complex

2. **Minimize Repaints and Reflows**:
   - Use `transform` and `opacity` for animations
   - Avoid changing layout properties frequently

3. **Reduce File Size**:
   - Minify CSS
   - Remove unused styles
   - Consider code

### 20. How do you approach debugging CSS layout issues? What tools do you use?

When debugging CSS layout issues, I follow a systematic approach:

1. **Browser Developer Tools**:
   - Element inspector to check applied styles
   - Toggle styles on/off to identify conflicts
   - Use the layout panel to visualize box model
   - Check for CSS Grid/Flexbox visualization tools

2. **Testing Techniques**:
   - Add temporary borders/backgrounds to visualize elements
   - Use `* { outline: 1px solid red; }` to see all elements
   - Test responsive behavior with device emulation

3. **Specialized Tools**:
   - CSS validators to catch syntax errors
   - Browser-specific tools like Firefox's Grid Inspector
   - Extensions like Pesticide for layout debugging

4. **Methodical Process**:
   - Isolate the problem by removing code
   - Test in multiple browsers
   - Create a minimal test case

### 21. What are the different types of selectors in CSS3?

CSS3 offers many selector types to target elements precisely:

1. **Basic Selectors**:
   - Element selector: `div`
   - Class selector: `.classname`
   - ID selector: `#idname`
   - Universal selector: `*`

2. **Combinators**:
   - Descendant: `div p`
   - Child: `div > p`
   - Adjacent sibling: `div + p`
   - General sibling: `div ~ p`

3. **Attribute Selectors**:
   - Has attribute: `[attr]`
   - Exact match: `[attr="value"]`
   - Contains word: `[attr~="value"]`
   - Starts with: `[attr^="value"]`
   - Ends with: `[attr$="value"]`
   - Contains substring: `[attr*="value"]`

4. **Pseudo-classes**:
   - State: `:hover`, `:focus`, `:checked`
   - Structure: `:first-child`, `:last-child`, `:nth-child()`
   - Form: `:valid`, `:invalid`, `:required`

5. **Pseudo-elements**:
   - `::before`, `::after`
   - `::first-line`, `::first-letter`
   - `::selection`

# JavaScript (ES6+) Interview Questions

### 22. Explain the difference between `var`, `let`, and `const` in JavaScript.

These three keywords declare variables but have important differences:

**var:**
- Function-scoped (or global if not in a function)
- Hoisted (can be used before declaration)
- Can be redeclared
- Can be updated

**let:**
- Block-scoped (limited to the block where declared)
- Not hoisted in the same way (exists in a "temporal dead zone")
- Cannot be redeclared in the same scope
- Can be updated

**const:**
- Block-scoped
- Not hoisted in the same way
- Cannot be redeclared in the same scope
- Cannot be reassigned (but object properties can be modified)

Example:
```javascript
function example() {
  // var is function-scoped
  if (true) {
    var x = 10;  // Available in entire function
    let y = 20;  // Only available in this block
    const z = 30;  // Only available in this block
  }
  
  console.log(x);  // 10
  console.log(y);  // ReferenceError: y is not defined
  console.log(z);  // ReferenceError: z is not defined
  
  x = 15;  // Valid
  // z = 35;  // TypeError: Assignment to constant variable
}
```

### 23. What are arrow functions in ES6? What are their advantages and disadvantages?

Arrow functions are a concise syntax for writing functions in ES6:

```javascript
// Traditional function
function add(a, b) {
  return a + b;
}

// Arrow function
const add = (a, b) => a + b;
```

**Advantages:**
1. Shorter syntax, especially for simple functions
2. Implicit return when no curly braces are used
3. Doesn't rebind `this` - inherits from parent scope
4. No need for `.bind()` in callbacks

**Disadvantages:**
1. Can't be used as constructors (no `new` keyword)
2. No `arguments` object available
3. Can't use `yield` inside them (not for generators)
4. Can't change `this` even when needed
5. Less readable for complex functions with multiple operations

Example of `this` binding:
```javascript
// Traditional function rebinds 'this'
const counter = {
  count: 0,
  increaseTraditional: function() {
    setTimeout(function() {
      this.count++;  // 'this' refers to window/global
      console.log(this.count);  // NaN
    }, 1000);
  },
  increaseArrow: function() {
    setTimeout(() => {
      this.count++;  // 'this' refers to counter object
      console.log(this.count);  // 1
    }, 1000);
  }
};
```

### 24. What are template literals, and how do they improve string manipulation in JavaScript?

Template literals (template strings) are a way to create strings in JavaScript using backticks (`) instead of quotes. They offer several improvements:

1. **String interpolation** using `${expression}`:
   ```javascript
   const name = 'John';
   console.log(`Hello, ${name}!`); // "Hello, John!"
   ```

2. **Multi-line strings** without escape characters:
   ```javascript
   const message = `This is a multi-line
   string that doesn't need
   special escaping.`;
   ```

3. **Expression evaluation** inside `${}`:
   ```javascript
   const a = 5;
   const b = 10;
   console.log(`Sum: ${a + b}, Product: ${a * b}`);
   // "Sum: 15, Product: 50"
   ```

4. **Tagged templates** for advanced string processing:
   ```javascript
   function highlight(strings, ...values) {
     return strings.reduce((result, str, i) => {
       return `${result}${str}${values[i] ? `<strong>${values[i]}</strong>` : ''}`;
     }, '');
   }
   
   const name = 'Alice';
   const result = highlight`Hello, ${name}!`;
   // "Hello, <strong>Alice</strong>!"
   ```

### 25. Explain the concept of destructuring in JavaScript.

Destructuring is an ES6 feature that lets you extract values from arrays or properties from objects into distinct variables:

**Array Destructuring:**
```javascript
// Basic array destructuring
const numbers = [1, 2, 3, 4, 5];
const [first, second, ...rest] = numbers;
console.log(first);  // 1
console.log(second); // 2
console.log(rest);   // [3, 4, 5]

// Skipping elements
const [a, , c] = numbers;
console.log(a, c);  // 1 3

// Default values
const [x = 0, y = 0] = [5];
console.log(x, y);  // 5 0

// Swapping variables
let m = 1, n = 2;
[m, n] = [n, m];
console.log(m, n);  // 2 1
```

**Object Destructuring:**
```javascript
// Basic object destructuring
const person = { name: 'John', age: 30, city: 'New York' };
const { name, age } = person;
console.log(name, age);  // "John" 30

// Aliasing properties
const { name: fullName, age: years } = person;
console.log(fullName, years);  // "John" 30

// Default values
const { country = 'USA' } = person;
console.log(country);  // "USA"

// Nested destructuring
const user = {
  id: 42,
  details: {
    firstName: 'Alice',
    job: { title: 'Developer' }
  }
};
const { details: { firstName, job: { title } } } = user;
console.log(firstName, title);  // "Alice" "Developer"
```

### 26. What are promises in JavaScript? How do they help with asynchronous programming?

Promises are objects representing the eventual completion or failure of an asynchronous operation. They help manage asynchronous code in a more readable way than callbacks.

**Basic Promise Structure:**
```javascript
const promise = new Promise((resolve, reject) => {
  // Asynchronous operation
  if (/* operation successful */) {
    resolve(value); // Success
  } else {
    reject(error);  // Failure
  }
});

promise
  .then(value => {
    // Handle success
  })
  .catch(error => {
    // Handle failure
  })
  .finally(() => {
    // Runs regardless of success/failure
  });
```

**Benefits:**
1. **Better flow control** than nested callbacks
2. **Chaining** with `.then()` for sequential async operations
3. **Error handling** with `.catch()`
4. **Promise composition** with `Promise.all()`, `Promise.race()`, etc.

**Example:**
```javascript
function fetchUserData(userId) {
  return fetch(`/api/users/${userId}`)
    .then(response => {
      if (!response.ok) {
        throw new Error('User not found');
      }
      return response.json();
    });
}

fetchUserData(123)
  .then(user => {
    console.log(user);
    return fetchUserData(user.friendId);
  })
  .then(friend => {
    console.log(friend);
  })
  .catch(error => {
    console.error('Error fetching data:', error);
  });
```

### 27. Explain async/await. How do they relate to promises?

Async/await is syntactic sugar built on top of Promises, making asynchronous code look and behave more like synchronous code.

**Basic Structure:**
```javascript
async function functionName() {
  try {
    const result = await promiseReturningFunction();
    // Code here waits until the promise resolves
    return processedResult;
  } catch (error) {
    // Handle errors
  }
}
```

**Key Features:**
1. Functions with the `async` keyword always return a Promise
2. The `await` keyword can only be used inside `async` functions
3. `await` pauses execution until the Promise resolves
4. Errors are handled with try/catch blocks

**Relation to Promises:**
- `async` functions return Promises
- `await` unwraps Promises and pauses until they settle
- Under the hood, it's still using Promises

**Comparison:**
```javascript
// Using Promises
function fetchUserData(userId) {
  return fetch(`/api/users/${userId}`)
    .then(response => response.json())
    .then(user => {
      return fetch(`/api/posts/${user.id}`);
    })
    .then(response => response.json())
    .catch(error => console.error(error));
}

// Using async/await
async function fetchUserData(userId) {
  try {
    const userResponse = await fetch(`/api/users/${userId}`);
    const user = await userResponse.json();
    const postsResponse = await fetch(`/api/posts/${user.id}`);
    const posts = await postsResponse.json();
    return posts;
  } catch (error) {
    console.error(error);
  }
}
```

### 28. What are JavaScript Modules and how are they used?

JavaScript modules are a way to organize code into separate files for better maintainability and reusability. They allow you to export functionality from one file and import it in another.

**Export Syntax:**
```javascript
// Named exports
export function sum(a, b) {
  return a + b;
}

export const PI = 3.14159;

// Default export (one per module)
export default function multiply(a, b) {
  return a * b;
}
```

**Import Syntax:**
```javascript
// Import named exports
import { sum, PI } from './math.js';

// Import default export
import multiply from './math.js';

// Import both
import multiply, { sum, PI } from './math.js';

// Rename imports
import { sum as addition } from './math.js';

// Import all exports as an object
import * as mathUtils from './math.js';
console.log(mathUtils.PI); // 3.14159
```

**Benefits:**
1. **Code organization**: Split code into logical, maintainable files
2. **Encapsulation**: Variables remain in module scope unless exported
3. **Dependency management**: Clear imports show what code depends on
4. **Reusability**: Share code between different parts of an application

**Using in HTML:**
```html
<script type="module" src="app.js"></script>
```

### 29. What is the difference between `==` and `===` in JavaScript?

The difference between `==` and `===` is how strictly they compare values:

**Double Equals (`==`)**:
- Performs type coercion before comparison
- Converts operands to the same type, then compares
- Called "loose equality" or "abstract equality"

**Triple Equals (`===`)**:
- No type coercion
- Values must be the same type and value to be equal
- Called "strict equality" or "identity"

**Examples:**
```javascript
// == (loose equality)
0 == ''      // true ('' converts to 0)
0 == '0'     // true ('0' converts to 0)
1 == true    // true (true converts to 1)
null == undefined  // true (special case)
'10' == 10   // true ('10' converts to 10)

// === (strict equality)
0 === ''     // false (different types)
0 === '0'    // false (different types)
1 === true   // false (different types)
null === undefined  // false (different types)
'10' === 10  // false (different types)

// Both == and === behave the same for same types
10 == 10     // true
10 === 10    // true
'hello' == 'hello'   // true
'hello' === 'hello'  // true
```

Best practice is to use `===` by default to avoid unexpected type coercion issues.

### 30. What is the `this` keyword in JavaScript? How does its value change in different contexts?

The `this` keyword refers to the object it belongs to, but its value changes depending on how a function is called:

1. **In global context**: `this` refers to the global object (window in browsers, global in Node.js)
   ```javascript
   console.log(this); // Window object (in browser)
   ```

2. **In object methods**: `this` refers to the object that owns the method
   ```javascript
   const person = {
     name: 'Alice',
     greet() {
       console.log(`Hello, I'm ${this.name}`);
     }
   };
   person.greet(); // "Hello, I'm Alice"
   ```

3. **In event handlers**: `this` usually refers to the element that received the event
   ```javascript
   button.addEventListener('click', function() {
     console.log(this); // The button element
   });
   ```

4. **In constructor functions**: `this` refers to the newly created instance
   ```javascript
   function User(name) {
     this.name = name;
   }
   const user = new User('Bob');
   console.log(user.name); // "Bob"
   ```

5. **In arrow functions**: `this` is lexically bound (inherits from the parent scope)
   ```javascript
   const obj = {
     name: 'Charlie',
     regularFunction() {
       setTimeout(function() {
         console.log(this.name); // undefined (this = Window)
       }, 100);
     },
     arrowFunction() {
       setTimeout(() => {
         console.log(this.name); // "Charlie" (this = obj)
       }, 100);
     }
   };
   ```

6. **With call/apply/bind**: `this` can be explicitly set
   ```javascript
   function introduce() {
     console.log(`I'm ${this.name}`);
   }
   introduce.call({name: 'Dave'}); // "I'm Dave"
   ```

### 31. Explain the concept of closures in JavaScript.

A closure is when a function "remembers" its lexical scope even when the function is executed outside that scope. In simpler terms, it's a function that can access variables from its outer function even after that outer function has finished running.

**Key aspects:**
1. Functions in JavaScript form closures
2. A closure can access variables defined in its own scope, parent function's scope, and global scope
3. The inner function preserves the scope chain throughout its lifetime

**Example:**
```javascript
function createCounter() {
  let count = 0;  // Private variable
  
  return {
    increment() {
      count++;
      return count;
    },
    decrement() {
      count--;
      return count;
    },
    getValue() {
      return count;
    }
  };
}

const counter = createCounter();
console.log(counter.getValue()); // 0
console.log(counter.increment()); // 1
console.log(counter.increment()); // 2
console.log(counter.decrement()); // 1
```

**Practical uses:**
1. **Data privacy**: Creating private variables
2. **Function factories**: Creating specialized functions
3. **Module pattern**: Encapsulating functionality
4. **Callbacks with preserved state**: Maintaining state between calls

### 32. What are the differences between `map`, `filter`, and `reduce` array methods?

These are three powerful array methods for transforming data:

**map()**:
- Creates a new array with the results of calling a function on every element
- Same length as original array
- Transforms each element

```javascript
const numbers = [1, 2, 3, 4];
const doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8]
```

**filter()**:
- Creates a new array with elements that pass a test function
- Length may be shorter than original
- Selects elements based on a condition

```javascript
const numbers = [1, 2, 3, 4, 5];
const evens = numbers.filter(num => num % 2 === 0);
console.log(evens); // [2, 4]
```

**reduce()**:
- Reduces array to a single value by calling a function with an accumulator
- Returns any type (not necessarily an array)
- Processes all elements to produce a combined result

```javascript
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((total, num) => total + num, 0);
console.log(sum); // 10

// More complex example - grouping objects
const people = [
  {name: 'Alice', age: 25},
  {name: 'Bob', age: 30},
  {name: 'Charlie', age: 25}
];

const groupedByAge = people.reduce((groups, person) => {
  const age = person.age;
  if (!groups[age]) groups[age] = [];
  groups[age].push(person);
  return groups;
}, {});

console.log(groupedByAge);
// { '25': [{name: 'Alice', age: 25}, {name: 'Charlie', age: 25}],
//   '30': [{name: 'Bob', age: 30}] }
```

### 33. What is the event loop in JavaScript?

The event loop is JavaScript's mechanism for handling asynchronous operations. It's what allows JavaScript (a single-threaded language) to perform non-blocking operations.

**Components:**
1. **Call Stack**: Where synchronous code executes
2. **Web APIs**: Browser features like setTimeout, fetch, DOM events
3. **Callback Queue**: Where callbacks wait to be executed
4. **Microtask Queue**: Higher priority queue for Promises
5. **Event Loop**: Checks if the call stack is empty, then moves callbacks to the stack

**How it works:**
1. JavaScript executes synchronous code in the call stack
2. When it encounters asynchronous operations (like setTimeout), they're delegated to Web APIs
3. The call stack continues executing the remaining code
4. When the asynchronous operation completes, its callback goes to the callback queue
5. The event loop checks if the call stack is empty
6. If empty, it moves the first callback from the queue to the stack

**Priority order:**
1. Synchronous code
2. Microtasks (Promise callbacks)
3. Regular callback tasks (setTimeout, events)

**Example:**
```javascript
console.log('Start');

setTimeout(() => {
  console.log('Timeout callback');
}, 0);

Promise.resolve().then(() => {
  console.log('Promise resolved');
});

console.log('End');

// Output:
// Start
// End
// Promise resolved
// Timeout callback
```

### 34. Explain the concept of prototypal inheritance in JavaScript.

Prototypal inheritance is JavaScript's mechanism for sharing properties and methods between objects. Every JavaScript object has a prototype property which is a reference to another object.

**Key concepts:**
1. Objects can inherit properties and methods from other objects
2. The `prototype` property is used to add properties and methods to all instances
3. The prototype chain allows looking up properties through linked objects

**Basic inheritance:**
```javascript
// Constructor function
function Person(name) {
  this.name = name;
}

// Adding to prototype
Person.prototype.greet = function() {
  return `Hello, I'm ${this.name}`;
};

// Create instances
const alice = new Person('Alice');
console.log(alice.greet()); // "Hello, I'm Alice"

// Check inheritance
console.log(alice.__proto__ === Person.prototype); // true
console.log(alice.hasOwnProperty('name')); // true
console.log(alice.hasOwnProperty('greet')); // false
```

**Creating inheritance between objects:**
```javascript
// ES6 Class syntax (still uses prototypes under the hood)
class Animal {
  constructor(name) {
    this.name = name;
  }
  
  speak() {
    return `${this.name} makes a noise`;
  }
}

class Dog extends Animal {
  speak() {
    return `${this.name} barks`;
  }
}

const dog = new Dog('Rex');
console.log(dog.speak()); // "Rex barks"
```

**Object.create method:**
```javascript
const personProto = {
  greet() {
    return `Hello, I'm ${this.name}`;
  }
};

const john = Object.create(personProto);
john.name = 'John';
console.log(john.greet()); // "Hello, I'm John"
```

### 35. How do you handle errors in JavaScript? What are `try...catch` blocks, and when should you use them?

Error handling in JavaScript prevents application crashes and provides better user experience when things go wrong.

**try...catch blocks:**
```javascript
try {
  // Code that might throw an error
  const result = riskyOperation();
} catch (error) {
  // Handle the error
  console.error('An error occurred:', error.message);
} finally {
  // Always executes, regardless of error
  cleanup();
}
```

**When to use try...catch:**
1. **External API calls**: Network requests might fail
2. **Parsing operations**: JSON.parse, XML parsing
3. **File operations**: Reading or writing files (in Node.js)
4. **User input validation**: When strict format is required
5. **Database operations**: Queries might fail

**Types of errors:**
- SyntaxError: Invalid JavaScript syntax
- ReferenceError: Invalid reference (undefined variables)
- TypeError: Operation on an inappropriate type
- RangeError: Number outside valid range
- URIError: Invalid URI parameters
- EvalError: Error in eval() function
- Custom errors: You can create your own

**Creating custom errors:**
```javascript
class ValidationError extends Error {
  constructor(message) {
    super(message);
    this.name = 'ValidationError';
  }
}

try {
  if (!isValid) {
    throw new ValidationError('Invalid data');
  }
} catch (error) {
  if (error instanceof ValidationError) {
    // Handle validation errors
  } else {
    // Handle other errors
  }
}
```

**Async error handling:**
```javascript
// With promises
fetchData()
  .then(result => processData(result))
  .catch(error => console.error(error));

// With async/await
async function getData() {
  try {
    const result = await fetchData();
    return processData(result);
  } catch (error) {
    console.error(error);
  }
}
```

### 36. Describe the concept of hoisting in JavaScript.

Hoisting is JavaScript's behavior of moving declarations to the top of their containing scope during compilation. It allows you to use variables and functions before they're declared in the code.

**Variable hoisting:**
- `var` declarations are hoisted with an initial value of `undefined`
- `let` and `const` declarations are hoisted but not initialized (temporal dead zone)

```javascript
// What you write:
console.log(x); // undefined
var x = 5;
console.log(x); // 5

// How JavaScript interprets it:
var x;
console.log(x); // undefined
x = 5;
console.log(x); // 5

// With let/const (throws error):
console.log(y); // ReferenceError: Cannot access 'y' before initialization
let y = 10;
```

**Function hoisting:**
- Function declarations are completely hoisted (including their definition)
- Function expressions are not hoisted (only the variable if declared with `var`)

```javascript
// Function declaration (works fine)
sayHello(); // "Hello!"
function sayHello() {
  console.log("Hello!");
}

// Function expression (throws error)
sayGoodbye(); // TypeError: sayGoodbye is not a function
var sayGoodbye = function() {
  console.log("Goodbye!");
};

// How JavaScript sees it:
var sayGoodbye;
sayGoodbye(); // Error: not a function yet
sayGoodbye = function() {
  console.log("Goodbye!");
};
```

**Best practices:**
1. Always declare variables at the top of their scope
2. Always declare functions before using them
3. Use `let` and `const` instead of `var` for clearer scope rules

# MERN Stack Interview Questions

### 37. Explain the MERN stack. What are the responsibilities of each component?

The MERN stack is a full-stack JavaScript framework for building web applications, consisting of:

**MongoDB:**
- NoSQL document database
- Stores data in flexible, JSON-like documents
- Responsibilities:
  - Data storage and retrieval
  - Schema design and validation
  - Indexing for performance
  - Horizontal scaling for large applications

**Express.js:**
- Minimal and flexible Node.js web application framework
- Responsibilities:
  - Handling HTTP requests and responses
  - Routing API endpoints
  - Middleware integration for request processing
  - Error handling and logging
  - Server-side validation

**React:**
- Frontend JavaScript library for building user interfaces
- Responsibilities:
  - UI component rendering
  - State management
  - User interaction handling
  - Client-side routing
  - Integration with backend APIs

**Node.js:**
- JavaScript runtime environment for server-side code
- Responsibilities:
  - Running server application
  - Handling connections and requests
  - File system operations
  - Package management via npm
  - Backend business logic

**How they work together:**
- Node.js + Express create a server and API
- MongoDB stores application data
- React consumes API data and renders the UI
- All use JavaScript, making it easier to work across the stack

### 38. Describe your experience building applications using the MERN stack.

When describing MERN stack experience in an interview, structure your answer with specific examples:

"I've built several applications using the MERN stack, including a project management tool similar to Trello. Let me walk you through my approach:

1. **MongoDB**: 
   - Designed a schema for projects, tasks, and users
   - Implemented data validation using Mongoose
   - Created indexes for frequently queried fields

2. **Express.js**:
   - Built RESTful APIs with proper HTTP methods
   - Implemented JWT authentication middleware
   - Set up error handling and request validation

3. **React**:
   - Created reusable components (cards, boards, modals)
   - Managed state using Context API and hooks
   - Implemented drag-and-drop functionality

4. **Node.js**:
   - Set up the server environment
   - Handled file uploads for attachments
   - Created background processes for notifications

5. **Challenges & Solutions**:
   - Optimized API calls to reduce load times
   - Implemented caching strategies
   - Ensured mobile responsiveness"

### 39. What are the advantages of using the MERN stack?

The MERN stack offers several advantages for modern web development:

1. **JavaScript Everywhere**:
   - Single language (JavaScript) across frontend and backend
   - Easier context switching and knowledge sharing
   - Consistent data format (JSON) throughout the stack

2. **Performance**:
   - Node.js is fast and efficient for I/O operations
   - React's virtual DOM minimizes UI updates
   - MongoDB's document model fits well with JavaScript objects

3. **Flexibility and Scalability**:
   - MongoDB scales horizontally for growing applications
   - React components are reusable and maintainable
   - Express is minimal but extensible

4. **Large Ecosystem**:
   - Vast npm package library
   - Strong community support
   - Well-documented components

5. **Real-time Applications**:
   - Easy integration with WebSockets
   - Efficient for real-time data updates

6. **Cost-effective Development**:
   - Open-source tools
   - Single team can work across the stack
   - Faster development cycle

7. **Modern Development Practices**:
   - Component-based architecture
   - API-driven development
   - Microservices friendly

### 40. How do you structure a MERN application? What are some common architectural patterns?

A well-structured MERN application typically follows these patterns:

**Backend Structure (Node.js/Express):**
```
server/
├── config/           # Configuration files
├── controllers/      # Request handlers
├── models/           # MongoDB schemas
├── routes/           # API endpoints
├── middleware/       # Custom middleware
├── utils/            # Helper functions
├── services/         # Business logic
├── tests/            # Test files
└── server.js         # Entry point
```

**Frontend Structure (React):**
```
client/
├── public/           # Static files
├── src/
│   ├── components/   # Reusable UI components
│   ├── pages/        # Page components
│   ├── hooks/        # Custom React hooks
│   ├── context/      # Context API files
│   ├── services/     # API integration
│   ├── utils/        # Helper functions
│   ├── assets/       # Images, fonts, etc.
│   ├── styles/       # Global styles
│   ├── App.js        # Main component
│   └── index.js      # Entry point
└── package.json      # Dependencies
```

**Common Architectural Patterns:**

1. **MVC (Model-View-Controller)**:
   - Models: MongoDB schemas (Mongoose)
   - Views: React components
   - Controllers: Express route handlers

2. **Container/Presentational Pattern**:
   - Container components: Handle data and state
   - Presentational components: Handle UI only

3. **Layered Architecture**:
   - Presentation layer: React components
   - Business logic layer: Services
   - Data access layer: Models/repositories

4. **Feature-based Structure**:
   - Organize by feature rather than technical role
   - Each feature has its own components, hooks, tests

5. **API-First Development**:
   - Design API contracts before implementation
   - Separate API versioning
   - Comprehensive API documentation

6. **Microservices (for larger applications)**:
   - Split backend into smaller, focused services
   - Use API gateway for client requests

## MongoDB Questions

### 41. What are the key features of MongoDB?

MongoDB is a popular NoSQL database with several distinctive features:

1. **Document-Oriented Storage**:
   - Stores data in flexible, JSON-like BSON documents
   - No need for predefined schemas
   - Fields can vary between documents

2. **Dynamic Schema Design**:
   - Add fields on the fly
   - No migrations needed for schema changes
   - Better suited for evolving data models

3. **Horizontal Scalability**:
   - Sharding distributes data across multiple servers
   - Auto-balancing for even data distribution
   - Built for scale from the ground up

4. **High Availability**:
   - Replica sets provide redundancy
   - Automatic failover if primary node fails
   - Self-healing recovery

5. **Indexing**:
   - Support for various index types
   - Compound, geospatial, text, and TTL indexes
   - Index optimization for query performance

6. **Aggregation Framework**:
   - Powerful data processing pipeline
   - Grouping, filtering, and transforming data
   - Complex analytics capabilities 

7. **GridFS**:
   - Storage system for large files
   - Divides files into chunks for efficient storage

8. **Native Drivers**:
   - Official support for many programming languages
   - Optimized for performance with specific languages

9. **Atlas Cloud Service**:
   - Fully-managed MongoDB in the cloud
   - Easy deployment and monitoring

10. **Transactions**:
    - ACID-compliant transactions (since version 4.0)
    - Multi-document transactions

### 42. Explain how to query MongoDB using the MongoDB query language.

MongoDB provides a powerful query language using JSON-like syntax:

**Basic Queries:**
```javascript
// Find all documents in a collection
db.users.find()

// Find with conditions
db.users.find({ age: 25 })

// Find with multiple conditions (AND)
db.users.find({ age: 25, name: "John" })

// Specific fields only (projection)
db.users.find({ age: 25 }, { name: 1, email: 1, _id: 0 })
```

**Comparison Operators:**
```javascript
// Greater than
db.users.find({ age: { $gt: 25 } })

// Less than or equal
db.users.find({ age: { $lte: 30 } })

// In array of values
db.users.find({ status: { $in: ["active", "pending"] } })

// Not equal
db.users.find({ status: { $ne: "inactive" } })
```

**Logical Operators:**
```javascript
// OR condition
db.users.find({ 
  $or: [
    { age: { $lt: 20 } }, 
    { age: { $gt: 60 } }
  ] 
})

// AND condition
db.users.find({ 
  $and: [
    { age: { $gt: 20 } }, 
    { status: "active" }
  ] 
})
```

**Array Queries:**
```javascript
// Array contains element
db.users.find({ hobbies: "reading" })

// Exact array match
db.users.find({ hobbies: ["reading", "swimming"] })

// Array with specific conditions
db.users.find({ "scores.math": { $gt: 80 } })
```

**Update Operations:**
```javascript
// Update one document
db.users.updateOne(
  { _id: ObjectId("123") },
  { $set: { status: "active", lastLogin: new Date() } }
)

// Update many documents
db.users.updateMany(
  { age: { $lt: 18 } },
  { $set: { category: "minor" } }
)
```

**Delete Operations:**
```javascript
// Delete one document
db.users.deleteOne({ status: "inactive" })

// Delete many documents
db.users.deleteMany({ lastLogin: { $lt: new Date('2022-01-01') } })
```

**Aggregation:**
```javascript
db.sales.aggregate([
  // Stage 1: Filter documents
  { $match: { status: "completed" } },
  
  // Stage 2: Group and calculate
  { $group: { 
      _id: "$category", 
      totalSales: { $sum: "$amount" },
      count: { $sum: 1 }
    }
  },
  
  // Stage 3: Sort results
  { $sort: { totalSales: -1 } }
])
```

### 43. How do you design schemas in MongoDB?

While MongoDB is schemaless, thoughtful schema design is still crucial for performance and maintainability:

**Key Schema Design Principles:**

1. **Model Based on Data Access Patterns**:
   - Design for how data will be queried, not just stored
   - Frequently accessed data should be easy to retrieve
   - Optimize for read vs. write operations based on application needs

2. **Embedding vs. Referencing**:
   - **Embedding** (nested documents):
     ```javascript
     {
       _id: 1,
       name: "John",
       address: {
         street: "123 Main St",
         city: "New York",
         zip: "10001"
       },
       orders: [
         { product: "Laptop", price: 1200 },
         { product: "Phone", price: 800 }
       ]
     }
     ```
     - Good for: one-to-few relationships, data that's always accessed together
     - Benefits: retrieves related data in a single query

   - **Referencing** (document relationships):
     ```javascript
     // Users collection
     {
       _id: 1,
       name: "John",
       orderIds: [101, 102, 103]
     }
     
     // Orders collection
     {
       _id: 101,
       userId: 1,
       product: "Laptop",
       price: 1200
     }
     ```
     - Good for: one-to-many or many-to-many relationships
     - Benefits: avoids document size limits, better for frequently changing data

3. **Data Validation with Mongoose**:
   ```javascript
   const UserSchema = new mongoose.Schema({
     name: { 
       type: String, 
       required: true,
       trim: true
     },
     email: {
       type: String,
       required: true,
       unique: true,
       validate: {
         validator: function(v) {
           return /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(v);
         },
         message: props => `${props.value} is not a valid email!`
       }
     },
     age: {
       type: Number,
       min: [18, 'Must be at least 18 years']
     }
   });
   ```

4. **Handling Schema Evolution**:
   - Add new fields without disrupting existing documents
   - Use middleware to update old documents when needed:
   ```javascript
   // Update old documents when they're accessed
   UserSchema.pre('find', function(next) {
     this.update({}, { $set: { lastAccessed: new Date() } });
     next();
   });
   ```

5. **Common Schema Patterns**:
   - **Polymorphic pattern**: Different document structures in same collection
   - **Bucket pattern**: Group related data by time period or category
   - **Computed pattern**: Store calculated values to avoid repeated calculations
   - **Schema versioning**: Track schema versions with a field

### 44. What are indexes in MongoDB, and why are they important?

Indexes in MongoDB are data structures that improve the speed of data retrieval operations. They work similar to indexes in books, helping the database find data without scanning every document.

**Types of Indexes:**

1. **Single Field Index**:
   ```javascript
   db.users.createIndex({ email: 1 }) // 1 for ascending, -1 for descending
   ```

2. **Compound Index** (multiple fields):
   ```javascript
   db.users.createIndex({ lastname: 1, firstname: 1 })
   ```

3. **Multikey Index** (indexes on array values):
   ```javascript
   db.products.createIndex({ tags: 1 }) // tags is an array field
   ```

4. **Text Index** (for text search):
   ```javascript
   db.articles.createIndex({ content: "text" })
   ```

5. **Geospatial Index** (for location data):
   ```javascript
   db.places.createIndex({ location: "2dsphere" })
   ```

6. **Hashed Index** (for hashed values):
   ```javascript
   db.users.createIndex({ _id: "hashed" })
   ```

7. **TTL Index** (expires documents):
   ```javascript
   db.sessions.createIndex({ createdAt: 1 }, { expireAfterSeconds: 3600 })
   ```

**Why Indexes Matter:**

1. **Query Performance**:
   - Dramatically improves search speed
   - Reduces disk I/O and CPU usage
   - Essential for large collections

2. **Sorting Efficiency**:
   - Pre-sorted data for faster sort operations
   - Avoid in-memory sorts which can fail with large data

3. **Unique Constraints**:
   - Enforce data uniqueness
   ```javascript
   db.users.createIndex({ email: 1 }, { unique: true })
   ```

4. **Covered Queries**:
   - Queries satisfied entirely by indexes
   - No need to fetch actual documents

**Index Considerations:**

1. **Write Performance**:
   - Each index requires updates when data changes
   - More indexes = slower write operations

2. **Index Size**:
   - Indexes consume storage space
   - Must fit in RAM for optimal performance

3. **Index Statistics and Optimization**:
   ```javascript
   // Check index usage
   db.users.find({ email: "test@example.com" }).explain("executionStats")
   ```

4. **Background Indexing**:
   - Create indexes without locking the database
   ```javascript
   db.users.createIndex({ name: 1 }, { background: true })
   ```

### 45. How do you handle data validation in MongoDB?

Data validation in MongoDB can be implemented in several ways:

**1. Schema Validation with MongoDB (since v3.6):**
```javascript
db.createCollection("users", {
  validator: {
    $jsonSchema: {
      bsonType: "object",
      required: ["name", "email", "age"],
      properties: {
        name: {
          bsonType: "string",
          description: "must be a string and is required"
        },
        email: {
          bsonType: "string",
          pattern: "^.+@.+$",
          description: "must be a valid email and is required"
        },
        age: {
          bsonType: "int",
          minimum: 18,
          maximum: 99,
          description: "must be an integer between 18 and 99"
        },
        phone: {
          bsonType: "string",
          description: "must be a string if present"
        }
      }
    }
  },
  validationLevel: "strict",
  validationAction: "error"
})
```

**2. Mongoose Validation (in Node.js):**
```javascript
const mongoose = require('mongoose');

const UserSchema = new mongoose.Schema({
  name: {
    type: String,
    required: [true, 'Name is required'],
    trim: true,
    minlength: [2, 'Name must be at least 2 characters']
  },
  email: {
    type: String,
    required: true,
    unique: true,
    lowercase: true,
    validate: {
      validator: function(v) {
        return /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(v);
      },
      message: props => `${props.value} is not a valid email!`
    }
  },
  password: {
    type: String,
    required: true,
    minlength: 8
  },
  role: {
    type: String,
    enum: ['user', 'admin', 'editor'],
    default: 'user'
  },
  createdAt: {
    type: Date,
    default: Date.now,
    immutable: true
  }
});

// Custom validation method
UserSchema.methods.isAdult = function() {
  return this.age >= 18;
};

// Pre-save hook for additional validation
UserSchema.pre('save', function(next) {
  if (this.role === 'admin' && !this.isAdult()) {
    throw new Error('Admin users must be adults');
  }
  next();
});

module.exports = mongoose.model('User', UserSchema);
```

**3. Application-Level Validation:**
```javascript
// Using express-validator middleware
const { body, validationResult } = require('express-validator');

app.post('/users', [
  body('name').isLength({ min: 2 }).withMessage('Name must be at least 2 characters'),
  body('email').isEmail().withMessage('Invalid email format'),
  body('password').isLength({ min: 8 }).withMessage('Password must be at least 8 characters'),
  body('age').isInt({ min: 18 }).withMessage('Must be at least 18 years old')
], (req, res) => {
  const errors = validationResult(req);
  
  if (!errors.isEmpty()) {
    return res.status(400).json({ errors: errors.array() });
  }
  
  // Process valid data
  const user = new User(req.body);
  user.save()
    .then(result => res.status(201).json(result))
    .catch(err => res.status(500).json({ error: err.message }));
});
```

**4. Update Validation:**
```javascript
// Mongoose validation for updates
const updateUser = async (id, updates) => {
  try {
    // runValidators ensures validation runs on update operations
    const options = { new: true, runValidators: true };
    const user = await User.findByIdAndUpdate(id, updates, options);
    return user;
  } catch (error) {
    throw error;
  }
};
```

**Best Practices:**
1. Use multi-layer validation (database + server + client)
2. Keep validation logic consistent across layers
3. Provide meaningful error messages
4. Consider performance impact of complex validators
5. Use appropriate validation levels based on requirements

## Express.js Questions

### 46. What is Express.js? What are its key features?
Express.js is a minimal, flexible web application framework for Node.js that simplifies the process of building web applications and APIs. 

Key features:
- Middleware system for processing HTTP requests
- Simplified routing for handling different HTTP methods and URLs
- Template engine integration for generating HTML
- Error handling mechanisms
- Easy integration with databases
- Minimal structure that gives developers flexibility

### 47. How do you create routes and handle requests in Express.js?
Routes in Express.js define how an application responds to client requests at specific URLs:

```javascript
const express = require('express');
const app = express();

// Basic route responding to GET request
app.get('/hello', (req, res) => {
  res.send('Hello World!');
});

// Route with URL parameters
app.get('/users/:id', (req, res) => {
  const userId = req.params.id;
  res.send(`User ID: ${userId}`);
});

// Handling POST requests
app.post('/data', (req, res) => {
  // Access request body
  console.log(req.body);
  res.send('Data received');
});

app.listen(3000, () => {
  console.log('Server running on port 3000');
});
```

### 48. How do you use middleware in Express.js? Give examples of common middleware.
Middleware functions are functions that have access to the request, response objects, and the next middleware function. They can:
- Execute code
- Make changes to request/response objects 
- End the request-response cycle
- Call the next middleware

Example:
```javascript
const express = require('express');
const app = express();

// Built-in middleware to parse JSON requests
app.use(express.json());

// Custom middleware
app.use((req, res, next) => {
  console.log(`Request received at: ${new Date()}`);
  next(); // Pass control to the next middleware
});

// Route-specific middleware
const authenticate = (req, res, next) => {
  if (req.headers.authorization) {
    next();
  } else {
    res.status(401).send('Unauthorized');
  }
};

app.get('/protected', authenticate, (req, res) => {
  res.send('Protected content');
});
```

Common middleware examples:
- `express.json()` - Parses JSON request bodies
- `express.urlencoded()` - Parses URL-encoded request bodies
- `express.static()` - Serves static files
- `morgan` - HTTP request logger
- `cors` - Handles Cross-Origin Resource Sharing
- `helmet` - Sets security headers

### 49. How do you handle errors in Express.js?
Express provides several ways to handle errors:

1. Using try-catch blocks in route handlers:
```javascript
app.get('/user/:id', async (req, res, next) => {
  try {
    const user = await findUser(req.params.id);
    res.send(user);
  } catch (error) {
    next(error); // Pass error to Express error handler
  }
});
```

2. Creating a centralized error handler middleware (must have 4 parameters):
```javascript
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```

3. Handling 404 errors:
```javascript
// Put this after all routes
app.use((req, res) => {
  res.status(404).send('Route not found');
});
```

# React

### 50. What are React components? What are the different types of components?
React components are reusable, self-contained pieces of code that define a part of the user interface. They encapsulate UI elements, related behavior, and styling.

Types of components:
1. **Functional Components** (now preferred):
   ```jsx
   function Greeting(props) {
     return <h1>Hello, {props.name}!</h1>;
   }
   ```

2. **Class Components**:
   ```jsx
   class Greeting extends React.Component {
     render() {
       return <h1>Hello, {this.props.name}!</h1>;
     }
   }
   ```

3. Components can also be classified based on purpose:
   - **Presentational (UI) Components**: Focus on how things look
   - **Container Components**: Focus on how things work, data fetching
   - **Higher-Order Components (HOCs)**: Functions that take a component and return a new component
   - **Render Props Components**: Share code using a prop whose value is a function

### 51. Explain the concept of the Virtual DOM in React.
The Virtual DOM is a lightweight JavaScript representation of the actual DOM. React uses it to improve performance:

1. When state changes, React creates a new Virtual DOM tree
2. React compares this new tree with the previous Virtual DOM tree (diffing)
3. React calculates the minimal number of changes needed to update the real DOM
4. Only those specific changes are applied to the actual DOM

Benefits:
- Minimizes direct DOM manipulation, which is slow
- Batches updates for better performance
- Handles cross-browser compatibility issues
- Enables declarative programming style

### 52. What is JSX?
JSX (JavaScript XML) is a syntax extension for JavaScript that looks similar to HTML but allows you to write HTML-like code in JavaScript files. React uses JSX to describe what the UI should look like.

Example:
```jsx
const element = <h1 className="greeting">Hello, world!</h1>;
```

Behind the scenes, JSX is transformed into regular JavaScript function calls:
```javascript
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```

Benefits of JSX:
- Easier to visualize UI structure
- Includes JavaScript expressions with curly braces: `{expression}`
- Helps prevent injection attacks
- Makes component code more readable

### 53. How do you manage state in React? What is the difference between `useState` and `useReducer`?
React provides several ways to manage state:

1. **useState Hook**: For simple state management
```jsx
function Counter() {
  const [count, setCount] = useState(0);
  return (
    <>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </>
  );
}
```

2. **useReducer Hook**: For complex state logic
```jsx
function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return {count: state.count + 1};
    case 'decrement':
      return {count: state.count - 1};
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, {count: 0});
  return (
    <>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({type: 'increment'})}>+</button>
      <button onClick={() => dispatch({type: 'decrement'})}>-</button>
    </>
  );
}
```

Differences between `useState` and `useReducer`:
- `useState` is simpler and good for independent state values
- `useReducer` is better for complex state logic with multiple sub-values
- `useReducer` centralizes state update logic
- `useReducer` is more predictable for complex state transitions
- `useState` updates are more direct and straightforward

### 54. What are React Hooks? Give examples of common hooks (`useState`, `useEffect`, `useContext`).
React Hooks are functions that let you use React features (like state) in functional components without writing a class.

1. **useState**: Manages state in function components
```jsx
function NameForm() {
  const [name, setName] = useState('');
  return (
    <>
      <input value={name} onChange={e => setName(e.target.value)} />
      <p>Hello, {name}</p>
    </>
  );
}
```

2. **useEffect**: Handles side effects like data fetching, subscriptions, DOM updates
```jsx
function UserProfile({ userId }) {
  const [user, setUser] = useState(null);
  
  useEffect(() => {
    // Function to fetch user data
    const fetchUser = async () => {
      const response = await fetch(`/api/users/${userId}`);
      const userData = await response.json();
      setUser(userData);
    };
    
    fetchUser();
    
    // Cleanup function (optional)
    return () => {
      // Cancel any pending requests or clean up subscriptions
    };
  }, [userId]); // Dependency array - effect runs when userId changes
  
  if (!user) return <div>Loading...</div>;
  return <div>Name: {user.name}</div>;
}
```

3. **useContext**: Accesses React context without nesting
```jsx
// Create a context
const ThemeContext = React.createContext('light');

// Parent component providing context
function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Toolbar />
    </ThemeContext.Provider>
  );
}

// Child component consuming context
function Toolbar() {
  const theme = useContext(ThemeContext);
  return <div style={{ background: theme === 'dark' ? '#333' : '#fff' }}>Themed Toolbar</div>;
}
```

Other common hooks:
- `useRef`: Creates a mutable reference that persists across renders
- `useCallback`: Memoizes functions to optimize performance
- `useMemo`: Memoizes computed values
- `useReducer`: Alternative to useState for complex state logic

### 55. How do you handle events in React?
React events are named using camelCase and passed as functions:

```jsx
function Button() {
  const handleClick = (event) => {
    event.preventDefault(); // Prevents default browser behavior
    console.log('Button clicked');
  };
  
  return (
    <button onClick={handleClick}>
      Click me
    </button>
  );
}
```

Key aspects of React events:
- React wraps browser events in a cross-browser wrapper (SyntheticEvent)
- Event handlers receive this SyntheticEvent object
- Events need to be bound to the component instance (automatically done in function components)
- For class components, binding is needed:
  ```jsx
  class Button extends React.Component {
    constructor(props) {
      super(props);
      // Binding the method
      this.handleClick = this.handleClick.bind(this);
    }
    
    handleClick() {
      console.log('Clicked');
    }
    
    render() {
      return <button onClick={this.handleClick}>Click me</button>;
    }
  }
  ```

### 56. How do you pass data between components in React?
There are several ways to share data between React components:

1. **Props** (Parent to Child):
```jsx
function Parent() {
  const data = "Hello from parent";
  return <Child message={data} />;
}

function Child({ message }) {
  return <p>{message}</p>;
}
```

2. **Lifting State Up** (Child to Parent):
```jsx
function Parent() {
  const [data, setData] = useState('');
  
  const handleChildData = (childData) => {
    setData(childData);
  };
  
  return (
    <>
      <Child onDataChange={handleChildData} />
      <p>Data from child: {data}</p>
    </>
  );
}

function Child({ onDataChange }) {
  return (
    <button onClick={() => onDataChange('Hello from child')}>
      Send data to parent
    </button>
  );
}
```

3. **Context API** (For components not directly connected):
```jsx
// Create context
const DataContext = React.createContext();

// Provider in parent
function App() {
  const [data, setData] = useState('Shared data');
  
  return (
    <DataContext.Provider value={{ data, setData }}>
      <ComponentA />
      <ComponentB />
    </DataContext.Provider>
  );
}

// Consumer in distant child
function ComponentB() {
  const { data, setData } = useContext(DataContext);
  return (
    <>
      <p>{data}</p>
      <button onClick={() => setData('Updated data')}>Update</button>
    </>
  );
}
```

4. **State Management Libraries** (Redux, Zustand, Recoil) for complex applications

### 57. What is React Router, and how do you use it for navigation?
React Router is a standard library for routing in React applications. It enables navigation between different components while keeping the UI in sync with the URL.

Basic setup:
```jsx
import { BrowserRouter, Routes, Route, Link } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/about">About</Link>
        <Link to="/users">Users</Link>
      </nav>
      
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/users" element={<Users />} />
        <Route path="/users/:id" element={<UserDetails />} />
        <Route path="*" element={<NotFound />} />
      </Routes>
    </BrowserRouter>
  );
}
```

Accessing URL parameters:
```jsx
import { useParams } from 'react-router-dom';

function UserDetails() {
  const { id } = useParams();
  return <h1>User Details for user {id}</h1>;
}
```

Programmatic navigation:
```jsx
import { useNavigate } from 'react-router-dom';

function LoginButton() {
  const navigate = useNavigate();
  
  const handleLogin = () => {
    // After successful login
    navigate('/dashboard');
  };
  
  return <button onClick={handleLogin}>Log In</button>;
}
```

### 58. What are some techniques for optimizing React application performance?
React performance optimization techniques:

1. **Use React.memo for component memoization**:
```jsx
const MemoizedComponent = React.memo(function MyComponent(props) {
  // Only re-renders if props change
  return <div>{props.name}</div>;
});
```

2. **Use useCallback for memoizing functions**:
```jsx
const memoizedCallback = useCallback(() => {
  doSomething(a, b);
}, [a, b]); // Only recreates if a or b changes
```

3. **Use useMemo for expensive calculations**:
```jsx
const memoizedValue = useMemo(() => {
  return computeExpensiveValue(a, b);
}, [a, b]);
```

4. **Code splitting with dynamic imports**:
```jsx
const LazyComponent = React.lazy(() => import('./LazyComponent'));

function App() {
  return (
    <React.Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </React.Suspense>
  );
}
```

5. **Virtualization for long lists** (using libraries like `react-window`):
```jsx
import { FixedSizeList } from 'react-window';

function List({ items }) {
  const Row = ({ index, style }) => (
    <div style={style}>Item {items[index]}</div>
  );
  
  return (
    <FixedSizeList
      height={500}
      width={300}
      itemCount={items.length}
      itemSize={50}
    >
      {Row}
    </FixedSizeList>
  );
}
```

6. **Use proper keys in lists**
7. **Avoid inline functions in renders**
8. **Prevent unnecessary re-renders by managing state carefully**
9. **Use production build for deployment**
10. **Web workers for CPU-intensive tasks**

# Node.js 

### 59. What is Node.js? What are its key features? (continued)
Key features:
- **Event-driven, non-blocking I/O model** - makes it lightweight and efficient
- **Single-threaded but highly scalable** - uses event loop architecture
- **NPM (Node Package Manager)** - huge ecosystem of open-source libraries
- **Asynchronous programming** - handles multiple operations without blocking
- **Cross-platform** - runs on Windows, macOS, Linux, etc.
- **Built-in modules** like HTTP, fs, path, etc.
- **Great for real-time applications** like chat, streaming services
- **JavaScript everywhere** - use the same language for frontend and backend

### 60. How does Node.js handle asynchronous operations?
Node.js uses non-blocking I/O and an event-driven architecture to handle asynchronous operations:

1. **Callbacks** (traditional approach):
```javascript
fs.readFile('file.txt', (err, data) => {
  if (err) throw err;
  console.log(data);
});
console.log('Reading file...'); // This runs before file is read
```

2. **Promises** (more structured):
```javascript
const readFilePromise = () => {
  return new Promise((resolve, reject) => {
    fs.readFile('file.txt', (err, data) => {
      if (err) reject(err);
      else resolve(data);
    });
  });
};

readFilePromise()
  .then(data => console.log(data))
  .catch(err => console.error(err));
```

3. **Async/await** (modern approach):
```javascript
async function readFile() {
  try {
    const data = await fs.promises.readFile('file.txt');
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}
```

The Event Loop is the core mechanism that enables this asynchronous behavior:
1. Events are pushed to a queue
2. The event loop processes events from the queue one by one
3. For I/O operations, Node delegates to background threads
4. When an operation completes, a callback is added to the queue
5. The event loop returns to this callback when it reaches it

### 61. What is the Node Package Manager (npm)?
NPM (Node Package Manager) is the default package manager for Node.js. It consists of:

1. **Online repository** of JavaScript packages
2. **Command-line tool** for installing, managing, and publishing packages
3. **Website** for discovering packages (npmjs.com)

Common npm commands:
```bash
# Initialize a new project
npm init

# Install a package locally
npm install express

# Install a package globally
npm install -g nodemon

# Install dependencies from package.json
npm install

# Install a package as a development dependency
npm install --save-dev jest

# Update packages
npm update

# Uninstall a package
npm uninstall express

# Run scripts defined in package.json
npm run start
```

The `package.json` file stores project metadata and dependencies.

### 62. How do you handle dependencies in Node.js?
Dependencies in Node.js are handled through package.json and node_modules:

1. **package.json** - Lists project dependencies:
```json
{
  "name": "my-app",
  "version": "1.0.0",
  "dependencies": {
    "express": "^4.17.1",
    "mongoose": "^6.0.0"
  },
  "devDependencies": {
    "jest": "^27.0.0",
    "nodemon": "^2.0.7"
  }
}
```

2. **Dependency types**:
   - `dependencies`: Packages required for production
   - `devDependencies`: Packages needed only for development/testing
   - `peerDependencies`: Packages that the project works with but doesn't directly include

3. **Semantic versioning** (SemVer):
   - `^4.17.1`: Compatible with 4.17.1 up to (but not including) 5.0.0
   - `~4.17.1`: Compatible with 4.17.1 up to (but not including) 4.18.0
   - `4.17.1`: Exact version 4.17.1

4. **package-lock.json**: Locks down exact versions of all dependencies (including dependencies of dependencies)

5. **Installing dependencies**:
```bash
# Install all dependencies
npm install

# Update all dependencies
npm update
```

6. **Dependency management**:
   - `npm outdated`: Check for outdated packages
   - `npm audit`: Check for security vulnerabilities
   - `npm ls`: List installed packages

# Tailwind CSS

### 63. What is Tailwind CSS? How does it differ from other CSS frameworks like Bootstrap or Material UI?
Tailwind CSS is a utility-first CSS framework for rapidly building custom user interfaces. 

Differences from Bootstrap/Material UI:
- **Utility-first approach**: Tailwind provides low-level utility classes rather than pre-designed components
- **Highly customizable**: Easier to build a unique design without fighting the framework
- **No pre-designed components**: You compose components yourself using utility classes
- **Smaller file size in production**: Only includes the utilities you use (with purging)
- **No JavaScript**: Pure CSS, so no additional JavaScript dependencies
- **Design system based**: Built to enforce consistent spacing, colors, etc.
- **More granular control**: Fine-grained utility classes for precise styling

### 64. What are the advantages of using Tailwind CSS?
Advantages of Tailwind CSS:

- **Faster development** - No need to write custom CSS or switch between files
- **Consistent design** - Built-in constraints for spacing, colors, etc. keep your design consistent
- **Responsive design built-in** - Prefix utilities with `sm:`, `md:`, `lg:`, etc.
- **No naming headaches** - No need to invent class names for elements
- **Highly customizable** - Easy to extend or modify the default configuration
- **Small production size** - Built-in purging removes unused styles
- **No CSS specificity issues** - Flat utility classes avoid specificity wars
- **Less context switching** - Style elements right in your HTML/JSX
- **Easier to maintain** - Changes are localized to the component
- **Works well with component frameworks** - Perfect match for React, Vue, etc.

### 65. Explain the concept of utility-first CSS.
Utility-first CSS is an approach where you create designs by applying small, single-purpose utility classes directly in your HTML:

Traditional approach:
```html
<style>
  .card {
    border-radius: 0.25rem;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    padding: 1.5rem;
    background-color: #ffffff;
  }
</style>

<div class="card">
  <!-- Content -->
</div>
```

Utility-first approach (Tailwind):
```html
<div class="rounded shadow p-6 bg-white">
  <!-- Content -->
</div>
```

Key principles:
- Small, single-purpose classes (e.g., `mt-4`, `flex`, `text-center`)
- Compose designs by combining many utility classes
- Avoids writing custom CSS in most cases
- Classes have consistent naming patterns
- Encourages design constraint adherence
- Enables rapid iteration in the markup

### 66. How do you customize Tailwind CSS? What is the `tailwind.config.js` file?
Tailwind CSS is customized through the `tailwind.config.js` file, which allows you to modify the default theme, add plugins, and configure how Tailwind works.

Basic `tailwind.config.js`:
```javascript
module.exports = {
  // Control which files Tailwind analyzes to purge unused styles
  content: [
    './src/**/*.{js,jsx,ts,tsx}',
    './public/index.html',
  ],
  // Dark mode strategy: 'media' (system preference) or 'class' (manual toggle)
  darkMode: 'media',
  // Customize the default theme
  theme: {
    // Completely replace the existing definition
    colors: {
      primary: '#3490dc',
      secondary: '#ffed4a',
      danger: '#e3342f',
    },
    // Extend the default theme
    extend: {
      spacing: {
        '72': '18rem',
        '84': '21rem',
      },
      borderRadius: {
        '4xl': '2rem',
      },
      fontFamily: {
        display: ['Oswald', 'sans-serif'],
        body: ['Open Sans', 'sans-serif'],
      },
    },
  },
  // Add custom variants
  variants: {
    extend: {
      borderColor: ['focus-visible'],
      opacity: ['disabled'],
    },
  },
  // Add plugins
  plugins: [
    require('@tailwindcss/forms'),
    require('@tailwindcss/typography'),
  ],
};
```

### 67. How do you handle responsive design with Tailwind CSS?
Tailwind provides built-in responsive utilities using breakpoint prefixes:

```html
<div class="text-center sm:text-left md:text-right lg:text-justify">
  This text changes alignment at different screen sizes
</div>
```

Default breakpoints:
- `sm`: 640px and up
- `md`: 768px and up
- `lg`: 1024px and up
- `xl`: 1280px and up
- `2xl`: 1536px and up

You can customize breakpoints in your config:
```javascript
module.exports = {
  theme: {
    screens: {
      'sm': '640px',
      'md': '768px',
      'lg': '1024px',
      'xl': '1280px',
      '2xl': '1536px',
    }
  }
}
```

Mobile-first approach:
- Unprefixed utilities apply to all screen sizes
- Prefixed utilities apply at the specified breakpoint and up
- Start with mobile design, then add prefixed utilities for larger screens

Example of a responsive card layout:
```html
<div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
  <div class="bg-white rounded shadow p-4">Card 1</div>
  <div class="bg-white rounded shadow p-4">Card 2</div>
  <!-- more cards -->
</div>
```

### 68. How do you create custom components with Tailwind CSS?
With Tailwind, you create custom components by combining utility classes. As components get reused, you can extract patterns:

1. **Using component classes** (for simple cases):
```html
<style>
  .btn {
    @apply py-2 px-4 rounded font-bold;
  }
  .btn-blue {
    @apply bg-blue-500 text-white hover:bg-blue-700;
  }
</style>

<button class="btn btn-blue">Button</button>
```

2. **Creating React/Vue/etc. components** (recommended approach):
```jsx
// Button.jsx
function Button({ color = 'blue', children }) {
  const colorClasses = {
    blue: 'bg-blue-500 hover:bg-blue-700 text-white',
    red: 'bg-red-500 hover:bg-red-700 text-white',
    green: 'bg-green-500 hover:bg-green-700 text-white',
  };
  
  return (
    <button className={`py-2 px-4 rounded font-bold ${colorClasses[color]}`}>
      {children}
    </button>
  );
}

// Usage
<Button color="green">Click me</Button>
```

3. **Using Tailwind plugins** (for more complex patterns):
```javascript
// tailwind.config.js
const plugin = require('tailwindcss/plugin')

module.exports = {
  plugins: [
    plugin(function({ addComponents, theme }) {
      const buttons = {
        '.btn': {
          padding: `${theme('spacing.2')} ${theme('spacing.4')}`,
          borderRadius: theme('borderRadius.md'),
          fontWeight: theme('fontWeight.bold'),
        },
        '.btn-blue': {
          backgroundColor: theme('colors.blue.500'),
          color: theme('colors.white'),
          '&:hover': {
            backgroundColor: theme('colors.blue.700')
          },
        },
      }
      addComponents(buttons)
    })
  ]
}
```

### 69. What are some best practices for using Tailwind CSS effectively?
Best practices for Tailwind CSS:

1. **Use consistent spacing** - Stick to Tailwind's built-in spacing scale
2. **Extract components for reusability** - Use React/Vue components or @apply for repeated patterns
3. **Group related utilities** - Keep spacing, typography, colors, etc. together
4. **Use Prettier with Tailwind plugin** - Formats long class lists consistently
5. **Use the JIT (Just-In-Time) mode** - Enables all variants and custom values without performance penalty
6. **Keep accessibility in mind** - Ensure sufficient color contrast, focus states, etc.
7. **Use custom CSS sparingly** - Try to solve problems with Tailwind utilities first
8. **Follow mobile-first approach** - Start with base styles, then add responsive variants
9. **Use @layer when adding custom styles** - Keeps cascade working properly
10. **Use the Container component pattern**:
```jsx
// Container.jsx
export function Container({ children }) {
  return (
    <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      {children}
    </div>
  );
}
```

### 70. How do you extend Tailwind's theme?
Extending Tailwind's theme involves adding new values to the theme configuration without replacing the defaults:

```javascript
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      // Add new colors
      colors: {
        'brand': {
          light: '#BFDBFE',
          DEFAULT: '#3B82F6',
          dark: '#1E40AF',
        },
      },
      // Add new spacing values
      spacing: {
        '128': '32rem',
        '144': '36rem',
      },
      // Add new font family
      fontFamily: {
        'heading': ['Montserrat', 'sans-serif'],
      },
      // Add new animation
      animation: {
        'bounce-slow': 'bounce 3s linear infinite',
      },
      // Custom box shadows
      boxShadow: {
        'inner-lg': 'inset 0 2px 15px 0 rgba(0, 0, 0, 0.1)',
      },
      // Custom border radius
      borderRadius: {
        'xl': '1rem',
      },
    },
  },
}
```

Using custom theme values:
```html
<div class="bg-brand text-white p-4 font-heading shadow-inner-lg rounded-xl">
  <h2>Custom themed component</h2>
</div>
```

You can also add entirely new theme sections:
```javascript
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      // Add custom aspect ratios
      aspectRatio: {
        '4/3': '4 / 3',
        '16/9': '16 / 9',
        'portrait': '3 / 4',
      },
    },
  },
  plugins: [
    // Plugin to use custom aspect ratios
    require('@tailwindcss/aspect-ratio'),
  ],
}
```

# Git

### 71. What is Git? What are its key features?
Git is a distributed version control system that tracks changes in source code during software development.

Key features:
- **Distributed architecture** - Every developer has a complete history of the project
- **Branching and merging** - Create isolated environments for development
- **Speed and efficiency** - Fast operations even with large repositories
- **Data integrity** - Content is checksummed to prevent corruption
- **Staging area** - Review and prepare changes before committing
- **Non-linear development** - Support for parallel development
- **Compatibility** - Works on all major platforms
- **Open source** - Free and widely supported

### 72. What are the common Git commands that you use? (continued)
Common Git commands:

**Basic commands**:
```bash
# Initialize a repository
git init

# Clone a repository
git clone https://github.com/username/repository.git

# Check status of working directory
git status

# Add files to staging area
git add filename.js           # Add specific file
git add .                     # Add all files

# Commit changes
git commit -m "Your message"

# View commit history
git log
git log --oneline --graph     # Compact history with branch visualization
```

**Branch operations**:
```bash
# List branches
git branch

# Create new branch
git branch feature-name

# Switch to a branch
git checkout branch-name
git switch branch-name        # Modern alternative

# Create and switch to new branch
git checkout -b feature-name
git switch -c feature-name    # Modern alternative

# Delete branch
git branch -d branch-name     # Safe delete (won't delete unmerged changes)
git branch -D branch-name     # Force delete
```

**Remote operations**:
```bash
# Add remote repository
git remote add origin https://github.com/username/repo.git

# List remote repositories
git remote -v

# Fetch changes from remote
git fetch origin

# Pull changes (fetch + merge)
git pull origin main

# Push changes to remote
git push origin main
```

**Merge operations**:
```bash
# Merge branch into current branch
git merge feature-branch

# Abort merge
git merge --abort
```

**Stash operations**:
```bash
# Save uncommitted changes temporarily
git stash

# List stashes
git stash list

# Apply stashed changes
git stash apply
git stash pop            # Apply and remove stash
```

### 73. What is the difference between `git merge` and `git rebase`? When would you use each one?
**Git Merge**:
- Creates a new "merge commit" that combines changes from both branches
- Preserves complete history and chronological order
- Non-destructive operation (original branches remain unchanged)

```bash
git checkout main
git merge feature-branch
```

**Git Rebase**:
- Moves the entire feature branch to begin on the tip of the main branch
- Results in a linear project history
- Rewrites project history by creating new commits

```bash
git checkout feature-branch
git rebase main
```

**When to use merge**:
- For integrating completed features into the main branch
- When you want to preserve the complete history
- For public/shared branches that others are working on
- When branch history context is important

**When to use rebase**:
- To keep feature branch updated with latest main changes
- For cleaning up local commits before sharing
- When you want a clean, linear project history
- For private/personal branches that aren't shared

### 74. How do you resolve merge conflicts in Git?
Merge conflicts occur when Git can't automatically resolve differences between branches. Here's how to resolve them:

1. **Git will indicate which files have conflicts**:
```bash
git merge feature-branch
# CONFLICT (content): Merge conflict in file.js
```

2. **Open the conflicted files in your editor**. You'll see:
```
<<<<<<< HEAD
// Current branch code
=======
// Incoming branch code
>>>>>>> feature-branch
```

3. **Manually edit the file** to resolve conflicts by:
   - Keeping your changes (`<<<<<<< HEAD` to `=======`)
   - Keeping the incoming changes (`=======` to `>>>>>>> feature-branch`)
   - Keeping both or modifying as needed
   - Removing the conflict markers

4. **Add the resolved files to the staging area**:
```bash
git add file.js
```

5. **Complete the merge by committing**:
```bash
git commit -m "Resolve merge conflicts"
```

**Tools to help with merge conflicts**:
- Visual tools: VS Code, GitKraken, SourceTree
- Command line tools: `git mergetool`
- Settings to reduce conflicts: `git config --global merge.conflictstyle diff3`

### 75. How do you revert a commit in Git?
There are multiple ways to revert commits in Git:

1. **`git revert`** - Creates a new commit that undoes changes (safest option):
```bash
# Revert the most recent commit
git revert HEAD

# Revert a specific commit
git revert abc123
```

2. **`git reset`** - Moves the branch pointer backwards (rewrites history):
```bash
# Soft reset - keeps changes staged
git reset --soft HEAD~1

# Mixed reset - keeps changes unstaged (default)
git reset HEAD~1

# Hard reset - discards changes (DANGEROUS)
git reset --hard HEAD~1
```

3. **`git checkout`** - Restore specific files from a previous commit:
```bash
# Restore a file to its state in a previous commit
git checkout abc123 -- file.js
```

4. **Amend most recent commit** - Replace the last commit:
```bash
# Make changes, then
git add .
git commit --amend -m "New commit message"
```

### 76. What is a `.gitignore` file, and how do you use it?
A `.gitignore` file specifies files and directories that Git should ignore (not track). It helps keep your repository clean from temporary files, build artifacts, and sensitive information.

Example `.gitignore` file:
```
# Node.js dependencies
node_modules/
npm-debug.log

# Build outputs
dist/
build/
*.min.js

# Environment variables
.env
.env.local

# Operating system files
.DS_Store
Thumbs.db

# Editor directories and files
.idea/
.vscode/
*.swp
*.swo

# Logs
logs/
*.log

# Testing
coverage/
```

Rules for `.gitignore` files:
- Each line is a pattern
- `#` starts a comment
- Blank lines are ignored
- `/pattern` specifies directory
- `pattern/` specifies all directories with that name
- `!pattern` negates a pattern (include previously excluded files)
- `*` matches any character sequence except `/`
- `?` matches any single character except `/`
- `**` matches any number of directories

### 77. What is the "staging area" in Git?
The staging area (or index) is a middle ground between your working directory and the repository. It's where you prepare changes before committing them.

Key aspects of the staging area:
- Allows you to selectively commit parts of your changes
- Lets you review what will be included in the next commit
- Helps organize related changes into cohesive commits

Working with the staging area:
```bash
# Add files to staging area
git add file.js           # Add specific file
git add directory/        # Add all files in directory
git add -p                # Interactively choose parts of files to stage

# Remove files from staging area (keeps file changes)
git restore --staged file.js  # Modern syntax
git reset HEAD file.js        # Traditional syntax

# View differences
git diff                  # Between working directory and staging
git diff --staged         # Between staging and last commit

# Commit staged changes
git commit -m "Your message"
```

### 78. What is Gitflow? Describe the branching strategy.
Gitflow is a branching model that defines a structured workflow for managing features, releases, and hotfixes.

Main branches:
- **main/master**: Production-ready code
- **develop**: Latest delivered development changes

Supporting branches:
- **feature branches**: For new features (`feature/user-authentication`)
- **release branches**: Prepare for production release (`release/1.2.0`)
- **hotfix branches**: Emergency fixes for production (`hotfix/login-bug`)

Gitflow workflow:
1. **Feature development**:
   - Branch off from `develop`: `git checkout -b feature/new-feature develop`
   - Work on the feature
   - Merge back to `develop`: 
     ```bash
     git checkout develop
     git merge --no-ff feature/new-feature
     git branch -d feature/new-feature
     ```

2. **Release preparation**:
   - Branch off from `develop`: `git checkout -b release/1.2.0 develop`
   - Minor bug fixes and release preparation
   - Finish release:
     ```bash
     git checkout main
     git merge --no-ff release/1.2.0
     git tag -a v1.2.0
     git checkout develop
     git merge --no-ff release/1.2.0
     git branch -d release/1.2.0
     ```

3. **Hotfix**:
   - Branch off from `main`: `git checkout -b hotfix/critical-bug main`
   - Fix the bug
   - Finish hotfix:
     ```bash
     git checkout main
     git merge --no-ff hotfix/critical-bug
     git tag -a v1.2.1
     git checkout develop
     git merge --no-ff hotfix/critical-bug
     git branch -d hotfix/critical-bug
     ```

### 79. How do you use Git hooks to automate tasks?
Git hooks are scripts that run automatically when certain Git events occur. They help enforce quality standards and automate workflows.

Common Git hooks:
- **pre-commit**: Runs before a commit is created
- **prepare-commit-msg**: Runs before commit message editor is launched
- **commit-msg**: Validates commit messages
- **post-commit**: Runs after a commit is completed
- **pre-push**: Runs before pushing to a remote
- **post-merge**: Runs after a merge is completed

Steps to implement a Git hook:
1. Navigate to `.git/hooks/` directory in your repository
2. Create a new file with the hook name (without extension) or rename the sample
3. Make the file executable: `chmod +x .git/hooks/pre-commit`
4. Write your script

Example pre-commit hook for linting:
```bash
#!/bin/sh

# Run ESLint on staged JS files
FILES=$(git diff --cached --name-only --diff-filter=ACM | grep '\.js$')
if [ -n "$FILES" ]; then
  echo "Running ESLint on staged files..."
  npx eslint $FILES
  if [ $? -ne 0 ]; then
    echo "ESLint failed. Please fix the issues before committing."
    exit 1
  fi
fi

exit 0
```

**Team-wide hooks with Husky**:
```bash
# Install Husky
npm install husky --save-dev

# In package.json
{
  "husky": {
    "hooks": {
      "pre-commit": "npm run lint",
      "commit-msg": "commitlint -E HUSKY_GIT_PARAMS"
    }
  }
}
```

### 80. What are submodules and subtrees in Git? When would you use them?
**Git Submodules**:
Include another Git repository within your repository as a subdirectory while keeping the commits separate.

```bash
# Add a submodule
git submodule add https://github.com/username/library.git libs/library

# Clone a repository with submodules
git clone --recursive https://github.com/username/main-project.git

# Update submodules
git submodule update --init --recursive

# Pull changes in all submodules
git submodule foreach git pull origin main
```

**Git Subtrees**:
Merge another repository's history into a subdirectory of your repository.

```bash
# Add a subtree
git subtree add --prefix=libs/library https://github.com/username/library.git main --squash

# Update a subtree
git subtree pull --prefix=libs/library https://github.com/username/library.git main --squash

# Push changes to subtree's remote
git subtree push --prefix=libs/library https://github.com/username/library.git main
```

**When to use submodules**:
- When you need to use the exact same code in multiple projects
- When you want to clearly separate the external code
- When contributors shouldn't modify the included code
- When you need precise versioning of the dependency

**When to use subtrees**:
- When you want to include the external code as part of your project
- When contributors should be able to modify the included code
- When you want a simpler workflow for your team
- When you need to backport changes to the original repository

### 81. How do you optimize Git performance?
Optimizing Git performance:

1. **Keep repositories small**:
   - Use `.gitignore` to exclude unnecessary files
   - Consider Git LFS for large files
   - Archive old branches: `git archive --format=zip HEAD > project.zip`

2. **Shallow clones** for large repositories:
```bash
# Clone with limited history
git clone --depth=1 https://github.com/username/repo.git

# Clone single branch
git clone --single-branch --branch=main https://github.com/username/repo.git
```

3. **Use sparse checkout** for monorepos:
```bash
git clone --no-checkout https://github.com/username/repo.git
cd repo
git sparse-checkout set folder1 folder2
git checkout main
```

4. **Regular maintenance**:
```bash
# Compress repository objects
git gc

# More aggressive optimization
git gc --aggressive

# Find unnecessary objects
git prune

# Verify repository integrity
git fsck
```

5. **Optimize local workflow**:
   - Use `git fetch` instead of `git pull` when appropriate
   - Use partial clones: `git clone --filter=blob:none`
   - Configure Git to not check file permissions: `git config core.fileMode false`

6. **Configure Git for performance**:
```bash
# Increase buffer sizes
git config --global core.packedGitLimit 512m
git config --global core.packedGitWindowSize 512m
git config --global pack.windowMemory 512m

# Enable filesystem cache
git config --global core.fscache true
```

### 82. Explain the difference between `git reset --soft`, `git reset --mixed`, and `git reset --hard`.
All three commands move the HEAD and branch pointer to a specified commit, but they differ in how they update the staging area and working directory:

**`git reset --soft`**:
- Moves HEAD to the specified commit
- Does NOT change staging area
- Does NOT change working directory
- All changes from reset commits appear staged and ready to commit
- Use case: When you want to combine several commits into one

```bash
git reset --soft HEAD~3  # Move HEAD back 3 commits, keep changes staged
git commit -m "Combined three commits"
```

**`git reset --mixed`** (default):
- Moves HEAD to the specified commit
- Updates staging area to match the specified commit
- Does NOT change working directory
- All changes from reset commits appear as unstaged modifications
- Use case: When you want to reorganize changes into different commits

```bash
git reset HEAD~3        # Move HEAD back 3 commits, unstage changes
git add first.js        # Stage specific files
git commit -m "First logical change"
git add second.js
git commit -m "Second logical change"
```

**`git reset --hard`**:
- Moves HEAD to the specified commit
- Updates staging area to match the specified commit
- Updates working directory to match the specified commit
- All changes from reset commits are permanently discarded (DANGEROUS)
- Use case: When you want to discard work and start over

```bash
git reset --hard HEAD~1  # Discard the last commit and all its changes
# or
git reset --hard origin/main  # Reset local branch to match remote
```

### 83. How do you recover a lost commit in Git?
Several ways to recover lost commits:

1. **Using git reflog** (most reliable):
```bash
# Show a log of HEAD movements
git reflog

# Found lost commit with hash abc1234
git checkout abc1234
# or
git branch recovery-branch abc1234
```

2. **Find dangling commits**:
```bash
# List all objects not reachable from any ref
git fsck --full --no-reflogs --unreachable --lost-found

# Examine a dangling commit
git show abc1234

# Recover the commit
git branch recovery-branch abc1234
```

3. **Using git cherry-pick** after finding the commit:
```bash
# After finding the lost commit hash
git cherry-pick abc1234
```

4. **If accidentally reset with --hard**:
```bash
# Check reflog immediately
git reflog
git reset --hard HEAD@{1}  # Go back to state before the reset
```

5. **If lost commit was in a deleted branch**:
```bash
# Reflog still tracks it
git reflog
git checkout -b recovered-branch abc1234
```

Git typically keeps unreferenced objects for at least 30 days by default (configurable via `gc.pruneExpire)

# AWS 

### 84. What is AWS? What are its key services?
AWS (Amazon Web Services) is a comprehensive cloud platform offering over 200 services from data centers globally.

Key services:
- **Compute**: EC2 (virtual servers), Lambda (serverless functions), ECS/EKS (containers)
- **Storage**: S3 (object storage), EBS (block storage), EFS (file system)
- **Database**: RDS (relational), DynamoDB (NoSQL), ElastiCache (in-memory)
- **Networking**: VPC (virtual network), Route 53 (DNS), CloudFront (CDN)
- **Security**: IAM (identity management), WAF (web application firewall), Shield (DDoS protection)
- **DevOps**: CodePipeline, CodeBuild, CodeDeploy (CI/CD)
- **Monitoring**: CloudWatch (metrics & logs), X-Ray (tracing)
- **AI/ML**: SageMaker, Rekognition, Comprehend

### 85. Describe your experience deploying web applications on AWS.
When deploying web applications on AWS, a typical approach involves:

1. **Architecture planning**:
   - Designing scalable, fault-tolerant architecture
   - Separating frontend and backend components
   - Planning for security, monitoring, and backups

2. **Implementation components**:
   - Frontend: S3 for static hosting, CloudFront for CDN
   - Backend: EC2 instances in auto-scaling groups or serverless with Lambda
   - Database: RDS for relational or DynamoDB for NoSQL
   - API Layer: API Gateway for serverless or Load Balancer with EC2

3. **Deployment process**:
   - Infrastructure as Code using CloudFormation or Terraform
   - CI/CD pipeline with CodePipeline or GitHub Actions
   - Blue-green deployments for zero downtime
   - Automated testing before production promotion

4. **Monitoring and maintenance**:
   - CloudWatch dashboards and alerts
   - Log analysis and performance monitoring
   - Regular security scanning and updates
   - Cost optimization reviews

### 86. What are the advantages of using AWS?
Advantages of using AWS:

- **Scalability** - Easily scale resources up or down based on demand
- **Pay-as-you-go pricing** - Only pay for what you use
- **Global infrastructure** - Deploy applications closer to users worldwide
- **Reliability** - High availability across multiple availability zones
- **Security** - Comprehensive security tools and compliance certifications
- **Managed services** - Reduced operational burden
- **Integration** - Seamless connection between services
- **Automation** - APIs for everything enable infrastructure as code
- **Innovation** - Continuous release of new services and features
- **Ecosystem** - Large marketplace of third-party tools and integrations

### 87. How do you secure your applications on AWS?
Securing applications on AWS involves multiple layers:

1. **Identity and Access Management**:
   - Use IAM roles and policies with least privilege principle
   - Enable MFA for all IAM users
   - Rotate access keys regularly
   - Use AWS Organizations for multi-account strategy

2. **Network Security**:
   - Implement VPCs with private subnets
   - Use security groups and network ACLs
   - Configure VPN or Direct Connect for secure access
   - Implement WAF for protection against common web exploits

3. **Data Protection**:
   - Encrypt data at rest using KMS or SSE
   - Encrypt data in transit using TLS/SSL
   - Implement S3 bucket policies and block public access
   - Use Secrets Manager for credential management

4. **Monitoring and Detection**:
   - Enable CloudTrail for API activity monitoring
   - Use GuardDuty for threat detection
   - Configure Config for compliance monitoring
   - Set up CloudWatch alarms for suspicious activities

5. **Security Best Practices**:
   - Regular security assessments with Inspector
   - Patch management strategy
   - Follow AWS Well-Architected Framework security pillar
   - Implement DDoS protection with Shield

### 88. How do you monitor the performance of your applications on AWS?
Monitoring applications on AWS involves several services and practices:

1. **CloudWatch** - Core monitoring service:
   - **Metrics**: Track CPU, memory, disk, network utilization
   - **Alarms**: Set thresholds and receive notifications
   - **Logs**: Centralize and analyze application logs
   - **Dashboards**: Create custom visualization dashboards

2. **X-Ray** - Application tracing:
   - Trace requests as they travel through the application
   - Identify bottlenecks and latency issues
   - Visualize service dependencies

3. **CloudTrail** - API activity monitoring:
   - Track who did what and when
   - Detect unauthorized access attempts

4. **AWS Config** - Resource configuration tracking:
   - Monitor infrastructure changes
   - Ensure compliance with best practices

5. **Performance best practices**:
   - Set up detailed monitoring on critical resources
   - Use custom metrics for application-specific monitoring
   - Implement automated remediation with EventBridge
   - Regular performance testing

### 89. What is EC2? How do you use it to launch virtual servers?
EC2 (Elastic Compute Cloud) is AWS's service for resizable virtual servers in the cloud.

Steps to launch an EC2 instance:
1. **Choose an Amazon Machine Image (AMI)** - OS and pre-installed software
2. **Select an instance type** - CPU, memory, storage, and networking capacity
3. **Configure instance details**:
   - Network (VPC) and subnet
   - IAM role for AWS access
   - User data for bootstrapping
   - Shutdown behavior
4. **Add storage** - Configure EBS volumes or instance store
5. **Add tags** - Key-value pairs for organization
6. **Configure security group** - Firewall rules for traffic control
7. **Review and launch** - Create or select key pair for SSH access
8. **Connect to the instance** - Via SSH, RDP, or Systems Manager

Key EC2 concepts:
- **AMI**: Template for root volume containing OS and applications
- **Instance types**: Different hardware configurations
- **Security groups**: Virtual firewalls controlling traffic
- **Key pairs**: Authentication for instance access
- **Elastic IP**: Static IP address for dynamic cloud computing
- **Auto Scaling**: Automatically adjust capacity based on demand

### 90. What are different EC2 instance types? How do you choose the right instance type for your application?
EC2 instance families:

1. **General Purpose (T, M)** - Balanced CPU, memory, networking
   - **Use cases**: Web servers, small databases, development environments

2. **Compute Optimized (C)** - High CPU performance
   - **Use cases**: Batch processing, scientific modeling, game servers, high-performance web servers

3. **Memory Optimized (R, X, z)** - Fast performance for memory-intensive workloads
   - **Use cases**: In-memory databases, real-time big data analytics, large caches

4. **Storage Optimized (D, I, H)** - High disk throughput and IOPS
   - **Use cases**: Data warehousing, log processing, distributed file systems

5. **Accelerated Computing (P, G, F)** - GPU or FPGA processing
   - **Use cases**: Machine learning, video encoding, graphics processing

Choosing the right instance type:
1. **Analyze requirements**:
   - CPU, memory, storage, and network needs
   - Burstable vs. consistent performance
   - Specialized hardware requirements (GPU, FPGA)

2. **Consider workload patterns**:
   - Steady-state vs. variable loads
   - Batch processing vs. real-time responses

3. **Test and measure**:
   - Benchmark with different instance types
   - Monitor performance metrics
   - Use CloudWatch to identify bottlenecks

4. **Cost optimization**:
   - Reserved Instances for predictable workloads
   - Spot Instances for flexible, non-critical workloads
   - Right-sizing based on utilization metrics

### 91. What are security groups in EC2? How do you use them to control network traffic?
Security groups are virtual firewalls that control inbound and outbound traffic to EC2 instances.

Key characteristics:
- Act at the instance level (not subnet level like NACLs)
- Support allow rules only (no explicit deny rules)
- Stateful (return traffic automatically allowed)
- Can reference other security groups, IP addresses, or CIDR blocks

Configuring security groups:
```
Inbound Rules:
- Type: HTTP (80)
  Source: 0.0.0.0/0
- Type: SSH (22)
  Source: 10.0.0.0/16 (VPC CIDR)
- Type: Custom TCP (3000)
  Source: sg-1234abcd (Reference to another security group)

Outbound Rules:
- Type: All Traffic
  Destination: 0.0.0.0/0
```

Best practices:
- Follow principle of least privilege
- Don't open SSH/RDP to the world (0.0.0.0/0)
- Use security group references instead of IP addresses when possible
- Create separate security groups for different functions
- Regularly audit security group rules
- Use Security Group IDs instead of names in references

### 92. How do you use Elastic Load Balancing (ELB) with EC2?
Elastic Load Balancing (ELB) distributes incoming traffic across multiple EC2 instances to improve availability and fault tolerance.

Types of load balancers:
1. **Application Load Balancer (ALB)** - HTTP/HTTPS traffic, path-based routing
2. **Network Load Balancer (NLB)** - TCP/UDP traffic, extreme performance
3. **Classic Load Balancer (CLB)** - Legacy option, basic load balancing

Setting up ELB with EC2:
1. **Create a load balancer**:
   - Choose the type (ALB, NLB, CLB)
   - Select VPC and subnets (multiple AZs for high availability)
   - Configure security settings (HTTPS certificates)
   - Configure security groups

2. **Configure health checks**:
   - Protocol (HTTP, HTTPS, TCP)
   - Path (for HTTP/HTTPS)
   - Success criteria
   - Check intervals and thresholds

3. **Register targets**:
   - Create a target group
   - Add EC2 instances or set up auto-scaling group
   - Define routing rules

4. **Configure listeners**:
   - Port and protocol (80/HTTP, 443/HTTPS)
   - Default actions and rules
   - Content-based routing (ALB)

Best practices:
- Deploy across multiple AZs for high availability
- Enable connection draining for graceful instance deregistration
- Use SSL termination at the load balancer
- Configure appropriate idle timeouts
- Implement sticky sessions when needed

### 93. What is S3? How do you use it to store and retrieve objects?
Amazon S3 (Simple Storage Service) is an object storage service offering industry-leading scalability, availability, security, and performance.

Key concepts:
- **Buckets**: Containers for objects (similar to top-level directories)
- **Objects**: Files and metadata stored in S3 (up to 5TB each)
- **Keys**: Unique identifiers for objects within a bucket
- **Regions**: Physical location where buckets are stored
- **Storage classes**: Different tiers with varying costs and retrieval times

Working with S3:
1. **Creating a bucket**:
```bash
aws s3 mb s3://my-unique-bucket-name --region us-east-1
```

2. **Uploading objects**:
```bash
# CLI
aws s3 cp local-file.txt s3://my-bucket/path/

# SDK (JavaScript)
const params = {
  Bucket: 'my-bucket',
  Key: 'path/file.txt',
  Body: fileContent
};
s3Client.putObject(params).promise();
```

3. **Downloading objects**:
```bash
# CLI
aws s3 cp s3://my-bucket/path/file.txt local-file.txt

# SDK (JavaScript)
const params = {
  Bucket: 'my-bucket',
  Key: 'path/file.txt'
};
const data = await s3Client.getObject(params).promise();
```

4. **Object URL patterns**:
```
https://bucket-name.s3.region.amazonaws.com/key-name
https://s3.region.amazonaws.com/bucket-name/key-name
```

### 94. What are S3 buckets?
S3 buckets are containers for objects stored in Amazon S3. They organize the Amazon S3 namespace at the highest level.

Characteristics:
- Names must be globally unique across all of AWS
- Names must be 3-63 characters long
- Names can contain lowercase letters, numbers, hyphens
- Names cannot be formatted as IP addresses
- Buckets are region-specific
- Unlimited objects can be stored in a bucket
- Default limit of 100 buckets per AWS account (can be increased)

Creating and managing buckets:
1. **Creation**:
```bash
aws s3 mb s3://bucket-name --region us-east-1
```

2. **Setting properties**:
- Versioning: Track multiple versions of objects
- Website hosting: Configure bucket for static website hosting
- Event notifications: Trigger Lambda functions on object events
- Lifecycle rules: Automatically transition or expire objects

3. **Bucket policies**: JSON documents defining access permissions:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::bucket-name/*"
    }
  ]
}
```

4. **Deletion**:
```bash
# Must delete all objects first
aws s3 rm s3://bucket-name --recursive
aws s3 rb s3://bucket-name
```

### 95. How do you control access to S3 objects?
Multiple mechanisms to control S3 access:

1. **IAM Policies** - User-based access control:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:ListBucket"
      ],
      "Resource": [
        "arn:aws:s3:::bucket-name",
        "arn:aws:s3:::bucket-name/*"
      ]
    }
  ]
}
```

2. **Bucket Policies** - Resource-based access control:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::123456789012:user/username"
      },
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::bucket-name/*"
    }
  ]
}
```

3. **Access Control Lists (ACLs)** - Object and bucket level permissions (legacy)

4. **Presigned URLs** - Temporary access to objects:
```javascript
const params = {
  Bucket: 'my-bucket',
  Key: 'private/file.jpg',
  Expires: 60 * 5 // 5 minutes
};
const signedUrl = s3.getSignedUrl('getObject', params);
```

5. **S3 Block Public Access** - Bucket-level settings to prevent public access

6. **S3 Object Lock** - Prevent object deletion for a specific time period

7. **S3 Access Points** - Named network endpoints with dedicated access policies

Best practices:
- Block public access by default
- Use bucket policies for cross-account access
- Use IAM roles for EC2 instances accessing S3
- Enable server-side encryption
- Use VPC endpoints for private access

### 96. How do you use S3 for static website hosting?
S3 can host static websites with HTML, CSS, JavaScript, images, and other client-side content.

Setting up static website hosting:
1. **Create a bucket** with a suitable name (e.g., `example.com`)

2. **Enable static website hosting**:
   - Console: Properties → Static website hosting → Enable
   - CLI:
     ```bash
     aws s3 website s3://example.com/ --index-document index.html --error-document error.html
     ```

3. **Configure bucket policy** for public read access:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::example.com/*"
    }
  ]
}
```

**94. What are S3 buckets?**
S3 buckets are cloud storage containers in AWS that store objects (files). Think of them like folders in the cloud where you can store any type of file. Each bucket has a globally unique name and can store an unlimited number of objects, with individual files up to 5TB in size. S3 offers high durability and availability for storing data like images, videos, backups, and application files.

**95. How do you control access to S3 objects?**
You can control S3 access through:
- Bucket policies: JSON documents defining permissions at the bucket level
- IAM policies: Control which users/roles can access buckets
- Access Control Lists (ACLs): Fine-grained control for individual objects
- Presigned URLs: Temporary access to specific objects
- Block Public Access settings: Prevent accidental public exposure
- Bucket encryption: Protect data with server-side encryption

**96. How do you use S3 for static website hosting?**
To host a static website on S3:
1. Create an S3 bucket with a name matching your domain
2. Upload your website files (HTML, CSS, JS, images)
3. Enable "Static website hosting" in bucket properties
4. Set your index document (e.g., index.html) and error document
5. Make the content publicly accessible using a bucket policy
6. Get the website endpoint URL from the properties tab
7. Optionally, connect it to a custom domain using Route 53 and CloudFront

### AWS Lambda

**97. What is AWS Lambda? What are its use cases?**
AWS Lambda is a serverless computing service that runs code in response to events without requiring server management. You pay only for the compute time consumed.

Common use cases:
- API backends (with API Gateway)
- Real-time file processing (when uploads happen to S3)
- Scheduled tasks (cron jobs)
- Processing streams of data (with Kinesis)
- Automated backups and notifications
- IoT backends
- Chatbots and voice assistants

**98. How do you deploy and execute code using Lambda?**
To deploy and execute Lambda code:
1. Write your function in a supported language (Node.js, Python, Java, etc.)
2. Package your code with dependencies into a deployment package
3. Create a Lambda function in the AWS console, CLI, or with IaC tools
4. Upload your code or point to an S3 bucket
5. Configure the function (memory, timeout, environment variables)
6. Set up trigger(s) to execute your function (API Gateway, S3, CloudWatch Events, etc.)
7. Add necessary IAM permissions for your function
8. Test and monitor execution using CloudWatch Logs

**99. What are Lambda functions?**
Lambda functions are individual units of code that run in response to events. Each function contains:
- Handler: The entry point for execution (e.g., index.handler)
- Runtime environment: Language interpreter (Node.js, Python, etc.)
- Configuration: Memory allocation, timeout settings, environment variables
- Execution context: Maintains state between invocations for efficiency
- Permissions: IAM role defining what AWS resources the function can access

Lambda functions are stateless but can connect to databases or other storage for persistent data.

**100. How do you trigger Lambda functions?**
Lambda functions can be triggered by:
- AWS services (S3, DynamoDB, SQS, SNS)
- API Gateway (HTTP/REST endpoints)
- CloudWatch Events/EventBridge (scheduled or event-pattern based)
- Kinesis (stream processing)
- Direct invocation via AWS SDK
- AWS IoT
- Alexa Skills
- CloudFront edge functions
- Custom application events

Each trigger type provides specific event data to the Lambda function.

### RDS (Relational Database Service)

**101. What is RDS? What are its advantages?**
RDS is a managed relational database service from AWS that makes it easy to set up, operate, and scale a relational database in the cloud.

Advantages:
- Automated backups and point-in-time recovery
- Automatic software patching
- Hardware provisioning handled by AWS
- Multi-AZ deployment for high availability
- Read replicas for improved performance
- Monitoring and metrics via CloudWatch
- Easy scaling (vertical and horizontal)
- Encryption at rest and in transit
- Managed database parameter groups

**102. What are the different database engines supported by RDS?**
RDS supports these database engines:
- MySQL
- PostgreSQL
- MariaDB
- Oracle
- Microsoft SQL Server
- Amazon Aurora (MySQL and PostgreSQL compatible)

Each engine has different versions, features, and pricing options.

**103. How do you connect to an RDS instance from your application?**
To connect to an RDS instance:
1. Create the RDS instance in the correct VPC/subnet
2. Configure security groups to allow traffic on the database port
3. Get connection details (endpoint, port, database name, username, password)
4. Use a database driver/connector in your application code
5. Create a connection string with the details
6. Use connection pooling for efficient connections
7. Store credentials securely (using Secrets Manager or Parameter Store)
8. Handle connection errors and retries in your code

Sample Node.js connection with MySQL:
```javascript
const mysql = require('mysql2');
const connection = mysql.createConnection({
  host: 'your-rds-endpoint.rds.amazonaws.com',
  user: 'username',
  password: 'password',
  database: 'database_name'
});
connection.connect();
```

**104. How do you back up and restore RDS databases?**
Backing up RDS databases:
- Automated backups: Configure retention period (0-35 days)
- Manual snapshots: Create on-demand, stored until deleted
- Enable Multi-AZ for synchronous replication

Restoring:
1. From automated backup: Select point-in-time recovery
2. From snapshot: Select the snapshot and create a new DB instance
3. Restored databases have new endpoints, update application connection strings
4. Verify data integrity after restore
5. For partial restores, you may need to export/import specific data

### CloudFront and CDN

**105. What is CloudFront? How does it improve website performance?**
CloudFront is AWS's Content Delivery Network (CDN) that speeds up distribution of static and dynamic content by caching copies at edge locations worldwide.

It improves performance by:
- Reducing latency by serving content from locations closer to users
- Decreasing load on origin servers through caching
- Handling traffic spikes with scalable edge infrastructure
- Optimizing connections with HTTP/2 and HTTPS
- Reducing bandwidth costs with compression
- Protecting against certain types of attacks with security features
- Enabling real-time logs for monitoring and analytics

**106. How do you configure CloudFront to cache content?**
To configure CloudFront caching:
1. Create a distribution with your origin (S3, ALB, custom HTTP server)
2. Configure cache behaviors for different URL patterns
3. Set TTL (Time To Live) values for content expiration
4. Define cache keys (what request attributes determine a cache hit)
5. Set up origin headers to control caching
6. Configure invalidation paths for updates
7. Specify compression settings
8. Implement cache headers on your origin (Cache-Control, ETag)
9. Use versioned file names for static assets

### IAM (Identity and Access Management)

**107. What is IAM? How do you use it to manage users and permissions on AWS?**
IAM is AWS's service for securely controlling access to AWS services and resources. It helps you manage who can do what in your AWS account.

To manage users and permissions:
1. Create IAM users for individuals or services
2. Organize users into groups for easier management
3. Assign policies that define permissions
4. Follow the principle of least privilege (grant only necessary permissions)
5. Use managed policies for common scenarios
6. Create custom policies for specific needs
7. Enable MFA for enhanced security
8. Rotate access keys regularly
9. Use IAM Analyzer to identify unused permissions
10. Review access activity with CloudTrail

**108. What are IAM roles?**
IAM roles are AWS identities with specific permissions that can be assumed by entities that need temporary access:
- Services like EC2, Lambda can use roles to access other AWS services
- External users through federation can assume roles
- Roles provide temporary credentials with automatic rotation
- No passwords or long-term access keys to manage
- Can be used across accounts for secure cross-account access
- Defined by trust policies (who can assume the role) and permission policies (what they can do)

## Web Development Security

**109. How do you ensure API security in Node.js?**
To secure a Node.js API:
1. Use HTTPS for all communications
2. Implement proper authentication (JWT, OAuth)
3. Add rate limiting to prevent abuse
4. Validate all input data
5. Implement proper error handling without exposing details
6. Use Helmet.js to set security headers
7. Implement CORS correctly
8. Use parameterized queries for database operations
9. Keep dependencies updated
10. Use a web application firewall (WAF)
11. Log and monitor suspicious activities

**110. What are CSRF and XSS attacks? How do you prevent them?**
**CSRF (Cross-Site Request Forgery):** Tricks users into submitting unwanted requests.
Prevention:
- Anti-CSRF tokens in forms
- SameSite cookie attribute
- Check Origin/Referer headers
- Require explicit actions for sensitive operations

**XSS (Cross-Site Scripting):** Injects malicious scripts into web pages.
Prevention:
- Escape/encode user input
- Use Content-Security-Policy headers
- Implement HttpOnly cookies
- Sanitize HTML and JavaScript
- Use frameworks with built-in protection
- Validate input on both client and server

**111. How do you implement role-based access control (RBAC)?**
Implementing RBAC:
1. Define roles (admin, user, guest, etc.)
2. Assign permissions to each role
3. Assign users to appropriate roles
4. Store role information in a database
5. Check permissions on each protected route/resource
6. Use middleware to verify access rights

Example in Express.js:
```javascript
function checkRole(role) {
  return (req, res, next) => {
    if (!req.user) {
      return res.status(401).send('Unauthorized');
    }
    if (req.user.role !== role) {
      return res.status(403).send('Forbidden');
    }
    next();
  }
}

// Usage
app.get('/admin-dashboard', checkRole('admin'), (req, res) => {
  // Only admins can access
});
```

**112. What are JWT tokens, and how do they work?**
JWT (JSON Web Tokens) are compact, self-contained tokens for securely transmitting information between parties.

How they work:
1. User logs in with credentials
2. Server validates and creates a JWT with a payload (user data, permissions)
3. Token is signed using a secret key or private key
4. Token is sent to client and stored (localStorage, cookies)
5. Client includes token in subsequent requests (Authorization header)
6. Server verifies signature and extracts user info
7. Server grants access based on token contents

JWTs consist of three parts: header, payload, and signature, separated by dots.

**113. What is CORS, and how do you handle it in Express.js?**
CORS (Cross-Origin Resource Sharing) is a security feature that restricts web pages from making requests to domains different from the one that served the page.

Handling CORS in Express:
```javascript
// Simple CORS for all routes
const cors = require('cors');
app.use(cors());

// Configuring specific options
app.use(cors({
  origin: 'https://yourdomain.com',  // Allow only specific origin
  methods: ['GET', 'POST'],          // Allow specific methods
  allowedHeaders: ['Content-Type', 'Authorization'],
  credentials: true                  // Allow cookies
}));

// For single route
app.get('/api/data', cors(), (req, res) => {
  res.json({ data: 'Here is your data' });
});
```

## Real-time and Advanced Frontend

**114. How does WebSockets work in a real-time application?**
WebSockets provide full-duplex communication channels over a single TCP connection, enabling real-time data transfer between client and server.

Implementation:
1. Client establishes connection via handshake (HTTP upgrade)
2. Connection stays open for bi-directional communication
3. Both client and server can send messages anytime
4. Messages are sent in frames (binary or text)
5. No need for repeated HTTP requests

Example with Socket.io in Node.js:
```javascript
// Server
const io = require('socket.io')(server);
io.on('connection', (socket) => {
  console.log('User connected');
  
  socket.on('chat message', (msg) => {
    io.emit('chat message', msg); // Broadcast to all clients
  });
  
  socket.on('disconnect', () => {
    console.log('User disconnected');
  });
});

// Client
const socket = io();
socket.emit('chat message', 'Hello!');
socket.on('chat message', (msg) => {
  console.log('New message:', msg);
});
```

**115. How do you optimize images in a React application?**
Image optimization in React:
1. Use appropriate formats (WebP, AVIF for modern browsers)
2. Compress images before importing
3. Implement lazy loading
4. Use responsive images with srcset
5. Consider image CDNs like Cloudinary or Imgix
6. Use image components like Next.js Image or react-responsive-image
7. Apply proper sizing (don't use larger images than needed)
8. Use CSS for simple decorative images

Example with lazy loading:
```jsx
import { LazyLoadImage } from 'react-lazy-load-image-component';

function Product({ product }) {
  return (
    <div className="product">
      <LazyLoadImage
        src={product.imageUrl}
        alt={product.name}
        width={300}
        height={200}
        effect="blur"
      />
      <h2>{product.name}</h2>
    </div>
  );
}
```

**116. How does caching improve performance?**
Caching improves performance by:
- Reducing server load by storing copies of resources
- Decreasing latency by serving content from closer/faster storage
- Minimizing database queries by caching results
- Reducing bandwidth usage by reusing downloaded resources
- Speeding up page loads with browser cache

Implementation strategies:
1. Browser caching with proper HTTP headers
2. CDN caching for static assets
3. Application-level caching (Redis, Memcached)
4. Database query caching
5. API response caching with proper invalidation
6. Service worker caching for offline support

**117. What are web workers in JavaScript?**
Web Workers are JavaScript scripts that run in the background, separate from the main browser thread:
- Enable true multi-threading in JavaScript
- Handle CPU-intensive tasks without freezing the UI
- Cannot directly access the DOM, window or parent objects
- Communicate via messaging (postMessage API)
- Types include dedicated workers, shared workers, and service workers

Example:
```javascript
// Main thread
const worker = new Worker('worker.js');
worker.postMessage({ data: complexData });
worker.onmessage = function(e) {
  console.log('Result:', e.data);
};

// worker.js
self.onmessage = function(e) {
  const result = performComplexCalculation(e.data.data);
  self.postMessage(result);
};
```

**118. What is lazy loading in React?**
Lazy loading in React is a technique to defer loading components until they're needed, improving initial load time:

```jsx
// Instead of:
// import HeavyComponent from './HeavyComponent';

// Use:
import React, { Suspense, lazy } from 'react';

const HeavyComponent = lazy(() => import('./HeavyComponent'));

function App() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <HeavyComponent />
      </Suspense>
    </div>
  );
}
```

Benefits:
- Reduces initial bundle size
- Improves page load speed
- Components load only when needed (e.g., route changes)
- Works well with React Router for route-based code splitting

## Backend and Database

**119. How do you handle large datasets efficiently in MongoDB?**
For large MongoDB datasets:
1. Use proper indexing for query patterns
2. Implement pagination with skip/limit or cursor-based approach
3. Project only needed fields (don't return everything)
4. Use aggregation pipeline for complex operations

**119. How do you handle large datasets efficiently in MongoDB?** (continued)
5. Use MongoDB's aggregation framework for data processing
6. Implement sharding for horizontal scaling
7. Consider read replicas for distributing read operations
8. Use capped collections for high-throughput logging
9. Implement TTL indexes for auto-expiration of data
10. Batch operations when possible instead of many small operations

Example of pagination in Node.js:
```javascript
// Cursor-based pagination (more efficient than skip/limit)
const pageSize = 100;
let lastId = null;

// First page
const firstPage = await db.collection('products')
  .find({})
  .sort({ _id: 1 })
  .limit(pageSize)
  .toArray();

if (firstPage.length > 0) {
  lastId = firstPage[firstPage.length - 1]._id;
}

// Subsequent pages
const nextPage = await db.collection('products')
  .find({ _id: { $gt: lastId } })
  .sort({ _id: 1 })
  .limit(pageSize)
  .toArray();
```

**120. How do you use Redux with React?**
Using Redux with React:
1. Set up store with reducers and initial state
2. Connect React app using Provider
3. Create actions to define possible state changes
4. Build reducers to handle state updates
5. Connect components using hooks or connect()
6. Dispatch actions to update state

Basic setup example:
```javascript
// Store setup
import { createStore } from 'redux';
import { Provider } from 'react-redux';

function counterReducer(state = { count: 0 }, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

const store = createStore(counterReducer);

// App component
function App() {
  return (
    <Provider store={store}>
      <Counter />
    </Provider>
  );
}

// Using hooks in component
import { useSelector, useDispatch } from 'react-redux';

function Counter() {
  const count = useSelector(state => state.count);
  const dispatch = useDispatch();
  
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => dispatch({ type: 'INCREMENT' })}>+</button>
      <button onClick={() => dispatch({ type: 'DECREMENT' })}>-</button>
    </div>
  );
}
```

**121. What is the difference between controlled and uncontrolled components in React?**
Controlled Components:
- Form values controlled by React state
- React is the "single source of truth"
- Component state updates on every input change
- More predictable, but requires more code
- Better for forms with validation and dynamic behavior

```jsx
function ControlledForm() {
  const [name, setName] = useState('');
  
  const handleSubmit = (e) => {
    e.preventDefault();
    console.log('Name submitted:', name);
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <input 
        type="text" 
        value={name} 
        onChange={(e) => setName(e.target.value)} 
      />
      <button type="submit">Submit</button>
    </form>
  );
}
```

Uncontrolled Components:
- DOM handles form data internally
- Uses refs to access values when needed
- Less code, but harder to perform validation
- Good for simple forms or third-party integrations

```jsx
function UncontrolledForm() {
  const nameRef = useRef();
  
  const handleSubmit = (e) => {
    e.preventDefault();
    console.log('Name submitted:', nameRef.current.value);
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <input type="text" ref={nameRef} defaultValue="" />
      <button type="submit">Submit</button>
    </form>
  );
}
```

**122. How do you prevent SQL injection in Node.js?**
Preventing SQL injection:
1. Use parameterized queries/prepared statements
2. Never concatenate user input directly into SQL strings
3. Use ORM libraries like Sequelize or TypeORM
4. Validate and sanitize all user inputs
5. Implement least privilege database users
6. Escape special characters if direct concatenation is unavoidable

Example with parameterized queries (using mysql2):
```javascript
// UNSAFE - DON'T DO THIS
app.get('/users', (req, res) => {
  const userId = req.query.id;
  const query = `SELECT * FROM users WHERE id = ${userId}`; // VULNERABLE!
  connection.query(query, (err, results) => {
    res.json(results);
  });
});

// SAFE - DO THIS
app.get('/users', (req, res) => {
  const userId = req.query.id;
  const query = 'SELECT * FROM users WHERE id = ?'; // Parameterized
  connection.query(query, [userId], (err, results) => {
    res.json(results);
  });
});
```

**123. How do you implement logging in a Node.js app?**
Implementing logging in Node.js:
1. Use a logging library like Winston, Pino, or Bunyan
2. Set up different log levels (error, warn, info, debug)
3. Configure multiple transports (console, file, database)
4. Include contextual data (request IDs, user IDs)
5. Format logs appropriately (JSON for machine parsing)
6. Implement log rotation for file logs
7. Use centralized logging for production

Example with Winston:
```javascript
const winston = require('winston');
const express = require('express');
const app = express();

// Configure logger
const logger = winston.createLogger({
  level: process.env.LOG_LEVEL || 'info',
  format: winston.format.combine(
    winston.format.timestamp(),
    winston.format.json(),
  ),
  defaultMeta: { service: 'user-service' },
  transports: [
    new winston.transports.Console(),
    new winston.transports.File({ filename: 'error.log', level: 'error' }),
    new winston.transports.File({ filename: 'combined.log' }),
  ],
});

// Middleware to log requests
app.use((req, res, next) => {
  const start = Date.now();
  res.on('finish', () => {
    logger.info({
      method: req.method,
      url: req.url,
      status: res.statusCode,
      responseTime: Date.now() - start,
      ip: req.ip
    });
  });
  next();
});

// Error handler
app.use((err, req, res, next) => {
  logger.error({
    message: err.message,
    stack: err.stack,
    method: req.method,
    url: req.url
  });
  res.status(500).send('Something went wrong');
});
```

**124. What is GraphQL, and how is it different from REST?**
GraphQL is a query language and runtime for APIs that allows clients to request exactly the data they need.

Differences from REST:
- Single endpoint vs multiple endpoints in REST
- Client specifies exact data shape vs server determines response structure
- Reduces over-fetching and under-fetching of data
- Strong typing system for API schema
- Introspection capabilities for documentation
- Built-in tooling for validation and exploration

Example GraphQL query:
```graphql
query {
  user(id: "123") {
    name
    email
    posts(last: 3) {
      title
      comments {
        text
      }
    }
  }
}
```

Equivalent REST might require multiple endpoints:
- GET /users/123
- GET /users/123/posts?limit=3
- GET /posts/:id/comments for each post

## Architecture and Performance

**125. What are the pros and cons of microservices architecture?**
Pros of microservices:
- Independent deployment of services
- Technology diversity (different languages/frameworks per service)
- Better scalability of individual components
- Easier to understand smaller codebases
- More resilient (single service failure doesn't take down entire system)
- Team autonomy and parallel development

Cons of microservices:
- Increased complexity in deployment and operations
- Network latency between services
- More difficult debugging across services
- Data consistency challenges
- More complex testing
- Potential duplication of code
- Higher infrastructure costs

**126. How do you optimize database performance?**
Database optimization techniques:
1. Create proper indexes for common queries
2. Normalize/denormalize schema appropriately for workload
3. Use connection pooling
4. Write efficient queries (avoid SELECT *)
5. Implement query caching
6. Use stored procedures for complex operations
7. Configure proper server settings (memory, cache)
8. Partition large tables
9. Implement read replicas for read-heavy workloads
10. Regular maintenance (vacuum, reindex)
11. Monitor slow queries and optimize
12. Consider database-specific optimization techniques

**127. What are observables in JavaScript?**
Observables are objects that represent a collection of future values or events:
- Part of Reactive Programming pattern (RxJS library)
- Similar to Promises but handle multiple values over time
- Support operations like map, filter, reduce
- Can be canceled, unlike Promises
- Work with streaming data and event-based systems

Example with RxJS:
```javascript
import { fromEvent } from 'rxjs';
import { debounceTime, map } from 'rxjs/operators';

// Create an observable from input events
const input = document.querySelector('input');
const inputObservable = fromEvent(input, 'input').pipe(
  debounceTime(300), // Wait for 300ms pause in events
  map(event => event.target.value)
);

// Subscribe to the observable
const subscription = inputObservable.subscribe(value => {
  console.log('Search term:', value);
  // Make API call with search term
});

// Later, unsubscribe when done
subscription.unsubscribe();
```

**128. How do you automate deployment using GitHub Actions?**
Automating deployment with GitHub Actions:
1. Create a workflow file (.github/workflows/deploy.yml)
2. Define triggers (push to main, pull request, etc.)
3. Set up build environment and dependencies
4. Configure authentication for deployment target
5. Define build steps
6. Add deployment commands
7. Configure notifications and reports

Example workflow for Node.js app deploying to AWS:

```yaml
name: Deploy to AWS

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v2
    
    - name: Set up Node.js
      uses: actions/setup-node@v2
      with:
        node-version: '16'
        
    - name: Install dependencies
      run: npm ci
      
    - name: Run tests
      run: npm test
      
    - name: Build application
      run: npm run build
      
    - name: Configure AWS credentials
      uses: aws-actions/configure-aws-credentials@v1
      with:
        aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
        aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
        aws-region: us-east-1
        
    - name: Deploy to S3
      run: |
        aws s3 sync ./build s3://my-app-bucket --delete
        
    - name: Invalidate CloudFront
      run: |
        aws cloudfront create-invalidation --distribution-id ${{ secrets.CLOUDFRONT_DISTRIBUTION_ID }} --paths "/*"
        
    - name: Notify deployment status
      if: always()
      uses: actions/github-script@v5
      with:
        github-token: ${{ secrets.GITHUB_TOKEN }}
        script: |
          const { owner, repo } = context.repo;
          github.issues.createComment({
            owner,
            repo,
            issue_number: context.issue.number,
            body: `Deployment ${context.job} ${context.status}!`
          });
```

This deployment workflow checks out code, sets up Node.js, installs dependencies, runs tests, builds the application, configures AWS credentials using repository secrets, deploys to S3, invalidates CloudFront cache, and adds a notification comment.