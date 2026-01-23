# Head First JavaScript Cheatsheet

> Your brain on JavaScript. Here you'll learn the language of the web the way your brain likes to learn - with conversational style, practical examples, and exercises that make concepts stick.

---

## How to Use This Cheatsheet

**We think of JavaScript as powerful, not puzzling.** You'll find Q&A sections, "Watch It!" warnings, "Brain Power" exercises, and lots of conversation. JavaScript has quirks, but we'll make them make sense.

**The activities are NOT optional.** The exercises and challenges are part of the learning experience. Open your browser console (F12) and try the code!

**The redundancy is intentional.** JavaScript concepts build on each other. You'll see scoping, closures, and `this` pop up again and again - that's how it clicks.

---

## Table of Contents

1. [Introduction: What is JavaScript?](#1-introduction-what-is-javascript)
2. [Variables: Storing Data](#2-variables-storing-data)
3. [Data Types: Primitive and Objects](#3-data-types-primitive-and-objects)
4. [Operators: Doing Math and Logic](#4-operators-doing-math-and-logic)
5. [Control Flow: Making Decisions](#5-control-flow-making-decisions)
6. [Loops: Doing Things Repeatedly](#6-loops-doing-things-repeatedly)
7. [Functions: Reusable Code](#7-functions-reusable-code)
8. [Arrays: Lists of Things](#8-arrays-lists-of-things)
9. [Objects: Key-Value Pairs](#9-objects-key-value-pairs)
10. [The 'this' Keyword: Context Matters](#10-the-this-keyword-context-matters)
11. [Asynchronous JavaScript: Dealing with Time](#11-asynchronous-javascript-dealing-with-time)
12. [Promises and Async/Await: Better Async](#12-promises-and-asyncawait-better-async)
13. [Classes: Object-Oriented JavaScript](#13-classes-object-oriented-javascript)
14. [Modules: Organizing Code](#14-modules-organizing-code)
15. [DOM and APIs: Interacting with the Web](#15-dom-and-apis-interacting-with-the-web)
16. [Regular Expressions: Pattern Matching](#16-regular-expressions-pattern-matching)
17. [Map and Set: Modern Collections](#17-map-and-set-modern-collections)
18. [Strings, Dates, and JSON: Essential Built-ins](#18-strings-dates-and-json-essential-built-ins)

---

## 1. Introduction: What is JavaScript?

### JavaScript: The language of the web

Remember HTML and CSS? HTML is structure, CSS is style. **JavaScript is behavior.** It makes websites interactive, handles user input, fetches data, and brings pages to life.

**JavaScript ≠ Java** (completely different languages, confusingly similar names!)

### History: From 10 days to world domination

- **1995:** Created by Brendan Eich in 10 days (explains some quirks!)
- **1997:** ECMAScript standard created
- **2009:** Node.js brings JavaScript to servers
- **2015:** ES6/ES2015 - massive improvements
- **Now:** Most popular programming language

### JavaScript Versions (ECMAScript)

- **ES5 (2009):** Old reliable
- **ES6/ES2015:** Modern JavaScript begins (arrow functions, classes, promises)
- **ES2016-ES2023:** Yearly updates with new features
- **"Modern JavaScript":** Usually means ES6+

### How to run JavaScript

```javascript
// 1. Browser console (F12 → Console)
console.log('Hello World');

// 2. HTML script tag
// <script>
//     console.log('Hello World');
// </script>

// 3. External file
// <script src="script.js"></script>

// 4. Node.js (terminal)
// node script.js
```

### Your first JavaScript program

```javascript
console.log('Hello, World!');
// Output: Hello, World!

alert('Hello!'); // Shows popup (browser only)

document.write('Hello!'); // Writes to page (not recommended)
```

### Brain Power
🧠 Why do you think JavaScript was created in just 10 days? What problems do you think that might cause?

**Answer:** Speed! Netscape needed a scripting language fast. But rushing led to quirks and inconsistencies that we still deal with today (like `==` vs `===`, hoisting, etc.).

### Watch It!
⚠️ **JavaScript runs in different environments!** Browser JavaScript has `window`, `document`, `alert`. Node.js has `process`, `require`, file system access. Code doesn't always work everywhere.

### There are NO Dumb Questions

**Q: Is JavaScript compiled or interpreted?**
**A:** Both! Modern JavaScript engines (V8, SpiderMonkey) use Just-In-Time (JIT) compilation - they compile code right before running it.

**Q: Do I need to learn ES5 or can I start with ES6?**
**A:** Start with ES6+! It's cleaner and more powerful. Learn ES5 quirks when you encounter old code.

**Q: What's the difference between JavaScript and ECMAScript?**
**A:** ECMAScript is the standard/specification. JavaScript is the implementation. Think of ECMAScript as the rules, JavaScript as the game.

---

## 2. Variables: Storing Data

### What are variables?

Variables are containers for storing data. Like labeled boxes where you put things.

```javascript
let name = 'Alice';
let age = 25;
let isStudent = true;
```

### The Three Ways to Declare Variables

#### var: The old way (avoid it!)

```javascript
var name = 'Bob';
var name = 'Alice'; // Can redeclare (bad!)
name = 'Charlie';   // Can reassign
```

**Problems with var:**
- Function scoped (not block scoped)
- Can be redeclared
- Hoisted (weird behavior)
- No temporal dead zone

#### let: The modern way

```javascript
let name = 'Alice';
// let name = 'Bob'; // Error: can't redeclare
name = 'Bob';        // Can reassign (OK)
```

**let is:**
- Block scoped
- Can't be redeclared
- Can be reassigned
- Has temporal dead zone

#### const: For constants

```javascript
const PI = 3.14159;
// PI = 3.14; // Error: can't reassign

const person = { name: 'Alice' };
person.name = 'Bob';  // OK: can modify object properties
// person = {};       // Error: can't reassign variable
```

**const is:**
- Block scoped
- Can't be redeclared
- Can't be reassigned
- Object/array contents CAN be modified

### Brain Power
🧠 When should you use `let` vs `const`?

**Answer:** Use `const` by default! Only use `let` when you know the variable will be reassigned. This makes your code clearer - readers know when values change.

### Variable Naming Rules

```javascript
// Valid names
let firstName = 'Alice';
let first_name = 'Alice';
let firstName2 = 'Alice';
let $name = 'Alice';
let _name = 'Alice';

// Invalid names
// let 2name = 'Alice';    // Can't start with number
// let first-name = 'Alice'; // No hyphens
// let let = 'Alice';      // Can't use keywords
// let first name = 'Alice'; // No spaces

// Conventions
let firstName;  // camelCase (recommended)
let FirstName;  // PascalCase (for classes)
let FIRST_NAME; // SCREAMING_SNAKE_CASE (for constants)
```

### Variable Scopes: Where can you use it?

#### Block Scope

```javascript
{
    let x = 10;
    const y = 20;
    var z = 30;
}

// console.log(x); // Error: x not defined
// console.log(y); // Error: y not defined
console.log(z);    // 30 (var is NOT block scoped!)
```

#### Function Scope

```javascript
function myFunction() {
    let x = 10;
    const y = 20;
    var z = 30;
}

// console.log(x); // Error
// console.log(y); // Error
// console.log(z); // Error (all are function scoped)
```

#### Global Scope

```javascript
let globalVar = 'I am global';

function test() {
    console.log(globalVar); // Can access global
}

test(); // 'I am global'
```

### Hoisting: JavaScript's weird behavior

```javascript
// Variables are "hoisted" to the top
console.log(x); // undefined (not error!)
var x = 5;

// What JavaScript actually does:
var x;
console.log(x); // undefined
x = 5;

// let and const ARE hoisted, but stay in the "Temporal Dead Zone"
// until their declaration is reached
// console.log(y); // Error: Cannot access before initialization
let y = 5;
```

### Watch It!
⚠️ **Always use `let` or `const`, never `var`!** `var` has confusing scoping rules and hoisting behavior. Modern JavaScript (ES6+) uses `let` and `const`.

### Interview: var vs let vs const

**Head First: Welcome to the show! So, var, you've been around since the beginning?**

**var:** That's right! I'm the OG. Been here since 1995.

**HF: And let, const, you two are newer?**

**let:** We arrived in ES6 (2015). We fixed a lot of var's... issues.

**const:** Yeah, we're var's cooler, smarter siblings.

**HF: What's wrong with var?**

**var:** Hey! I'm function scoped, hoisted, and flexible!

**let:** "Flexible" means "unpredictable." You can be redeclared, which causes bugs.

**const:** And your hoisting behavior is confusing!

**var:** *Grumbles* Fine, use them. I'll just be over here in legacy code.

### Complete Variable Example

```javascript
// Bad (old way)
var name = 'Alice';
var age = 25;
var age = 30; // Oops, redeclared!

// Good (modern way)
const PI = 3.14159;        // Never changes
let score = 0;             // Will change
const user = {             // Object reference won't change
    name: 'Alice',
    age: 25
};

// Block scope example
if (true) {
    let blockScoped = 'inside';
    const alsoBlock = 'inside';
}

// console.log(blockScoped); // Error: not defined
```

### There are NO Dumb Questions

**Q: Why does `var` still exist if it's bad?**
**A:** Backwards compatibility! Removing it would break millions of websites. JavaScript never removes features.

**Q: Can I use `const` with objects and arrays?**
**A:** Yes! `const` prevents reassignment, not mutation. You can't change what the variable points to, but you can change what's inside.

**Q: What's the temporal dead zone?**
**A:** The period between entering scope and the variable declaration. `let` and `const` can't be accessed in this zone (unlike `var` which returns `undefined`).

---

## 3. Data Types: Primitive and Objects

### JavaScript has 8 data types

**7 Primitive Types:** (immutable, stored by value)
1. String
2. Number
3. BigInt
4. Boolean
5. Undefined
6. Null
7. Symbol

**1 Object Type:** (mutable, stored by reference)
- Object (includes arrays, functions, dates, etc.)

### String: Text data

```javascript
let single = 'Hello';
let double = "World";
let backtick = `Hello World`; // Template literal

// Template literals (powerful!)
let name = 'Alice';
let greeting = `Hello, ${name}!`; // Hello, Alice!

let math = `2 + 2 = ${2 + 2}`; // 2 + 2 = 4

// Multi-line
let multi = `Line 1
Line 2
Line 3`;

// String properties and methods
'hello'.length;           // 5
'hello'.toUpperCase();    // 'HELLO'
'HELLO'.toLowerCase();    // 'hello'
'hello'.charAt(0);        // 'h'
'hello'.includes('ell');  // true
'hello world'.split(' '); // ['hello', 'world']
'  hello  '.trim();       // 'hello'
```

### Number: Integer and decimal

```javascript
let integer = 42;
let decimal = 3.14;
let negative = -10;
let scientific = 1e6; // 1,000,000

// Special numbers
let infinity = Infinity;
let negInfinity = -Infinity;
let notANumber = NaN; // "Not a Number"

// Math operations
let sum = 5 + 3;      // 8
let difference = 5 - 3; // 2
let product = 5 * 3;   // 15
let quotient = 5 / 2;  // 2.5
let remainder = 5 % 2; // 1
let power = 2 ** 3;    // 8

// Number methods
Number.isInteger(42);     // true
Number.isNaN(NaN);        // true
parseInt('42');           // 42
parseFloat('3.14');       // 3.14
(3.14159).toFixed(2);     // '3.14'
```

### BigInt: Really big numbers

```javascript
let bigNum = 9007199254740991n; // Note the 'n'
let big = BigInt(123);

// Can't mix BigInt and Number
// let mixed = 10n + 5; // Error!
let correct = 10n + 5n; // 15n
```

### Boolean: True or false

```javascript
let isTrue = true;
let isFalse = false;

// Truthy values (act like true)
if (1) { }         // truthy
if ('hello') { }   // truthy
if ([]) { }        // truthy (empty array)
if ({}) { }        // truthy (empty object)

// Falsy values (act like false)
if (0) { }         // falsy
if ('') { }        // falsy (empty string)
if (null) { }      // falsy
if (undefined) { } // falsy
if (NaN) { }       // falsy
if (false) { }     // falsy
```

### Undefined: Variable declared but not assigned

```javascript
let x;
console.log(x); // undefined

let obj = {};
console.log(obj.missing); // undefined

function noReturn() {}
console.log(noReturn()); // undefined
```

### Null: Intentionally empty

```javascript
let nothing = null; // Deliberately empty

// null vs undefined
let notAssigned; // undefined (forgot to assign)
let empty = null; // null (intentionally empty)
```

### Symbol: Unique identifier

```javascript
let sym1 = Symbol('id');
let sym2 = Symbol('id');

console.log(sym1 === sym2); // false (always unique!)

// Used for object properties
let id = Symbol('id');
let user = {
    [id]: 12345
};
```

### Object: Key-value pairs

```javascript
let person = {
    name: 'Alice',
    age: 25,
    isStudent: true
};

// Access properties
console.log(person.name);    // 'Alice'
console.log(person['age']);  // 25

// Add property
person.city = 'NYC';

// Delete property
delete person.age;
```

### typeof operator: Check data type

```javascript
typeof 'hello';        // 'string'
typeof 42;             // 'number'
typeof true;           // 'boolean'
typeof undefined;      // 'undefined'
typeof null;           // 'object' (JavaScript bug!)
typeof Symbol('id');   // 'symbol'
typeof 123n;           // 'bigint'
typeof {};             // 'object'
typeof [];             // 'object' (arrays are objects)
typeof function() {};  // 'function'
```

### Watch It!
⚠️ **`typeof null` returns 'object'!** This is a famous JavaScript bug that can't be fixed (would break the web). `null` is NOT an object!

### Type Conversion: Changing types

```javascript
// Explicit conversion (you do it)
String(123);           // '123'
Number('123');         // 123
Boolean(1);            // true

// Implicit conversion (JavaScript does it)
'5' + 3;               // '53' (number to string)
'5' - 3;               // 2 (string to number)
'5' * '2';             // 10 (both to numbers)
!!'hello';             // true (to boolean)
```

### Brain Power
🧠 What's the difference between `null` and `undefined`?

**Answer:**
- `undefined` = JavaScript's way of saying "I don't know what this is"
- `null` = Your way of saying "This is intentionally empty"

### Complete Data Types Example

```javascript
// Primitives (immutable)
const name = 'Alice';          // string
const age = 25;                // number
const isStudent = true;        // boolean
const big = 9999999999999n;    // bigint
const nothing = null;          // null
const unknown = undefined;     // undefined
const id = Symbol('id');       // symbol

// Object (mutable)
const person = {
    name: 'Alice',
    age: 25,
    greet: function() {
        console.log(`Hi, I'm ${this.name}`);
    }
};

// Arrays (special objects)
const numbers = [1, 2, 3, 4, 5];
const mixed = [1, 'hello', true, null, {}];

// Type checking
console.log(typeof name);      // 'string'
console.log(typeof numbers);   // 'object'
console.log(Array.isArray(numbers)); // true
```

### There are NO Dumb Questions

**Q: Why do we need BigInt when we have Number?**
**A:** Number can only safely represent integers up to 2^53 - 1. BigInt handles arbitrarily large integers (for cryptography, IDs, etc.).

**Q: What's the difference between '===' and typeof?**
**A:** `===` compares values. `typeof` returns the type as a string. Different purposes!

**Q: Are arrays primitive or objects?**
**A:** Objects! Arrays are special objects with numeric keys and extra methods (push, pop, etc.).

---

## 4. Operators: Doing Math and Logic

### Arithmetic Operators: Math basics

```javascript
let a = 10, b = 3;

a + b;  // 13 (addition)
a - b;  // 7 (subtraction)
a * b;  // 30 (multiplication)
a / b;  // 3.333... (division)
a % b;  // 1 (remainder/modulo)
a ** b; // 1000 (exponentiation, ES2016)

// Increment/Decrement
let x = 5;
x++;    // x = 6 (post-increment)
++x;    // x = 7 (pre-increment)
x--;    // x = 6 (post-decrement)
--x;    // x = 5 (pre-decrement)

// Pre vs Post
let y = 5;
let z = y++;  // z = 5, y = 6 (use then increment)
let w = ++y;  // w = 7, y = 7 (increment then use)
```

### Assignment Operators: Shortcuts

```javascript
let x = 10;

x += 5;   // x = x + 5   (15)
x -= 3;   // x = x - 3   (12)
x *= 2;   // x = x * 2   (24)
x /= 4;   // x = x / 4   (6)
x %= 4;   // x = x % 4   (2)
x **= 3;  // x = x ** 3  (8)

// Multiple assignment (same type)
let a = 10, b = 10, c = 10;
```

### Comparison Operators: True or false

```javascript
5 == 5;    // true (loose equality, converts types)
5 == '5';  // true (string converted to number)

5 === 5;   // true (strict equality, no conversion)
5 === '5'; // false (different types)

5 != 6;    // true (not equal, loose)
5 !== '5'; // true (not equal, strict)

5 > 3;     // true
5 >= 5;    // true
3 < 5;     // true
5 <= 5;    // true
```

### Watch It!
⚠️ **Always use `===` and `!==`, never `==` and `!=`!** Loose equality has weird type coercion rules. `[] == false` is true, but `[] === false` is false. Strict equality is predictable!

### Logical Operators: Combining conditions

```javascript
// AND (&&) - both must be true
true && true;   // true
true && false;  // false

let age = 25;
age > 18 && age < 65;  // true

// OR (||) - at least one must be true
true || false;  // true
false || false; // false

age < 18 || age > 65; // false

// NOT (!) - flip the boolean
!true;   // false
!false;  // true

let isAdmin = false;
if (!isAdmin) {
    console.log('Not an admin');
}

// Nullish coalescing (??) - ES2020
let name = null;
let displayName = name ?? 'Guest'; // 'Guest'

let count = 0;
let value = count ?? 10; // 0 (not nullish!)

// Optional chaining (?.) - ES2020
let user = {};
let street = user?.address?.street; // undefined (no error!)
```

### Brain Power
🧠 What's the difference between `||` and `??`?

**Answer:**
- `||` returns right side if left is FALSY (0, '', false, null, undefined, NaN)
- `??` returns right side if left is NULLISH (null or undefined only)
```javascript
0 || 10;   // 10 (0 is falsy)
0 ?? 10;   // 0 (0 is not nullish)
```

### Ternary Operator: Inline if-else

```javascript
// condition ? valueIfTrue : valueIfFalse
let age = 20;
let status = age >= 18 ? 'adult' : 'minor';

// Nested ternary (use sparingly!)
let num = 0;
let sign = num > 0 ? 'positive' : num < 0 ? 'negative' : 'zero';
```

### String Operators: Concatenation

```javascript
'Hello' + ' ' + 'World';  // 'Hello World'

let name = 'Alice';
'Hello ' + name;  // 'Hello Alice'

// Template literals (better!)
`Hello ${name}`;  // 'Hello Alice'
```

### Bitwise Operators: Low-level operations

```javascript
5 & 3;   // 1 (AND)
5 | 3;   // 7 (OR)
5 ^ 3;   // 6 (XOR)
~5;      // -6 (NOT)
5 << 1;  // 10 (left shift)
5 >> 1;  // 2 (right shift)
```

### typeof and instanceof

```javascript
typeof 'hello';        // 'string'
typeof 42;             // 'number'
typeof true;           // 'boolean'

[] instanceof Array;   // true
{} instanceof Object;  // true
```

### Complete Operators Example

```javascript
// Math
let total = 100;
let discount = 20;
let taxRate = 0.08;

let subtotal = total - discount;           // 80
let tax = subtotal * taxRate;               // 6.4
let finalPrice = subtotal + tax;            // 86.4

// Comparison
let age = 25;
let isAdult = age >= 18;                    // true

// Logical
let hasLicense = true;
let hasInsurance = true;
let canDrive = hasLicense && hasInsurance;  // true

// Ternary
let message = age >= 18 ? 'Can vote' : 'Cannot vote';

// Nullish coalescing
let username = null;
let display = username ?? 'Guest';          // 'Guest'

// Optional chaining
let user = { name: 'Alice' };
let email = user?.contact?.email;           // undefined
```

### There are NO Dumb Questions

**Q: Why does '5' + 3 equal '53' but '5' - 3 equal 2?**
**A:** Type coercion! `+` with strings means concatenation. `-` only works with numbers, so JavaScript converts '5' to 5. Weird, but consistent... in its own way.

**Q: What's the difference between `&&` and `||` beyond true/false?**
**A:** They return values, not just booleans! `'Alice' || 'Guest'` returns 'Alice'. `false && 'Alice'` returns false. Used for default values!

**Q: When should I use bitwise operators?**
**A:** Rarely! Only for low-level operations (flags, permissions, graphics). For most code, stick to logical operators.

---

## 5. Control Flow: Making Decisions

### if...else: The basic decision

```javascript
let age = 20;

if (age >= 18) {
    console.log('You are an adult');
}

// if...else
if (age >= 18) {
    console.log('Adult');
} else {
    console.log('Minor');
}

// if...else if...else
if (age < 13) {
    console.log('Child');
} else if (age < 18) {
    console.log('Teenager');
} else {
    console.log('Adult');
}

// Nested if
if (age >= 18) {
    if (age < 65) {
        console.log('Working age');
    } else {
        console.log('Retirement age');
    }
}
```

### Truthy and Falsy: What counts as true?

```javascript
// Falsy values (treated as false)
if (false) { }       // false itself
if (0) { }           // zero
if ('') { }          // empty string
if (null) { }        // null
if (undefined) { }   // undefined
if (NaN) { }         // NaN

// Everything else is truthy!
if (1) { }           // truthy
if ('hello') { }     // truthy
if ([]) { }          // truthy (empty array!)
if ({}) { }          // truthy (empty object!)
if (-1) { }          // truthy
```

### Watch It!
⚠️ **Empty arrays and objects are truthy!** `if ([])` and `if ({})` are TRUE. Check length/keys instead: `if (arr.length)` or `if (Object.keys(obj).length)`.

### Switch: Multiple conditions

```javascript
let day = 'Monday';

switch (day) {
    case 'Monday':
        console.log('Start of the week');
        break;
    case 'Friday':
        console.log('End of the week!');
        break;
    case 'Saturday':
    case 'Sunday':
        console.log('Weekend!');
        break;
    default:
        console.log('Midweek');
}
```

### Watch It!
⚠️ **Don't forget `break`!** Without it, execution "falls through" to the next case. This is usually a bug (but sometimes intentional).

### Brain Power
🧠 What happens if you forget `break` in a switch statement?

**Answer:** Execution continues to the next case! This is called "fall-through" and is usually unintended:
```javascript
switch (day) {
    case 'Monday':
        console.log('Monday');
        // Forgot break!
    case 'Tuesday':
        console.log('Tuesday'); // This runs too!
}
```

### Conditional (Ternary) Operator: Short if-else

```javascript
let age = 20;
let status = age >= 18 ? 'adult' : 'minor';

// Multiple ternaries (careful!)
let color = score > 90 ? 'green' :
            score > 70 ? 'yellow' :
            score > 50 ? 'orange' : 'red';
```

### Short-circuit Evaluation: Clever tricks

```javascript
// OR (||) - returns first truthy value
let name = '';
let display = name || 'Guest'; // 'Guest'

// AND (&&) - returns last value if all truthy
let user = { name: 'Alice' };
let greeting = user && user.name; // 'Alice'

// Nullish coalescing (??) - only null/undefined
let count = 0;
let value1 = count || 10;  // 10 (0 is falsy)
let value2 = count ?? 10;  // 0 (0 is not null/undefined)
```

### Exception Handling: Dealing with errors

```javascript
// try...catch
try {
    // Code that might throw an error
    let result = riskyOperation();
} catch (error) {
    console.error('Error:', error.message);
} finally {
    // Always runs (cleanup code)
    console.log('Cleanup');
}

// Throwing errors
function divide(a, b) {
    if (b === 0) {
        throw new Error('Cannot divide by zero!');
    }
    return a / b;
}

try {
    divide(10, 0);
} catch (error) {
    console.log(error.message); // 'Cannot divide by zero!'
}

// Error types
throw new Error('Generic error');
throw new TypeError('Wrong type');
throw new ReferenceError('Variable not found');
throw new RangeError('Number out of range');
```

### Complete Control Flow Example

```javascript
function processAge(age) {
    // Input validation
    if (typeof age !== 'number') {
        throw new TypeError('Age must be a number');
    }

    if (age < 0) {
        throw new RangeError('Age cannot be negative');
    }

    // Main logic
    let category;

    if (age < 13) {
        category = 'child';
    } else if (age < 18) {
        category = 'teenager';
    } else if (age < 65) {
        category = 'adult';
    } else {
        category = 'senior';
    }

    // Switch for pricing
    let price;
    switch (category) {
        case 'child':
            price = 10;
            break;
        case 'teenager':
            price = 15;
            break;
        case 'adult':
            price = 20;
            break;
        case 'senior':
            price = 12;
            break;
        default:
            price = 20;
    }

    return {
        category,
        price,
        message: `You are a ${category}. Ticket price: $${price}`
    };
}

// Usage
try {
    console.log(processAge(25));  // { category: 'adult', price: 20, ... }
    console.log(processAge(-5));  // Throws error
} catch (error) {
    console.error('Error:', error.message);
}
```

### There are NO Dumb Questions

**Q: Should I use if-else or switch?**
**A:** Use if-else for ranges (`age < 18`) and complex conditions. Use switch for exact value matching (like `day === 'Monday'`).

**Q: What's the difference between throw and return?**
**A:** `return` exits the function normally with a value. `throw` exits the function abnormally with an error (and can be caught with try-catch).

**Q: When should I use ternary operator vs if-else?**
**A:** Ternary for simple assignments. If-else for complex logic or multiple statements. If it's hard to read, use if-else!

---

## 6. Loops: Doing Things Repeatedly

### for loop: Classic iteration

```javascript
for (let i = 0; i < 5; i++) {
    console.log(i); // 0, 1, 2, 3, 4
}

// Countdown
for (let i = 5; i > 0; i--) {
    console.log(i); // 5, 4, 3, 2, 1
}

// Step by 2
for (let i = 0; i < 10; i += 2) {
    console.log(i); // 0, 2, 4, 6, 8
}
```

### while loop: Keep going until...

```javascript
let count = 0;

while (count < 5) {
    console.log(count); // 0, 1, 2, 3, 4
    count++;
}

// Watch out for infinite loops!
// while (true) {
//     console.log('Forever!'); // BAD!
// }
```

### do...while loop: At least once

```javascript
let count = 0;

do {
    console.log(count); // 0, 1, 2, 3, 4
    count++;
} while (count < 5);

// Runs at least once, even if condition is false
let x = 10;
do {
    console.log(x); // 10 (runs once!)
} while (x < 5);
```

### for...of loop: Iterate over values

```javascript
// Arrays
let numbers = [1, 2, 3, 4, 5];

for (let num of numbers) {
    console.log(num); // 1, 2, 3, 4, 5
}

// Strings
let name = 'Alice';

for (let char of name) {
    console.log(char); // A, l, i, c, e
}

// With index
for (let [index, value] of numbers.entries()) {
    console.log(index, value); // 0 1, 1 2, 2 3, ...
}
```

### for...in loop: Iterate over keys

```javascript
// Objects
let person = {
    name: 'Alice',
    age: 25,
    city: 'NYC'
};

for (let key in person) {
    console.log(key, person[key]);
    // 'name' 'Alice'
    // 'age' 25
    // 'city' 'NYC'
}

// Arrays (not recommended!)
let arr = [10, 20, 30];

for (let index in arr) {
    console.log(index, arr[index]); // 0 10, 1 20, 2 30
}
```

### Watch It!
⚠️ **Use `for...of` for arrays, `for...in` for objects!** `for...in` on arrays gives you string indices ('0', '1', '2') and includes prototype properties.

### break: Exit the loop

```javascript
for (let i = 0; i < 10; i++) {
    if (i === 5) {
        break; // Exit loop completely
    }
    console.log(i); // 0, 1, 2, 3, 4
}
```

### continue: Skip to next iteration

```javascript
for (let i = 0; i < 10; i++) {
    if (i % 2 === 0) {
        continue; // Skip even numbers
    }
    console.log(i); // 1, 3, 5, 7, 9
}
```

### Brain Power
🧠 What's the difference between `for...of` and `for...in`?

**Answer:**
- `for...of` loops over VALUES (use for arrays, strings)
- `for...in` loops over KEYS (use for objects)

```javascript
let arr = ['a', 'b', 'c'];
for (let value of arr) { console.log(value); } // 'a', 'b', 'c'
for (let key in arr) { console.log(key); }     // 0, 1, 2
```

### Array Methods: Modern iteration

```javascript
let numbers = [1, 2, 3, 4, 5];

// forEach - do something for each item
numbers.forEach(num => {
    console.log(num); // 1, 2, 3, 4, 5
});

// map - transform each item
let doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10]

// filter - keep items that match
let evens = numbers.filter(num => num % 2 === 0);
console.log(evens); // [2, 4]

// reduce - accumulate to single value
let sum = numbers.reduce((total, num) => total + num, 0);
console.log(sum); // 15

// find - get first match
let found = numbers.find(num => num > 3);
console.log(found); // 4

// some - check if any match
let hasEven = numbers.some(num => num % 2 === 0);
console.log(hasEven); // true

// every - check if all match
let allPositive = numbers.every(num => num > 0);
console.log(allPositive); // true
```

### Complete Loops Example

```javascript
// Find prime numbers up to 50
function findPrimes(max) {
    let primes = [];

    // Loop through numbers
    for (let num = 2; num <= max; num++) {
        let isPrime = true;

        // Check if divisible by any number
        for (let i = 2; i < num; i++) {
            if (num % i === 0) {
                isPrime = false;
                break; // Not prime, exit inner loop
            }
        }

        if (isPrime) {
            primes.push(num);
        }
    }

    return primes;
}

console.log(findPrimes(50));
// [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47]

// Modern array methods approach
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

let results = numbers
    .filter(num => num % 2 === 0)    // Get evens: [2, 4, 6, 8, 10]
    .map(num => num * num)            // Square: [4, 16, 36, 64, 100]
    .reduce((sum, num) => sum + num); // Sum: 220

console.log(results); // 220
```

### There are NO Dumb Questions

**Q: When should I use for vs while?**
**A:** Use `for` when you know how many iterations. Use `while` when you loop until a condition changes.

**Q: What's the difference between forEach and map?**
**A:** `forEach` does something for each item (no return). `map` transforms each item and returns a new array.

**Q: Can I use break in forEach?**
**A:** No! `forEach` can't be interrupted. Use a regular `for` loop or `for...of` if you need `break`.

---

## 7. Functions: Reusable Code

### Function Declaration

```javascript
function greet(name) {
    return `Hello, ${name}!`;
}

console.log(greet('Alice')); // 'Hello, Alice!'
```

### Function Expression

```javascript
const greet = function(name) {
    return `Hello, ${name}!`;
};
```

### Arrow Functions: Modern syntax

```javascript
// Traditional function expression
const addTraditional = function(a, b) {
    return a + b;
};

// Arrow function (full form)
const addArrow = (a, b) => {
    return a + b;
};

// Arrow function (implicit return)
const addShort = (a, b) => a + b;

// Single parameter (no parentheses needed)
const double = x => x * 2;

// No parameters
const random = () => Math.random();
```

### Function Hoisting

```javascript
// Function declarations are hoisted (can be called before definition)
sayHello(); // Works!
function sayHello() {
    console.log('Hello!');
}

// Function expressions are NOT hoisted
// sayBye(); // Error: Cannot access before initialization
const sayBye = function() {
    console.log('Bye!');
};

// Arrow functions are NOT hoisted either
// greet(); // Error!
const greet = () => console.log('Hi!');
```

### Watch It!
⚠️ **Function declarations are hoisted, expressions are not!** This means you can call a `function` declaration before it appears in the code, but not a `const`/`let` function expression or arrow function.

### Parameters and Arguments

```javascript
// Default parameters
function greet(name = 'Guest') {
    return `Hello, ${name}!`;
}

greet();        // 'Hello, Guest!'
greet('Alice'); // 'Hello, Alice!'

// Rest parameters
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}

sum(1, 2, 3, 4, 5); // 15

// Destructuring parameters
function displayUser({ name, age }) {
    console.log(`${name} is ${age} years old`);
}

displayUser({ name: 'Alice', age: 25 });
```

### Higher-Order Functions

```javascript
// Functions that take or return other functions

// Taking a function as argument
function repeat(n, action) {
    for (let i = 0; i < n; i++) {
        action(i);
    }
}

repeat(3, console.log); // 0, 1, 2

// Returning a function
function multiplier(factor) {
    return (number) => number * factor;
}

const double = multiplier(2);
const triple = multiplier(3);
double(5);  // 10
triple(5);  // 15

// Real-world: function composition
const compose = (...fns) => (x) => fns.reduceRight((acc, fn) => fn(acc), x);

const addOne = x => x + 1;
const square = x => x * x;
const negate = x => -x;

const transform = compose(negate, square, addOne);
transform(2); // -(3²) = -9
```

### Closures: Functions remember

```javascript
function createCounter() {
    let count = 0; // Private variable

    return function() {
        count++;
        return count;
    };
}

const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3

// Closure with multiple methods
function createWallet(initialBalance) {
    let balance = initialBalance;

    return {
        deposit(amount) { balance += amount; },
        withdraw(amount) { balance -= amount; },
        getBalance() { return balance; }
    };
}

const wallet = createWallet(100);
wallet.deposit(50);
wallet.getBalance(); // 150
```

### IIFE: Immediately Invoked Function Expressions

```javascript
// Runs immediately, creates its own scope
(function() {
    let secret = 'hidden';
    console.log('I run immediately!');
})();

// console.log(secret); // Error: not defined

// Arrow IIFE
(() => {
    console.log('Arrow IIFE!');
})();

// With parameters
const result = ((x, y) => x + y)(3, 4); // 7
```

### Recursion: Functions calling themselves

```javascript
// Factorial: 5! = 5 × 4 × 3 × 2 × 1
function factorial(n) {
    if (n <= 1) return 1; // Base case
    return n * factorial(n - 1); // Recursive case
}

factorial(5); // 120

// Flatten nested arrays
function flatten(arr) {
    return arr.reduce((flat, item) => {
        return flat.concat(Array.isArray(item) ? flatten(item) : item);
    }, []);
}

flatten([1, [2, [3, [4]]]]); // [1, 2, 3, 4]
```

### Brain Power
🧠 What is a closure and why is it useful?

**Answer:** A closure is a function that remembers variables from its outer scope, even after the outer function has returned. Useful for private variables, factories, and maintaining state!

### Complete Functions Example

```javascript
// Function pipeline builder
function pipe(...fns) {
    return function(input) {
        return fns.reduce((value, fn) => fn(value), input);
    };
}

// Utility functions
const trim = str => str.trim();
const lowercase = str => str.toLowerCase();
const split = separator => str => str.split(separator);
const join = separator => arr => arr.join(separator);
const map = fn => arr => arr.map(fn);
const capitalize = str => str.charAt(0).toUpperCase() + str.slice(1);

// Build a slug generator using composition
const slugify = pipe(
    trim,
    lowercase,
    split(' '),
    join('-')
);

slugify('  Hello World Example  '); // 'hello-world-example'

// Build a title case converter
const titleCase = pipe(
    trim,
    lowercase,
    split(' '),
    map(capitalize),
    join(' ')
);

titleCase('hello world'); // 'Hello World'
```

### There are NO Dumb Questions

**Q: When should I use a function declaration vs arrow function?**
**A:** Use declarations for top-level named functions (hoisting is helpful). Use arrows for callbacks, array methods, and short inline functions. Use regular function expressions when you need `this` binding.

**Q: What's the difference between arguments and parameters?**
**A:** Parameters are the names in the function definition. Arguments are the actual values passed when calling the function. `function add(a, b)` — `a`, `b` are parameters. `add(2, 3)` — `2`, `3` are arguments.

**Q: Can a function have too many parameters?**
**A:** Generally, more than 3 parameters is a code smell. Use an options object instead: `function createUser({ name, age, email })` is cleaner than `function createUser(name, age, email)`.

---

## 8. Arrays: Lists of Things

### What are arrays?

Arrays are ordered collections of values. Like a numbered list where each item has an index (starting at 0).

```javascript
let fruits = ['apple', 'banana', 'cherry'];
let mixed = [1, 'hello', true, null, { name: 'Alice' }];
let empty = [];

// Access by index
console.log(fruits[0]); // 'apple'
console.log(fruits[2]); // 'cherry'
console.log(fruits.length); // 3
```

### Creating Arrays

```javascript
// Array literal (preferred)
let colors = ['red', 'green', 'blue'];

// Array constructor (rarely used)
let numbers = new Array(1, 2, 3);
let sized = new Array(5); // Empty array with length 5

// Array.from (convert to array)
let chars = Array.from('hello'); // ['h', 'e', 'l', 'l', 'o']
let range = Array.from({ length: 5 }, (_, i) => i); // [0, 1, 2, 3, 4]

// Array.of
let arr = Array.of(1, 2, 3); // [1, 2, 3]
```

### Adding and Removing Elements

```javascript
let arr = [1, 2, 3];

// End of array
arr.push(4);         // [1, 2, 3, 4] - add to end
arr.pop();           // [1, 2, 3] - remove from end

// Beginning of array
arr.unshift(0);      // [0, 1, 2, 3] - add to beginning
arr.shift();         // [1, 2, 3] - remove from beginning

// Middle of array (splice)
arr.splice(1, 0, 'a');   // [1, 'a', 2, 3] - insert at index 1
arr.splice(1, 1);        // [1, 2, 3] - remove 1 item at index 1
arr.splice(1, 1, 'b');   // [1, 'b', 3] - replace 1 item at index 1
```

### Watch It!
⚠️ **`push`/`pop` are faster than `unshift`/`shift`!** Adding/removing from the beginning requires re-indexing every element. Use push/pop when order doesn't matter.

### Searching Arrays

```javascript
let fruits = ['apple', 'banana', 'cherry', 'banana'];

// Find index
fruits.indexOf('banana');      // 1 (first occurrence)
fruits.lastIndexOf('banana');  // 3 (last occurrence)
fruits.indexOf('grape');       // -1 (not found)

// Check existence
fruits.includes('cherry');     // true
fruits.includes('grape');      // false

// Find with condition
let numbers = [1, 5, 10, 15, 20];
numbers.find(n => n > 8);          // 10 (first match)
numbers.findIndex(n => n > 8);     // 2 (index of first match)
```

### Transforming Arrays

```javascript
let numbers = [1, 2, 3, 4, 5];

// map - transform each element
let doubled = numbers.map(n => n * 2);
// [2, 4, 6, 8, 10]

// filter - keep elements that pass test
let evens = numbers.filter(n => n % 2 === 0);
// [2, 4]

// reduce - accumulate into single value
let sum = numbers.reduce((acc, n) => acc + n, 0);
// 15

// flat - flatten nested arrays
let nested = [[1, 2], [3, 4], [5]];
nested.flat(); // [1, 2, 3, 4, 5]

// flatMap - map then flatten
let sentences = ['hello world', 'foo bar'];
sentences.flatMap(s => s.split(' '));
// ['hello', 'world', 'foo', 'bar']
```

### Sorting Arrays

```javascript
// Alphabetical sort (default)
let fruits = ['cherry', 'apple', 'banana'];
fruits.sort(); // ['apple', 'banana', 'cherry']

// Numeric sort (need compare function!)
let numbers = [10, 1, 21, 2];
numbers.sort();                    // [1, 10, 2, 21] WRONG!
numbers.sort((a, b) => a - b);    // [1, 2, 10, 21] Correct!
numbers.sort((a, b) => b - a);    // [21, 10, 2, 1] Descending

// Reverse
let arr = [1, 2, 3];
arr.reverse(); // [3, 2, 1]
```

### Watch It!
⚠️ **`sort()` without a compare function sorts as strings!** `[10, 1, 21, 2].sort()` gives `[1, 10, 2, 21]` because '10' < '2' alphabetically. Always provide a compare function for numbers.

### Slicing and Combining

```javascript
let arr = [1, 2, 3, 4, 5];

// slice - extract portion (non-destructive)
arr.slice(1, 3);    // [2, 3] (index 1 to 2)
arr.slice(2);       // [3, 4, 5] (index 2 to end)
arr.slice(-2);      // [4, 5] (last 2)

// concat - combine arrays
let a = [1, 2];
let b = [3, 4];
let combined = a.concat(b); // [1, 2, 3, 4]

// Spread operator (modern way)
let combined2 = [...a, ...b]; // [1, 2, 3, 4]
let copy = [...arr]; // Shallow copy
```

### Destructuring Arrays

```javascript
let colors = ['red', 'green', 'blue'];

// Basic destructuring
let [first, second, third] = colors;
// first = 'red', second = 'green', third = 'blue'

// Skip elements
let [, , last] = colors; // last = 'blue'

// Rest pattern
let [head, ...rest] = colors;
// head = 'red', rest = ['green', 'blue']

// Default values
let [a = 1, b = 2, c = 3] = [10];
// a = 10, b = 2, c = 3

// Swap variables
let x = 1, y = 2;
[x, y] = [y, x]; // x = 2, y = 1
```

### Brain Power
🧠 What's the difference between `slice` and `splice`?

**Answer:**
- `slice(start, end)` extracts a portion WITHOUT modifying the original array
- `splice(start, deleteCount, ...items)` MODIFIES the original array (removes/inserts)

### Complete Arrays Example

```javascript
// Student grade tracker
const students = [
    { name: 'Alice', grade: 92 },
    { name: 'Bob', grade: 78 },
    { name: 'Charlie', grade: 95 },
    { name: 'Diana', grade: 88 },
    { name: 'Eve', grade: 72 }
];

// Get names of students with A grades (90+)
const honorRoll = students
    .filter(s => s.grade >= 90)
    .map(s => s.name);
// ['Alice', 'Charlie']

// Calculate class average
const average = students.reduce((sum, s) => sum + s.grade, 0) / students.length;
// 85

// Sort by grade (highest first)
const ranked = [...students].sort((a, b) => b.grade - a.grade);
// Charlie, Alice, Diana, Bob, Eve

// Check if everyone passed (grade >= 60)
const allPassed = students.every(s => s.grade >= 60); // true

// Find first failing student
const failing = students.find(s => s.grade < 60); // undefined
```

### There are NO Dumb Questions

**Q: Do `sort`, `splice`, and `reverse` modify the original array?**
**A:** Yes! They are "mutating" methods. Use `[...arr].sort()` or `arr.slice().sort()` if you want to keep the original unchanged.

**Q: What's the difference between `find` and `filter`?**
**A:** `find` returns the FIRST matching element (or undefined). `filter` returns ALL matching elements as a new array.

**Q: How do I remove duplicates from an array?**
**A:** Use a Set! `[...new Set(arr)]` gives you unique values.

---

## 9. Objects: Key-Value Pairs

### What are objects?

Objects store data as key-value pairs. Like a dictionary or phone book - you look up a key and get a value.

```javascript
let person = {
    name: 'Alice',
    age: 25,
    isStudent: true,
    hobbies: ['reading', 'coding']
};
```

### Creating Objects

```javascript
// Object literal (most common)
let car = {
    make: 'Toyota',
    model: 'Camry',
    year: 2023
};

// Object constructor (rarely used)
let obj = new Object();
obj.name = 'Alice';

// Object.create (set prototype)
let proto = { greet() { return 'Hello'; } };
let child = Object.create(proto);

// From entries
let map = Object.fromEntries([['a', 1], ['b', 2]]);
// { a: 1, b: 2 }
```

### Accessing Properties

```javascript
let person = { name: 'Alice', age: 25, 'favorite color': 'blue' };

// Dot notation (preferred)
person.name;          // 'Alice'
person.age;           // 25

// Bracket notation (required for special keys)
person['name'];             // 'Alice'
person['favorite color'];   // 'blue'

// Dynamic keys
let key = 'age';
person[key];          // 25

// Optional chaining
let user = {};
user?.address?.city;  // undefined (no error)
```

### Modifying Objects

```javascript
let person = { name: 'Alice', age: 25 };

// Add properties
person.city = 'NYC';
person['phone'] = '555-0123';

// Update properties
person.age = 26;

// Delete properties
delete person.phone;

// Check if property exists
'name' in person;              // true
person.hasOwnProperty('age');  // true
```

### Object Methods

```javascript
let calculator = {
    value: 0,

    add(n) {
        this.value += n;
        return this; // Enable chaining
    },

    subtract(n) {
        this.value -= n;
        return this;
    },

    result() {
        return this.value;
    }
};

calculator.add(10).subtract(3).result(); // 7
```

### Object Destructuring

```javascript
let person = { name: 'Alice', age: 25, city: 'NYC' };

// Basic destructuring
let { name, age } = person;
// name = 'Alice', age = 25

// Rename variables
let { name: firstName, age: years } = person;
// firstName = 'Alice', years = 25

// Default values
let { name, country = 'US' } = person;
// country = 'US' (not in object)

// Rest pattern
let { name, ...rest } = person;
// rest = { age: 25, city: 'NYC' }

// Nested destructuring
let user = { address: { city: 'NYC', zip: '10001' } };
let { address: { city, zip } } = user;
// city = 'NYC', zip = '10001'
```

### Spread Operator with Objects

```javascript
let defaults = { color: 'red', size: 'medium', speed: 'fast' };
let custom = { color: 'blue', weight: 'heavy' };

// Merge objects (later properties win)
let merged = { ...defaults, ...custom };
// { color: 'blue', size: 'medium', speed: 'fast', weight: 'heavy' }

// Shallow copy
let copy = { ...defaults };

// Add properties
let extended = { ...defaults, newProp: 'value' };
```

### Useful Object Methods

```javascript
let person = { name: 'Alice', age: 25, city: 'NYC' };

// Get keys, values, entries
Object.keys(person);    // ['name', 'age', 'city']
Object.values(person);  // ['Alice', 25, 'NYC']
Object.entries(person); // [['name','Alice'], ['age',25], ['city','NYC']]

// Freeze (make immutable)
let frozen = Object.freeze({ x: 1, y: 2 });
frozen.x = 10; // Silently fails (or error in strict mode)

// Assign (copy properties)
let target = { a: 1 };
Object.assign(target, { b: 2, c: 3 });
// target = { a: 1, b: 2, c: 3 }
```

### Computed Property Names

```javascript
let key = 'name';
let obj = {
    [key]: 'Alice',           // name: 'Alice'
    [`${key}Upper`]: 'ALICE'  // nameUpper: 'ALICE'
};

// Useful for dynamic objects
function createPair(key, value) {
    return { [key]: value };
}
createPair('color', 'blue'); // { color: 'blue' }
```

### Watch It!
⚠️ **Objects are passed by reference!** Assigning an object to a new variable doesn't copy it - both variables point to the same object. Use spread (`{...obj}`) for shallow copies.

```javascript
let original = { name: 'Alice' };
let reference = original;
reference.name = 'Bob';
console.log(original.name); // 'Bob' (both changed!)

let copy = { ...original };
copy.name = 'Charlie';
console.log(original.name); // 'Bob' (original unchanged)
```

### Brain Power
🧠 What's the difference between shallow copy and deep copy?

**Answer:**
- **Shallow copy** (`{...obj}`) copies top-level properties. Nested objects are still references!
- **Deep copy** (`structuredClone(obj)`) copies everything recursively.
```javascript
let obj = { a: 1, nested: { b: 2 } };
let shallow = { ...obj };
shallow.nested.b = 99;
console.log(obj.nested.b); // 99 (nested still shared!)

let deep = structuredClone(obj);
deep.nested.b = 42;
console.log(obj.nested.b); // 99 (truly independent)
```

### Complete Objects Example

```javascript
// Shopping cart system
const cart = {
    items: [],

    addItem(name, price, quantity = 1) {
        const existing = this.items.find(item => item.name === name);
        if (existing) {
            existing.quantity += quantity;
        } else {
            this.items.push({ name, price, quantity });
        }
        return this;
    },

    removeItem(name) {
        this.items = this.items.filter(item => item.name !== name);
        return this;
    },

    get total() {
        return this.items.reduce(
            (sum, item) => sum + item.price * item.quantity, 0
        );
    },

    get summary() {
        return {
            itemCount: this.items.length,
            total: this.total,
            items: this.items.map(({ name, quantity }) => `${name} x${quantity}`)
        };
    }
};

cart.addItem('Shirt', 25, 2)
    .addItem('Pants', 40)
    .addItem('Shirt', 25, 1); // Adds to existing

console.log(cart.summary);
// { itemCount: 2, total: 115, items: ['Shirt x3', 'Pants x1'] }
```

### There are NO Dumb Questions

**Q: When should I use dot notation vs bracket notation?**
**A:** Use dot notation by default. Use brackets when: the key is dynamic (a variable), contains special characters, or is a number.

**Q: What's the difference between `Object.freeze` and `const`?**
**A:** `const` prevents reassignment of the variable. `Object.freeze` prevents modification of the object's properties. They do different things!

**Q: How do I iterate over an object?**
**A:** Use `Object.keys()`, `Object.values()`, `Object.entries()` with `forEach` or `for...of`. Or use `for...in` (but check `hasOwnProperty`).

---

## 10. The 'this' Keyword: Context Matters

### What is 'this'?

`this` refers to the object that is executing the current function. Its value depends on HOW the function is called, not where it's defined.

```javascript
const person = {
    name: 'Alice',
    greet() {
        console.log(`Hi, I'm ${this.name}`);
    }
};

person.greet(); // "Hi, I'm Alice" (this = person)
```

### 'this' in Different Contexts

#### Global context

```javascript
// In browser
console.log(this); // window object

// In Node.js
console.log(this); // {} (module scope)
```

#### Object method

```javascript
const user = {
    name: 'Alice',
    sayName() {
        console.log(this.name); // 'Alice'
    }
};

user.sayName(); // this = user
```

#### Regular function

```javascript
function showThis() {
    console.log(this);
}

showThis(); // window (non-strict) or undefined (strict mode)
```

#### Arrow function (no own 'this')

```javascript
const user = {
    name: 'Alice',
    greet: () => {
        console.log(this.name); // undefined! Arrow uses outer 'this'
    },
    delayedGreet() {
        setTimeout(() => {
            console.log(this.name); // 'Alice'! Arrow inherits 'this' from delayedGreet
        }, 1000);
    }
};
```

### Watch It!
⚠️ **Arrow functions don't have their own `this`!** They inherit `this` from the enclosing scope. This is great for callbacks inside methods, but terrible for object methods themselves.

```javascript
// BAD: Arrow function as method
const obj = {
    value: 42,
    getValue: () => this.value // undefined! 'this' is outer scope
};

// GOOD: Regular function as method
const obj2 = {
    value: 42,
    getValue() { return this.value; } // 42
};
```

### The 'this' Problem: Lost Context

```javascript
const user = {
    name: 'Alice',
    greet() {
        console.log(`Hi, I'm ${this.name}`);
    }
};

user.greet(); // "Hi, I'm Alice"

// Extracting the method loses 'this'!
const greetFn = user.greet;
greetFn(); // "Hi, I'm undefined" (this = window/undefined)

// Passing as callback loses 'this'!
setTimeout(user.greet, 1000); // "Hi, I'm undefined"
```

### Fixing 'this': bind, call, apply

```javascript
const user = {
    name: 'Alice',
    greet(greeting) {
        console.log(`${greeting}, I'm ${this.name}`);
    }
};

// bind - creates new function with fixed 'this'
const boundGreet = user.greet.bind(user);
boundGreet('Hey'); // "Hey, I'm Alice"

// call - invokes function with specified 'this'
user.greet.call({ name: 'Bob' }, 'Hello'); // "Hello, I'm Bob"

// apply - like call, but args as array
user.greet.apply({ name: 'Charlie' }, ['Hi']); // "Hi, I'm Charlie"
```

### Brain Power
🧠 When should you use arrow functions vs regular functions?

**Answer:**
- **Arrow functions:** For callbacks, array methods, closures inside methods (they inherit `this`)
- **Regular functions:** For object methods, constructors, when you need your own `this`

### 'this' in Classes

```javascript
class Timer {
    constructor() {
        this.seconds = 0;
    }

    start() {
        // Arrow function inherits 'this' from start()
        setInterval(() => {
            this.seconds++;
            console.log(this.seconds);
        }, 1000);
    }
}

const timer = new Timer();
timer.start(); // 1, 2, 3, ...
```

### Complete 'this' Example

```javascript
class EventEmitter {
    constructor() {
        this.events = {};
    }

    on(event, callback) {
        if (!this.events[event]) {
            this.events[event] = [];
        }
        this.events[event].push(callback);
        return this; // Chaining
    }

    emit(event, ...args) {
        const callbacks = this.events[event] || [];
        callbacks.forEach(cb => cb(...args));
        return this;
    }
}

const emitter = new EventEmitter();

emitter
    .on('greet', name => console.log(`Hello, ${name}!`))
    .on('greet', name => console.log(`Welcome, ${name}!`));

emitter.emit('greet', 'Alice');
// "Hello, Alice!"
// "Welcome, Alice!"
```

### There are NO Dumb Questions

**Q: Why is 'this' so confusing in JavaScript?**
**A:** Because `this` is determined by how a function is CALLED, not where it's defined. Other languages bind `this` at definition time. JavaScript's approach is flexible but surprising.

**Q: Should I avoid 'this' entirely?**
**A:** No! `this` is essential for classes and object methods. Just understand the rules: method call → object, arrow → inherited, regular function → window/undefined.

**Q: What about 'this' in event handlers?**
**A:** In DOM event handlers, `this` refers to the element that triggered the event. But arrow functions in event handlers inherit `this` from the outer scope instead.

---

## 11. Asynchronous JavaScript: Dealing with Time

### The Problem: JavaScript is single-threaded

JavaScript can only execute one piece of code at a time. Without async, fetching data from a server would freeze the entire page until the response arrives.

```javascript
// Synchronous (blocking)
console.log('1');
console.log('2');
console.log('3');
// Output: 1, 2, 3 (in order, immediately)

// Asynchronous (non-blocking)
console.log('1');
setTimeout(() => console.log('2'), 1000);
console.log('3');
// Output: 1, 3, 2 (2 comes last, after 1 second!)
```

### The Event Loop: How async works

```javascript
// JavaScript has a call stack, a task queue, and an event loop

// 1. Synchronous code runs on the call stack
// 2. Async operations (timers, network) go to Web APIs
// 3. When done, callbacks are placed in the task queue
// 4. Event loop moves queue tasks to stack when stack is empty

console.log('Start');           // 1. Runs immediately

setTimeout(() => {
    console.log('Timeout');     // 4. Runs after stack is empty
}, 0);                          // Even with 0ms delay!

console.log('End');             // 2. Runs immediately

// Output: Start, End, Timeout
```

### Brain Power
🧠 Why does `setTimeout(fn, 0)` not run immediately?

**Answer:** Even with 0ms delay, the callback goes to the task queue and waits for the call stack to be empty. The event loop won't process it until all synchronous code finishes!

### setTimeout and setInterval

```javascript
// setTimeout - run once after delay
const timeoutId = setTimeout(() => {
    console.log('Runs after 2 seconds');
}, 2000);

// Cancel timeout
clearTimeout(timeoutId);

// setInterval - run repeatedly
const intervalId = setInterval(() => {
    console.log('Runs every second');
}, 1000);

// Cancel interval
clearInterval(intervalId);

// Common pattern: self-clearing interval
let count = 0;
const id = setInterval(() => {
    count++;
    console.log(count);
    if (count >= 5) {
        clearInterval(id); // Stop after 5
    }
}, 1000);
```

### Callbacks: Passing functions as arguments

```javascript
// A callback is a function passed to another function
function fetchData(callback) {
    setTimeout(() => {
        const data = { name: 'Alice', age: 25 };
        callback(data);
    }, 1000);
}

fetchData(function(data) {
    console.log(data); // { name: 'Alice', age: 25 }
});

// Error-first callbacks (Node.js convention)
function readFile(path, callback) {
    setTimeout(() => {
        if (path === '') {
            callback(new Error('Path is empty'), null);
        } else {
            callback(null, 'file contents');
        }
    }, 100);
}

readFile('data.txt', (error, data) => {
    if (error) {
        console.error(error.message);
    } else {
        console.log(data);
    }
});
```

### Callback Hell: The problem with callbacks

```javascript
// Nested callbacks become unreadable
getUser(userId, function(user) {
    getOrders(user.id, function(orders) {
        getOrderDetails(orders[0].id, function(details) {
            getShipping(details.shippingId, function(shipping) {
                console.log(shipping);
                // Welcome to the pyramid of doom!
            });
        });
    });
});
```

### Watch It!
⚠️ **Callback hell is a code smell!** If you have more than 2 levels of nested callbacks, refactor to Promises or async/await (covered in the next section).

### Complete Async Basics Example

```javascript
// Simulating async operations with callbacks
function simulateAPI(endpoint, callback) {
    const delay = Math.random() * 2000;
    setTimeout(() => {
        const data = { endpoint, timestamp: Date.now() };
        callback(null, data);
    }, delay);
}

// Sequential requests (slow!)
simulateAPI('/users', (err, users) => {
    console.log('Got users:', users);
    simulateAPI('/posts', (err, posts) => {
        console.log('Got posts:', posts);
        simulateAPI('/comments', (err, comments) => {
            console.log('Got comments:', comments);
            console.log('All done!');
        });
    });
});
```

### There are NO Dumb Questions

**Q: Is JavaScript really single-threaded?**
**A:** Yes! JavaScript itself runs on one thread. But the browser/Node.js provides Web APIs (timers, network, file I/O) that run on separate threads. The results come back through the event loop.

**Q: What's the difference between microtasks and macrotasks?**
**A:** Promises use the microtask queue (higher priority). setTimeout/setInterval use the macrotask queue. Microtasks run before the next macrotask.

**Q: Can I make synchronous code from asynchronous code?**
**A:** Not directly. You can use `async/await` to WRITE it like synchronous code, but it's still asynchronous under the hood.

---

## 12. Promises and Async/Await: Better Async

### What is a Promise?

A Promise is an object representing the eventual completion (or failure) of an asynchronous operation. It's like an IOU - "I promise to give you a value later."

```javascript
// A promise has three states:
// 1. Pending - operation not yet complete
// 2. Fulfilled (resolved) - operation succeeded
// 3. Rejected - operation failed
```

### Creating Promises

```javascript
// Basic promise
const promise = new Promise((resolve, reject) => {
    const success = true;

    if (success) {
        resolve('Operation succeeded!');
    } else {
        reject(new Error('Operation failed!'));
    }
});

// Promise that simulates network request
function fetchUser(id) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (id > 0) {
                resolve({ id, name: 'Alice' });
            } else {
                reject(new Error('Invalid ID'));
            }
        }, 1000);
    });
}
```

### Consuming Promises: then, catch, finally

```javascript
fetchUser(1)
    .then(user => {
        console.log(user); // { id: 1, name: 'Alice' }
        return user.name;
    })
    .then(name => {
        console.log(name); // 'Alice'
    })
    .catch(error => {
        console.error(error.message);
    })
    .finally(() => {
        console.log('Done!'); // Always runs
    });
```

### Promise Chaining

```javascript
// Each .then returns a new promise
function getUser(id) {
    return fetch(`/api/users/${id}`)
        .then(response => response.json());
}

function getUserPosts(user) {
    return fetch(`/api/users/${user.id}/posts`)
        .then(response => response.json());
}

function getPostComments(post) {
    return fetch(`/api/posts/${post.id}/comments`)
        .then(response => response.json());
}

// Flat chain instead of nested callbacks!
getUser(1)
    .then(user => getUserPosts(user))
    .then(posts => getPostComments(posts[0]))
    .then(comments => console.log(comments))
    .catch(error => console.error(error));
```

### Watch It!
⚠️ **Always return in `.then()` callbacks!** If you forget `return`, the next `.then()` receives `undefined` instead of your value.

```javascript
// BAD
fetch(url)
    .then(response => { response.json(); }) // Missing return!
    .then(data => console.log(data)); // undefined

// GOOD
fetch(url)
    .then(response => response.json()) // Implicit return
    .then(data => console.log(data)); // Actual data
```

### Promise Static Methods

```javascript
// Promise.all - wait for ALL to resolve (fails fast)
const p1 = fetch('/api/users');
const p2 = fetch('/api/posts');
const p3 = fetch('/api/comments');

Promise.all([p1, p2, p3])
    .then(([users, posts, comments]) => {
        console.log('All loaded!');
    })
    .catch(error => {
        console.error('One failed:', error); // If ANY fails
    });

// Promise.allSettled - wait for ALL to complete (never fails)
Promise.allSettled([p1, p2, p3])
    .then(results => {
        results.forEach(result => {
            if (result.status === 'fulfilled') {
                console.log(result.value);
            } else {
                console.error(result.reason);
            }
        });
    });

// Promise.race - first to settle wins
Promise.race([p1, p2, p3])
    .then(winner => console.log('First done:', winner));

// Promise.any - first to RESOLVE wins (ES2021)
Promise.any([p1, p2, p3])
    .then(winner => console.log('First success:', winner))
    .catch(error => console.log('All failed'));
```

### async/await: Syntactic sugar for Promises

```javascript
// async function always returns a Promise
async function fetchData() {
    // await pauses execution until promise resolves
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    return data; // Wrapped in Promise.resolve()
}

// Equivalent to:
function fetchData() {
    return fetch('https://api.example.com/data')
        .then(response => response.json());
}
```

### Error Handling with async/await

```javascript
// try/catch (recommended)
async function fetchUser(id) {
    try {
        const response = await fetch(`/api/users/${id}`);
        if (!response.ok) {
            throw new Error(`HTTP ${response.status}`);
        }
        const user = await response.json();
        return user;
    } catch (error) {
        console.error('Failed to fetch user:', error.message);
        return null; // Graceful fallback
    }
}

// Multiple await with error handling
async function loadDashboard() {
    try {
        const user = await fetchUser(1);
        const posts = await fetchPosts(user.id);
        const notifications = await fetchNotifications(user.id);
        return { user, posts, notifications };
    } catch (error) {
        console.error('Dashboard load failed:', error);
        throw error; // Re-throw to caller
    }
}
```

### Parallel async/await

```javascript
// SEQUENTIAL (slow!) - each waits for the previous
async function loadSequential() {
    const users = await fetch('/api/users');      // Wait...
    const posts = await fetch('/api/posts');      // Then wait...
    const comments = await fetch('/api/comments'); // Then wait...
    return { users, posts, comments };
}

// PARALLEL (fast!) - all start at once
async function loadParallel() {
    const [users, posts, comments] = await Promise.all([
        fetch('/api/users'),
        fetch('/api/posts'),
        fetch('/api/comments')
    ]);
    return { users, posts, comments };
}
```

### Brain Power
🧠 When should you use sequential vs parallel async operations?

**Answer:**
- **Sequential:** When each operation depends on the previous result (get user, then get user's posts)
- **Parallel:** When operations are independent (get users, posts, and comments simultaneously)

### Complete Promises/Async Example

```javascript
// Real-world API wrapper with retry logic
async function fetchWithRetry(url, options = {}, maxRetries = 3) {
    for (let attempt = 1; attempt <= maxRetries; attempt++) {
        try {
            const response = await fetch(url, options);

            if (!response.ok) {
                throw new Error(`HTTP ${response.status}`);
            }

            return await response.json();
        } catch (error) {
            console.warn(`Attempt ${attempt} failed:`, error.message);

            if (attempt === maxRetries) {
                throw new Error(`Failed after ${maxRetries} attempts: ${error.message}`);
            }

            // Wait before retrying (exponential backoff)
            await new Promise(resolve =>
                setTimeout(resolve, 1000 * Math.pow(2, attempt - 1))
            );
        }
    }
}

// Usage
async function loadUserProfile(userId) {
    try {
        const [user, posts, followers] = await Promise.all([
            fetchWithRetry(`/api/users/${userId}`),
            fetchWithRetry(`/api/users/${userId}/posts`),
            fetchWithRetry(`/api/users/${userId}/followers`)
        ]);

        return {
            ...user,
            postCount: posts.length,
            followerCount: followers.length,
            recentPosts: posts.slice(0, 5)
        };
    } catch (error) {
        console.error('Failed to load profile:', error.message);
        return null;
    }
}
```

### There are NO Dumb Questions

**Q: Can I use await outside an async function?**
**A:** Yes! Top-level await works in ES modules. In regular scripts, wrap it in an async IIFE: `(async () => { await ... })()`.

**Q: What's the difference between Promise.all and Promise.allSettled?**
**A:** `Promise.all` rejects immediately if ANY promise fails. `Promise.allSettled` waits for ALL to complete, regardless of success or failure.

**Q: Should I use .then() or async/await?**
**A:** Prefer async/await for readability. Use `.then()` for simple one-liners or when you don't need to store intermediate results.

---

## 13. Classes: Object-Oriented JavaScript

### What are classes?

Classes are blueprints for creating objects. They encapsulate data (properties) and behavior (methods) together. JavaScript classes are syntactic sugar over prototypal inheritance.

```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }

    greet() {
        return `Hi, I'm ${this.name}`;
    }
}

const alice = new Person('Alice', 25);
console.log(alice.greet()); // "Hi, I'm Alice"
```

### Class Syntax

```javascript
class Animal {
    // Constructor - called when creating new instance
    constructor(name, sound) {
        this.name = name;
        this.sound = sound;
    }

    // Method
    speak() {
        return `${this.name} says ${this.sound}!`;
    }

    // Getter
    get info() {
        return `${this.name} (${this.sound})`;
    }

    // Setter
    set nickname(value) {
        this._nickname = value;
    }

    // Static method (called on class, not instance)
    static create(name, sound) {
        return new Animal(name, sound);
    }
}

const dog = new Animal('Rex', 'Woof');
dog.speak();         // "Rex says Woof!"
dog.info;            // "Rex (Woof)"
dog.nickname = 'Buddy';

const cat = Animal.create('Whiskers', 'Meow');
```

### Inheritance: extends and super

```javascript
class Animal {
    constructor(name) {
        this.name = name;
    }

    speak() {
        return `${this.name} makes a noise.`;
    }
}

class Dog extends Animal {
    constructor(name, breed) {
        super(name); // Call parent constructor
        this.breed = breed;
    }

    // Override parent method
    speak() {
        return `${this.name} barks!`;
    }

    // New method
    fetch(item) {
        return `${this.name} fetches the ${item}!`;
    }
}

const rex = new Dog('Rex', 'German Shepherd');
rex.speak();           // "Rex barks!"
rex.fetch('ball');     // "Rex fetches the ball!"
rex instanceof Dog;    // true
rex instanceof Animal; // true
```

### Watch It!
⚠️ **Always call `super()` first in child constructors!** You can't use `this` before calling `super()`. JavaScript enforces this to ensure the parent is properly initialized.

### Private Fields and Methods (ES2022)

```javascript
class BankAccount {
    #balance = 0; // Private field

    constructor(owner, initialBalance) {
        this.owner = owner;
        this.#balance = initialBalance;
    }

    // Private method
    #validateAmount(amount) {
        if (amount <= 0) throw new Error('Amount must be positive');
        return true;
    }

    deposit(amount) {
        this.#validateAmount(amount);
        this.#balance += amount;
        return this;
    }

    withdraw(amount) {
        this.#validateAmount(amount);
        if (amount > this.#balance) {
            throw new Error('Insufficient funds');
        }
        this.#balance -= amount;
        return this;
    }

    get balance() {
        return this.#balance;
    }
}

const account = new BankAccount('Alice', 1000);
account.deposit(500).withdraw(200);
console.log(account.balance);   // 1300
// console.log(account.#balance); // SyntaxError!
```

### Static Properties and Methods

```javascript
class MathUtils {
    static PI = 3.14159;

    static add(a, b) {
        return a + b;
    }

    static random(min, max) {
        return Math.floor(Math.random() * (max - min + 1)) + min;
    }
}

// Called on the class itself, not instances
MathUtils.add(2, 3);       // 5
MathUtils.random(1, 10);   // Random 1-10
MathUtils.PI;              // 3.14159
```

### Brain Power
🧠 What's the difference between class syntax and constructor functions?

**Answer:** They do the same thing! Classes are syntactic sugar over prototypal inheritance. But classes are cleaner, have `extends`/`super`, support private fields, and enforce `new` (can't call a class without `new`).

### Complete Classes Example

```javascript
class TodoList {
    #items = [];
    #nextId = 1;

    add(text) {
        this.#items.push({
            id: this.#nextId++,
            text,
            completed: false,
            createdAt: new Date()
        });
        return this;
    }

    toggle(id) {
        const item = this.#items.find(i => i.id === id);
        if (item) item.completed = !item.completed;
        return this;
    }

    remove(id) {
        this.#items = this.#items.filter(i => i.id !== id);
        return this;
    }

    get pending() {
        return this.#items.filter(i => !i.completed);
    }

    get completed() {
        return this.#items.filter(i => i.completed);
    }

    get stats() {
        return {
            total: this.#items.length,
            pending: this.pending.length,
            completed: this.completed.length
        };
    }
}

const todos = new TodoList();
todos.add('Learn JavaScript')
     .add('Build a project')
     .add('Get a job');

todos.toggle(1); // Complete "Learn JavaScript"
console.log(todos.stats); // { total: 3, pending: 2, completed: 1 }
```

### There are NO Dumb Questions

**Q: Should I use classes or plain objects?**
**A:** Use classes when you need multiple instances with shared behavior, inheritance, or encapsulation. Use plain objects for simple data containers or one-off configurations.

**Q: What does `new` actually do?**
**A:** `new` creates a fresh object, sets its prototype to the class's prototype, runs the constructor with `this` pointing to the new object, and returns the object.

**Q: Are JavaScript classes the same as Java/C# classes?**
**A:** Similar syntax, but different underneath. JavaScript uses prototypal inheritance (objects inherit from objects), not classical inheritance (classes inherit from classes).

---

## 14. Modules: Organizing Code

### Why modules?

Without modules, all JavaScript shares a global scope. Modules let you split code into separate files, each with its own scope, and explicitly share what's needed.

```javascript
// Without modules (old way) - everything is global!
// <script src="utils.js"></script>
// <script src="app.js"></script>
// Variables from utils.js can clash with app.js!

// With modules - explicit imports/exports
// Each file is its own scope
```

### Export: Sharing code

```javascript
// math.js

// Named exports (multiple per file)
export const PI = 3.14159;

export function add(a, b) {
    return a + b;
}

export function subtract(a, b) {
    return a - b;
}

// Export at the bottom (alternative)
const multiply = (a, b) => a * b;
const divide = (a, b) => a / b;

export { multiply, divide };
```

### Default Export: One per file

```javascript
// User.js

// Default export (one per file)
export default class User {
    constructor(name) {
        this.name = name;
    }

    greet() {
        return `Hi, I'm ${this.name}`;
    }
}

// Alternative: export at bottom
// class User { ... }
// export default User;
```

### Import: Using shared code

```javascript
// app.js

// Import named exports (use curly braces)
import { add, subtract, PI } from './math.js';

console.log(add(2, 3));  // 5
console.log(PI);          // 3.14159

// Import default export (no curly braces, any name)
import User from './User.js';

const alice = new User('Alice');

// Import all as namespace
import * as MathUtils from './math.js';

MathUtils.add(2, 3);     // 5
MathUtils.PI;             // 3.14159

// Rename imports
import { add as sum, subtract as minus } from './math.js';
sum(2, 3); // 5
```

### Watch It!
⚠️ **Named exports use curly braces, default exports don't!** Mixing them up is a common bug.

```javascript
// Named export → named import
export function add() { }
import { add } from './math.js'; // Correct
// import add from './math.js';  // WRONG! Gets undefined

// Default export → default import
export default function add() { }
import add from './math.js';     // Correct (any name works)
// import { add } from './math.js'; // WRONG! Named import for default
```

### Combining Default and Named

```javascript
// api.js
export default class API {
    // ...
}

export const BASE_URL = 'https://api.example.com';
export function formatURL(path) {
    return `${BASE_URL}${path}`;
}

// Importing both
import API, { BASE_URL, formatURL } from './api.js';
```

### Re-exports: Barrel files

```javascript
// components/index.js (barrel file)
export { default as Button } from './Button.js';
export { default as Input } from './Input.js';
export { default as Modal } from './Modal.js';

// Now import from one place
import { Button, Input, Modal } from './components/index.js';
```

### Dynamic Imports: Load on demand

```javascript
// Static import (top of file, always loaded)
import { heavyFunction } from './heavy-module.js';

// Dynamic import (loaded when needed)
async function loadFeature() {
    const module = await import('./heavy-module.js');
    module.heavyFunction();
}

// Conditional loading
if (userWantsChart) {
    const { Chart } = await import('./chart-library.js');
    new Chart(data);
}
```

### Brain Power
🧠 When should you use default exports vs named exports?

**Answer:**
- **Default export:** When a module has one primary thing to export (a class, a component, a main function)
- **Named exports:** When a module has multiple related utilities, constants, or functions
- Many style guides prefer named exports because they enforce consistent naming and enable better auto-imports

### Module Patterns

```javascript
// Pattern 1: Utility module (all named exports)
// utils.js
export function formatDate(date) { /* ... */ }
export function formatCurrency(amount) { /* ... */ }
export function capitalize(str) { /* ... */ }

// Pattern 2: Class module (default + named)
// UserService.js
export default class UserService { /* ... */ }
export const USER_ROLES = ['admin', 'user', 'guest'];

// Pattern 3: Constants module
// config.js
export const API_URL = 'https://api.example.com';
export const MAX_RETRIES = 3;
export const TIMEOUT = 5000;
```

### Using Modules in HTML

```html
<!-- type="module" enables ES modules in the browser -->
<script type="module" src="app.js"></script>

<!-- Modules are automatically deferred (load after HTML) -->
<!-- Modules have strict mode by default -->
<!-- Each module has its own scope (no global pollution) -->
```

### Complete Modules Example

```javascript
// --- logger.js ---
const LOG_LEVELS = { DEBUG: 0, INFO: 1, WARN: 2, ERROR: 3 };

export class Logger {
    #level;
    #prefix;

    constructor(prefix, level = 'INFO') {
        this.#prefix = prefix;
        this.#level = LOG_LEVELS[level];
    }

    #shouldLog(level) {
        return LOG_LEVELS[level] >= this.#level;
    }

    #format(level, message) {
        const time = new Date().toISOString();
        return `[${time}] [${level}] [${this.#prefix}] ${message}`;
    }

    debug(msg) { if (this.#shouldLog('DEBUG')) console.log(this.#format('DEBUG', msg)); }
    info(msg)  { if (this.#shouldLog('INFO'))  console.log(this.#format('INFO', msg)); }
    warn(msg)  { if (this.#shouldLog('WARN'))  console.warn(this.#format('WARN', msg)); }
    error(msg) { if (this.#shouldLog('ERROR')) console.error(this.#format('ERROR', msg)); }
}

export default new Logger('App');


// --- validators.js ---
export const required = value => value !== null && value !== undefined && value !== '';
export const minLength = min => value => value.length >= min;
export const maxLength = max => value => value.length <= max;
export const matches = pattern => value => pattern.test(value);
export const isEmail = matches(/^[^\s@]+@[^\s@]+\.[^\s@]+$/);

export function validate(value, ...rules) {
    return rules.every(rule => rule(value));
}


// --- userService.js ---
import logger, { Logger } from './logger.js';
import { validate, required, minLength, isEmail } from './validators.js';

export async function createUser(data) {
    const { name, email, password } = data;

    if (!validate(name, required, minLength(2))) {
        throw new Error('Invalid name');
    }
    if (!validate(email, required, isEmail)) {
        throw new Error('Invalid email');
    }
    if (!validate(password, required, minLength(8))) {
        throw new Error('Invalid password');
    }

    logger.info(`Creating user: ${email}`);
    const response = await fetch('/api/users', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ name, email, password })
    });

    if (!response.ok) {
        logger.error(`Failed to create user: HTTP ${response.status}`);
        throw new Error('User creation failed');
    }

    logger.info(`User created: ${email}`);
    return response.json();
}


// --- app.js (entry point) ---
import { createUser } from './userService.js';

document.querySelector('#signup-form').addEventListener('submit', async (e) => {
    e.preventDefault();
    const form = new FormData(e.target);

    try {
        const user = await createUser({
            name: form.get('name'),
            email: form.get('email'),
            password: form.get('password')
        });
        console.log('Welcome!', user);
    } catch (error) {
        console.error(error.message);
    }
});
```

### There are NO Dumb Questions

**Q: What's the difference between ES modules and CommonJS?**
**A:** ES modules use `import`/`export` (standard, static, browser + Node.js). CommonJS uses `require`/`module.exports` (Node.js only, dynamic). Modern code should use ES modules.

**Q: Do I need a bundler (Webpack, Vite) for modules?**
**A:** Browsers support ES modules natively. But bundlers add benefits: bundling many files into fewer requests, tree-shaking unused code, and supporting older browsers.

**Q: What is tree-shaking?**
**A:** Removing unused exports from the final bundle. Named exports enable better tree-shaking because bundlers can see exactly what's used.

---

## 15. DOM and APIs: Interacting with the Web

### What is the DOM?

The DOM (Document Object Model) is a tree representation of your HTML. JavaScript uses the DOM to read, modify, add, and remove page elements.

```javascript
// The DOM tree:
// document
//   └── html
//       ├── head
//       │   └── title
//       └── body
//           ├── h1
//           ├── p
//           └── div
//               └── button
```

### Selecting Elements

```javascript
// By ID (returns one element)
const header = document.getElementById('header');

// By class (returns HTMLCollection)
const items = document.getElementsByClassName('item');

// By tag (returns HTMLCollection)
const paragraphs = document.getElementsByTagName('p');

// CSS selectors (modern, preferred!)
const first = document.querySelector('.item');        // First match
const all = document.querySelectorAll('.item');       // All matches
const nested = document.querySelector('#nav > .link'); // Complex selector
```

### Watch It!
⚠️ **`querySelectorAll` returns a NodeList, not an Array!** Use `Array.from(nodeList)` or `[...nodeList]` to use array methods like `map` and `filter`.

### Modifying Elements

```javascript
const el = document.querySelector('#myElement');

// Text content
el.textContent = 'New text';     // Sets text (safe, no HTML parsing)
el.innerHTML = '<b>Bold</b>';    // Sets HTML (careful with user input!)

// Attributes
el.setAttribute('class', 'active');
el.getAttribute('class');        // 'active'
el.removeAttribute('class');
el.id = 'newId';                 // Direct property access

// Classes
el.classList.add('active');
el.classList.remove('hidden');
el.classList.toggle('visible');
el.classList.contains('active'); // true

// Styles
el.style.color = 'red';
el.style.fontSize = '16px';
el.style.display = 'none';
```

### Creating and Removing Elements

```javascript
// Create element
const div = document.createElement('div');
div.textContent = 'Hello!';
div.classList.add('card');

// Add to page
document.body.appendChild(div);                    // Add at end
document.body.prepend(div);                        // Add at beginning
document.body.insertBefore(div, referenceElement); // Add before

// Modern insertion
const parent = document.querySelector('#list');
parent.append(div);                                // After last child
parent.prepend(div);                               // Before first child
referenceElement.after(div);                       // After reference
referenceElement.before(div);                      // Before reference

// Remove element
div.remove();                                      // Modern
parent.removeChild(div);                           // Old way

// Clone element
const clone = div.cloneNode(true); // true = deep clone (with children)
```

### Event Handling

```javascript
const button = document.querySelector('#myButton');

// addEventListener (preferred!)
button.addEventListener('click', function(event) {
    console.log('Clicked!', event.target);
});

// Arrow function
button.addEventListener('click', (e) => {
    e.preventDefault(); // Prevent default behavior
    console.log('Clicked!');
});

// Remove event listener (need named function)
function handleClick(e) {
    console.log('Clicked!');
}
button.addEventListener('click', handleClick);
button.removeEventListener('click', handleClick);

// Common events
// click, dblclick, mouseenter, mouseleave
// keydown, keyup, keypress
// submit, change, input, focus, blur
// load, DOMContentLoaded, scroll, resize
```

### Event Delegation

```javascript
// Instead of adding listeners to each item...
// Add ONE listener to the parent!
const list = document.querySelector('#todoList');

list.addEventListener('click', (e) => {
    // Check what was actually clicked
    if (e.target.matches('.delete-btn')) {
        e.target.closest('li').remove();
    }

    if (e.target.matches('.toggle-btn')) {
        e.target.closest('li').classList.toggle('completed');
    }
});

// Works for dynamically added items too!
```

### Brain Power
🧠 Why is event delegation better than adding listeners to each element?

**Answer:**
- **Performance:** One listener vs hundreds
- **Dynamic elements:** Works for elements added later
- **Memory:** Fewer event listeners = less memory usage

### Fetch API: Making HTTP requests

```javascript
// GET request
async function getUsers() {
    const response = await fetch('https://api.example.com/users');
    const users = await response.json();
    return users;
}

// POST request
async function createUser(userData) {
    const response = await fetch('https://api.example.com/users', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify(userData)
    });
    return response.json();
}

// PUT, PATCH, DELETE
async function updateUser(id, data) {
    const response = await fetch(`/api/users/${id}`, {
        method: 'PUT',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(data)
    });
    return response.json();
}

async function deleteUser(id) {
    await fetch(`/api/users/${id}`, { method: 'DELETE' });
}
```

### Watch It!
⚠️ **`fetch` doesn't throw on HTTP errors!** A 404 or 500 response still resolves the promise. Check `response.ok` or `response.status` manually.

```javascript
const response = await fetch('/api/data');
if (!response.ok) {
    throw new Error(`HTTP ${response.status}: ${response.statusText}`);
}
const data = await response.json();
```

### Local Storage: Persistent data

```javascript
// Store data (strings only!)
localStorage.setItem('username', 'Alice');
localStorage.setItem('theme', 'dark');

// Retrieve data
const name = localStorage.getItem('username'); // 'Alice'

// Remove item
localStorage.removeItem('username');

// Clear all
localStorage.clear();

// Store objects (must serialize!)
const user = { name: 'Alice', age: 25 };
localStorage.setItem('user', JSON.stringify(user));

// Retrieve objects
const saved = JSON.parse(localStorage.getItem('user'));
console.log(saved.name); // 'Alice'
```

### Complete DOM Example

```javascript
// Interactive todo list
class TodoApp {
    constructor(containerSelector) {
        this.container = document.querySelector(containerSelector);
        this.todos = JSON.parse(localStorage.getItem('todos')) || [];
        this.render();
        this.bindEvents();
    }

    bindEvents() {
        // Event delegation on container
        this.container.addEventListener('click', (e) => {
            if (e.target.matches('.todo-toggle')) {
                const id = Number(e.target.dataset.id);
                this.toggle(id);
            }
            if (e.target.matches('.todo-delete')) {
                const id = Number(e.target.dataset.id);
                this.remove(id);
            }
        });

        // Form submission
        this.container.querySelector('.todo-form')
            .addEventListener('submit', (e) => {
                e.preventDefault();
                const input = e.target.querySelector('input');
                if (input.value.trim()) {
                    this.add(input.value.trim());
                    input.value = '';
                }
            });
    }

    add(text) {
        this.todos.push({
            id: Date.now(),
            text,
            completed: false
        });
        this.save();
        this.render();
    }

    toggle(id) {
        const todo = this.todos.find(t => t.id === id);
        if (todo) todo.completed = !todo.completed;
        this.save();
        this.render();
    }

    remove(id) {
        this.todos = this.todos.filter(t => t.id !== id);
        this.save();
        this.render();
    }

    save() {
        localStorage.setItem('todos', JSON.stringify(this.todos));
    }

    render() {
        const list = this.container.querySelector('.todo-list');
        list.innerHTML = this.todos.map(todo => `
            <li class="${todo.completed ? 'completed' : ''}">
                <button class="todo-toggle" data-id="${todo.id}">
                    ${todo.completed ? '✓' : '○'}
                </button>
                <span>${todo.text}</span>
                <button class="todo-delete" data-id="${todo.id}">×</button>
            </li>
        `).join('');
    }
}

// Initialize when DOM is ready
document.addEventListener('DOMContentLoaded', () => {
    new TodoApp('#app');
});
```

### There are NO Dumb Questions

**Q: What's the difference between `textContent` and `innerHTML`?**
**A:** `textContent` sets/gets plain text (safe). `innerHTML` parses HTML (can execute scripts if you insert user input - XSS vulnerability!). Use `textContent` unless you need HTML.

**Q: When should I use localStorage vs sessionStorage?**
**A:** `localStorage` persists until explicitly cleared. `sessionStorage` is cleared when the tab closes. Use session for temporary data, local for persistent preferences.

**Q: What's the difference between `DOMContentLoaded` and `load`?**
**A:** `DOMContentLoaded` fires when HTML is parsed (fast). `load` waits for ALL resources (images, stylesheets, etc.) to finish loading (slow). Usually you want `DOMContentLoaded`.

---

## 16. Regular Expressions: Pattern Matching

### What are Regular Expressions?

Regular expressions (regex) are patterns for matching text. They're used to search, validate, extract, and replace strings.

```javascript
// Two ways to create regex
const regex1 = /hello/;           // Literal (preferred)
const regex2 = new RegExp('hello'); // Constructor (dynamic patterns)

// Basic test
/hello/.test('hello world'); // true
/hello/.test('goodbye');     // false
```

### Regex Flags

```javascript
/pattern/g;  // Global - find all matches, not just first
/pattern/i;  // Case insensitive
/pattern/m;  // Multiline - ^ and $ match line starts/ends
/pattern/s;  // Dotall - . matches newlines too
/pattern/u;  // Unicode support

// Combine flags
/hello/gi;   // Global + case insensitive
```

### Character Classes

```javascript
/[abc]/;     // Match a, b, or c
/[a-z]/;     // Match any lowercase letter
/[A-Z]/;     // Match any uppercase letter
/[0-9]/;     // Match any digit
/[a-zA-Z]/;  // Match any letter
/[^abc]/;    // Match anything EXCEPT a, b, c

// Shorthand character classes
/\d/;        // Digit [0-9]
/\D/;        // Non-digit [^0-9]
/\w/;        // Word character [a-zA-Z0-9_]
/\W/;        // Non-word character
/\s/;        // Whitespace (space, tab, newline)
/\S/;        // Non-whitespace
/./;         // Any character (except newline)
```

### Quantifiers

```javascript
/a*/;        // 0 or more a's
/a+/;        // 1 or more a's
/a?/;        // 0 or 1 a's (optional)
/a{3}/;      // Exactly 3 a's
/a{2,5}/;    // 2 to 5 a's
/a{2,}/;     // 2 or more a's

// Greedy vs Lazy
'aabab'.match(/a.*b/);   // 'aabab' (greedy - longest match)
'aabab'.match(/a.*?b/);  // 'aab' (lazy - shortest match)
```

### Anchors and Boundaries

```javascript
/^hello/;    // Must start with 'hello'
/world$/;    // Must end with 'world'
/^hello$/;   // Must be exactly 'hello'
/\bhello\b/; // Word boundary (whole word 'hello')

'hello world'.match(/^hello/);   // ['hello']
'say hello'.match(/^hello/);     // null (not at start)
```

### Groups and Alternation

```javascript
// Groups - capture parts of the match
const match = 'Jan 25, 2024'.match(/(\w+) (\d+), (\d+)/);
// match[0] = 'Jan 25, 2024' (full match)
// match[1] = 'Jan' (first group)
// match[2] = '25' (second group)
// match[3] = '2024' (third group)

// Named groups
const date = '2024-01-25'.match(/(?<year>\d{4})-(?<month>\d{2})-(?<day>\d{2})/);
date.groups.year;  // '2024'
date.groups.month; // '01'
date.groups.day;   // '25'

// Alternation (OR)
/cat|dog/;           // Match 'cat' or 'dog'
/(red|blue) car/;    // Match 'red car' or 'blue car'

// Non-capturing group (don't store match)
/(?:red|blue) car/;  // Groups but doesn't capture
```

### String Methods with Regex

```javascript
let str = 'Hello World, hello everyone';

// test - returns boolean
/hello/i.test(str);              // true

// match - returns matches
str.match(/hello/gi);            // ['Hello', 'hello']

// matchAll - returns iterator of all matches with groups
const matches = [...str.matchAll(/(\w+) (\w+)/g)];

// search - returns index of first match
str.search(/world/i);            // 6

// replace - replace matches
str.replace(/hello/gi, 'Hi');    // 'Hi World, Hi everyone'

// replaceAll - replace all matches
str.replaceAll('hello', 'hi');   // Only exact string matches

// split - split by pattern
'one1two2three'.split(/\d/);     // ['one', 'two', 'three']
```

### Watch It!
⚠️ **Regex can be a security risk!** Complex patterns can cause "catastrophic backtracking" (ReDoS attacks). Avoid nested quantifiers like `(a+)+` on user input.

### Common Regex Patterns

```javascript
// Email (simple validation)
const email = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
email.test('user@example.com');  // true

// URL
const url = /^https?:\/\/[\w\-.]+(:\d+)?(\/\S*)?$/;

// Phone number (US)
const phone = /^\(?(\d{3})\)?[-.\s]?(\d{3})[-.\s]?(\d{4})$/;
phone.test('(555) 123-4567');   // true

// Password (8+ chars, letter + number)
const password = /^(?=.*[A-Za-z])(?=.*\d).{8,}$/;

// Hex color
const hex = /^#([0-9A-Fa-f]{3}|[0-9A-Fa-f]{6})$/;
hex.test('#ff0000'); // true
hex.test('#f00');    // true
```

### Brain Power
🧠 What does `(?=...)` mean in regex?

**Answer:** It's a "lookahead" - it checks if a pattern exists ahead without consuming it. `(?=.*\d)` means "somewhere ahead there must be a digit." Used for complex validations like passwords that need multiple requirements.

### Complete Regex Example

```javascript
// Markdown-like text parser
function parseInlineMarkdown(text) {
    return text
        .replace(/\*\*(.+?)\*\*/g, '<strong>$1</strong>')      // **bold**
        .replace(/\*(.+?)\*/g, '<em>$1</em>')                  // *italic*
        .replace(/`(.+?)`/g, '<code>$1</code>')                // `code`
        .replace(/\[(.+?)\]\((.+?)\)/g, '<a href="$2">$1</a>') // [text](url)
}

parseInlineMarkdown('Hello **world** and *everyone*');
// 'Hello <strong>world</strong> and <em>everyone</em>'

// Input sanitizer
function sanitizeInput(input) {
    return input
        .replace(/[<>]/g, '')          // Remove angle brackets
        .replace(/\s+/g, ' ')          // Collapse whitespace
        .trim();
}

// Extract data from structured text
function parseCSVLine(line) {
    const values = [];
    const regex = /(?:"([^"]*(?:""[^"]*)*)"|([^,]*))(,|$)/g;
    let match;

    while ((match = regex.exec(line)) !== null) {
        values.push(match[1] !== undefined ? match[1].replace(/""/g, '"') : match[2]);
        if (match[3] === '') break;
    }

    return values;
}
```

### There are NO Dumb Questions

**Q: When should I use regex vs string methods?**
**A:** Use string methods (`includes`, `startsWith`, `indexOf`) for simple checks. Use regex for patterns, multiple matches, or complex replacements.

**Q: How do I make regex readable?**
**A:** Use named groups, break into smaller patterns, and add comments with `new RegExp()`:
```javascript
const datePattern = new RegExp(
    '(?<year>\\d{4})-' +   // Year
    '(?<month>\\d{2})-' +  // Month
    '(?<day>\\d{2})'        // Day
);
```

**Q: Why does my regex work in a tester but not in JavaScript?**
**A:** Common issues: forgetting the `g` flag for multiple matches, not escaping backslashes in `new RegExp('\\d')`, or using features not supported in all browsers.

---

## 17. Map and Set: Modern Collections

### Why Map and Set?

Objects and arrays have limitations as data structures. `Map` provides true key-value mapping (any key type), and `Set` provides unique value collections.

### Map: Key-value pairs with any key type

```javascript
// Creating a Map
const map = new Map();

// Setting values (any type as key!)
map.set('name', 'Alice');
map.set(42, 'a number key');
map.set(true, 'a boolean key');

const objKey = { id: 1 };
map.set(objKey, 'an object key');

// Getting values
map.get('name');    // 'Alice'
map.get(42);       // 'a number key'
map.get(objKey);   // 'an object key'

// Checking and deleting
map.has('name');    // true
map.delete('name');
map.size;           // 3
map.clear();        // Remove all
```

### Map vs Object

```javascript
// Objects: string/symbol keys only
const obj = {};
obj[1] = 'one';
obj['1'] = 'string one';
console.log(obj[1]); // 'string one' (key was coerced to string!)

// Map: any key type, no coercion
const map = new Map();
map.set(1, 'number one');
map.set('1', 'string one');
map.get(1);   // 'number one' (preserved!)
map.get('1'); // 'string one'
```

### Iterating Maps

```javascript
const userRoles = new Map([
    ['Alice', 'admin'],
    ['Bob', 'editor'],
    ['Charlie', 'viewer']
]);

// for...of
for (const [user, role] of userRoles) {
    console.log(`${user}: ${role}`);
}

// forEach
userRoles.forEach((role, user) => {
    console.log(`${user}: ${role}`);
});

// Get keys, values, entries
[...userRoles.keys()];    // ['Alice', 'Bob', 'Charlie']
[...userRoles.values()];  // ['admin', 'editor', 'viewer']
[...userRoles.entries()]; // [['Alice','admin'], ...]

// Convert to/from Object
const obj = Object.fromEntries(userRoles);
const map = new Map(Object.entries(obj));
```

### Watch It!
⚠️ **Use Map instead of Object when:**
- Keys are unknown at code time (dynamic)
- Keys are not strings (numbers, objects, etc.)
- You need to iterate in insertion order
- You need the `size` property
- You frequently add/remove entries

### Set: Unique values only

```javascript
// Creating a Set
const set = new Set();

set.add(1);
set.add(2);
set.add(3);
set.add(2); // Ignored! Already exists
set.add(1); // Ignored!

console.log(set.size); // 3
console.log(set);      // Set {1, 2, 3}

// Create from array (removes duplicates!)
const unique = new Set([1, 2, 2, 3, 3, 3]);
console.log([...unique]); // [1, 2, 3]

// Methods
set.has(2);     // true
set.delete(2);  // true
set.clear();    // Remove all
```

### Set Operations

```javascript
const a = new Set([1, 2, 3, 4]);
const b = new Set([3, 4, 5, 6]);

// Union (all elements from both)
const union = new Set([...a, ...b]);
// Set {1, 2, 3, 4, 5, 6}

// Intersection (elements in both)
const intersection = new Set([...a].filter(x => b.has(x)));
// Set {3, 4}

// Difference (elements in a but not b)
const difference = new Set([...a].filter(x => !b.has(x)));
// Set {1, 2}

// Symmetric difference (elements in one but not both)
const symDiff = new Set([...a].filter(x => !b.has(x)).concat([...b].filter(x => !a.has(x))));
// Set {1, 2, 5, 6}
```

### Brain Power
🧠 When should you use a Set instead of an Array?

**Answer:**
- When you need unique values (no duplicates)
- When you frequently check if a value exists (`Set.has()` is O(1), `Array.includes()` is O(n))
- When you don't need index-based access

### WeakMap and WeakSet

```javascript
// WeakMap: keys must be objects, garbage-collected when no other references
const cache = new WeakMap();

function processUser(user) {
    if (cache.has(user)) {
        return cache.get(user); // Return cached result
    }
    const result = expensiveOperation(user);
    cache.set(user, result);
    return result;
}

// When 'user' is garbage collected, the cache entry is too!
// No memory leaks!

// WeakSet: values must be objects, garbage-collected
const visited = new WeakSet();

function trackVisit(node) {
    if (visited.has(node)) return; // Already visited
    visited.add(node);
    // Process node...
}
```

### Complete Map/Set Example

```javascript
// Word frequency counter
function wordFrequency(text) {
    const words = text.toLowerCase().match(/\b\w+\b/g) || [];
    const freq = new Map();

    for (const word of words) {
        freq.set(word, (freq.get(word) || 0) + 1);
    }

    // Sort by frequency (descending)
    return [...freq.entries()]
        .sort((a, b) => b[1] - a[1]);
}

wordFrequency('the cat sat on the mat');
// [['the', 2], ['cat', 1], ['sat', 1], ['on', 1], ['mat', 1]]

// Tag system with Set
class TagManager {
    #tags = new Map(); // item -> Set of tags

    addTag(item, tag) {
        if (!this.#tags.has(item)) {
            this.#tags.set(item, new Set());
        }
        this.#tags.get(item).add(tag);
    }

    removeTag(item, tag) {
        this.#tags.get(item)?.delete(tag);
    }

    getTags(item) {
        return [...(this.#tags.get(item) || [])];
    }

    getItemsByTag(tag) {
        const results = [];
        for (const [item, tags] of this.#tags) {
            if (tags.has(tag)) results.push(item);
        }
        return results;
    }
}

const tags = new TagManager();
tags.addTag('post1', 'javascript');
tags.addTag('post1', 'tutorial');
tags.addTag('post2', 'javascript');
tags.getTags('post1');              // ['javascript', 'tutorial']
tags.getItemsByTag('javascript');   // ['post1', 'post2']
```

### There are NO Dumb Questions

**Q: Why can't WeakMap keys be primitives?**
**A:** WeakMap relies on garbage collection. Primitives aren't garbage collected (they're copied by value), so there's no reference to "weaken."

**Q: Does Map preserve insertion order?**
**A:** Yes! Both Map and Set iterate in insertion order. Objects also preserve insertion order in modern engines, but Map guarantees it by specification.

**Q: Can I use JSON.stringify on a Map?**
**A:** Not directly. Convert to array first: `JSON.stringify([...map])`. To parse back: `new Map(JSON.parse(str))`.

---

## 18. Strings, Dates, and JSON: Essential Built-ins

### String Methods (Complete reference)

```javascript
let str = 'Hello, World!';

// Searching
str.indexOf('World');         // 7
str.lastIndexOf('l');         // 10
str.includes('World');        // true
str.startsWith('Hello');      // true
str.endsWith('!');            // true
str.search(/world/i);        // 7 (regex search)

// Extracting
str.slice(7, 12);            // 'World'
str.slice(-6);               // 'orld!'
str.substring(0, 5);         // 'Hello'
str.charAt(0);               // 'H'
str.at(-1);                  // '!' (ES2022)

// Transforming
str.toUpperCase();           // 'HELLO, WORLD!'
str.toLowerCase();           // 'hello, world!'
str.trim();                  // Remove whitespace both ends
str.trimStart();             // Remove whitespace from start
str.trimEnd();               // Remove whitespace from end
str.padStart(20, '-');       // '-------Hello, World!'
str.padEnd(20, '-');         // 'Hello, World!-------'
str.repeat(2);               // 'Hello, World!Hello, World!'

// Replacing
str.replace('World', 'JS');           // 'Hello, JS!'
str.replace(/l/g, 'L');               // 'HeLLo, WorLd!'
str.replaceAll('l', 'L');             // 'HeLLo, WorLd!'

// Splitting and joining
str.split(', ');             // ['Hello', 'World!']
'a-b-c'.split('-');          // ['a', 'b', 'c']
['a', 'b', 'c'].join('-');  // 'a-b-c'
```

### Template Literals: Advanced usage

```javascript
// Tagged templates
function highlight(strings, ...values) {
    return strings.reduce((result, str, i) => {
        const value = values[i] !== undefined ? `<mark>${values[i]}</mark>` : '';
        return result + str + value;
    }, '');
}

const name = 'Alice';
const age = 25;
highlight`My name is ${name} and I'm ${age} years old.`;
// 'My name is <mark>Alice</mark> and I'm <mark>25</mark> years old.'

// Raw strings (no escape processing)
String.raw`\n\t`; // '\\n\\t' (literal backslash-n, not newline)
```

### JSON: Data interchange format

```javascript
// JavaScript Object Notation
// Used for APIs, config files, data storage

const user = {
    name: 'Alice',
    age: 25,
    hobbies: ['reading', 'coding'],
    address: { city: 'NYC' }
};

// Stringify (object → string)
const json = JSON.stringify(user);
// '{"name":"Alice","age":25,"hobbies":["reading","coding"],"address":{"city":"NYC"}}'

// Pretty print
JSON.stringify(user, null, 2);
// Formatted with 2-space indentation

// Custom serialization (replacer)
JSON.stringify(user, ['name', 'age']);
// '{"name":"Alice","age":25}' (only specified keys)

JSON.stringify(user, (key, value) => {
    if (typeof value === 'string') return value.toUpperCase();
    return value;
});

// Parse (string → object)
const parsed = JSON.parse(json);
console.log(parsed.name); // 'Alice'

// Reviver (custom deserialization)
const withDates = '{"created":"2024-01-25T10:00:00Z"}';
JSON.parse(withDates, (key, value) => {
    if (key === 'created') return new Date(value);
    return value;
});
```

### Watch It!
⚠️ **JSON.stringify ignores `undefined`, functions, and Symbols!** These are silently dropped from objects. Arrays replace them with `null`.

```javascript
JSON.stringify({ a: undefined, b: function() {}, c: Symbol() });
// '{}' (all dropped!)

JSON.stringify([undefined, function() {}, Symbol()]);
// '[null,null,null]' (replaced with null)
```

### Date: Working with time

```javascript
// Creating dates
const now = new Date();                    // Current date/time
const specific = new Date(2024, 0, 25);   // Jan 25, 2024 (month is 0-indexed!)
const fromString = new Date('2024-01-25'); // From ISO string
const fromTimestamp = new Date(1706140800000); // From milliseconds

// Getting components
now.getFullYear();     // 2024
now.getMonth();        // 0-11 (0 = January!)
now.getDate();         // 1-31
now.getDay();          // 0-6 (0 = Sunday)
now.getHours();        // 0-23
now.getMinutes();      // 0-59
now.getSeconds();      // 0-59
now.getTime();         // Milliseconds since epoch

// Setting components
now.setFullYear(2025);
now.setMonth(11);      // December
now.setDate(25);

// Formatting
now.toISOString();     // '2024-01-25T10:30:00.000Z'
now.toLocaleDateString(); // '1/25/2024' (locale-dependent)
now.toLocaleTimeString(); // '10:30:00 AM'
now.toLocaleString('en-US', {
    weekday: 'long',
    year: 'numeric',
    month: 'long',
    day: 'numeric'
}); // 'Thursday, January 25, 2024'
```

### Watch It!
⚠️ **Months are 0-indexed in JavaScript!** January is 0, December is 11. This is a constant source of bugs. `new Date(2024, 1, 1)` is February 1st, not January!

### Date Arithmetic

```javascript
// Difference between dates
const start = new Date('2024-01-01');
const end = new Date('2024-12-31');
const diffMs = end - start;                          // Milliseconds
const diffDays = Math.floor(diffMs / (1000 * 60 * 60 * 24)); // 365

// Add/subtract time
function addDays(date, days) {
    const result = new Date(date);
    result.setDate(result.getDate() + days);
    return result;
}

addDays(new Date('2024-01-25'), 7); // Feb 1, 2024

// Compare dates
const date1 = new Date('2024-01-01');
const date2 = new Date('2024-06-15');
date1 < date2;  // true
date1 > date2;  // false
date1.getTime() === date2.getTime(); // Exact equality
```

### Brain Power
🧠 Why is the Date API so awkward?

**Answer:** JavaScript's Date was copied from Java 1.0 in 1995, and even Java replaced it! The 0-indexed months, mutable dates, and limited formatting are legacy issues. Use libraries like `date-fns` or the upcoming Temporal API for serious date work.

### Complete Built-ins Example

```javascript
// Log entry parser and formatter
function parseLogEntry(line) {
    // Parse: "[2024-01-25 10:30:45] ERROR: Connection failed"
    const regex = /\[(?<date>[\d-]+) (?<time>[\d:]+)\] (?<level>\w+): (?<message>.+)/;
    const match = line.match(regex);

    if (!match) return null;

    const { date, time, level, message } = match.groups;
    return {
        timestamp: new Date(`${date}T${time}`),
        level,
        message
    };
}

// Format relative time ("2 hours ago", "just now")
function timeAgo(date) {
    const seconds = Math.floor((new Date() - date) / 1000);

    const intervals = [
        { label: 'year', seconds: 31536000 },
        { label: 'month', seconds: 2592000 },
        { label: 'day', seconds: 86400 },
        { label: 'hour', seconds: 3600 },
        { label: 'minute', seconds: 60 }
    ];

    for (const { label, seconds: intervalSeconds } of intervals) {
        const count = Math.floor(seconds / intervalSeconds);
        if (count >= 1) {
            return `${count} ${label}${count > 1 ? 's' : ''} ago`;
        }
    }

    return 'just now';
}

// Deep clone with JSON (simple objects only)
function deepClone(obj) {
    return JSON.parse(JSON.stringify(obj));
}

// Safe JSON parse with fallback
function safeJSON(str, fallback = null) {
    try {
        return JSON.parse(str);
    } catch {
        return fallback;
    }
}

safeJSON('{"valid": true}');  // { valid: true }
safeJSON('not json', []);     // [] (fallback)
```

### There are NO Dumb Questions

**Q: What's the difference between `slice` and `substring` for strings?**
**A:** They're similar, but `slice` supports negative indices (`str.slice(-3)` = last 3 chars) while `substring` treats negatives as 0. Prefer `slice`.

**Q: Should I use Date or a library?**
**A:** For simple timestamps and comparisons, `Date` is fine. For timezones, formatting, parsing, or complex math, use `date-fns`, `dayjs`, or `luxon`.

**Q: What can't be represented in JSON?**
**A:** `undefined`, functions, Symbols, `Infinity`, `NaN`, circular references, `Date` objects (serialized as strings), `Map`/`Set`, and `BigInt`.

---

## Congratulations!

You've made it through the JavaScript essentials! But this is just the beginning.

### What's next?

1. **Practice, practice, practice** - Build projects!
2. **Learn a framework** - React, Vue, or Angular
3. **Build with Node.js** - Server-side JavaScript
4. **Explore TypeScript** - Static types for JavaScript
5. **Learn testing** - Jest, Vitest, or Playwright
6. **Study design patterns** - Singleton, Observer, Factory
7. **Keep learning** - JavaScript evolves every year!

### Final Challenge
🧠 Build a complete to-do list app with:
- Add/remove items
- Mark items complete
- Save to localStorage
- Filter by status
- Full ES6+ syntax

### Additional Resources

- **MDN Web Docs:** https://developer.mozilla.org/en-US/docs/Web/JavaScript
- **JavaScript.info:** https://javascript.info/
- **Eloquent JavaScript:** https://eloquentjavascript.net/
- **You Don't Know JS:** https://github.com/getify/You-Dont-Know-JS
- **Frontend Roadmap:** https://roadmap.sh/javascript

---

## Quick Reference Card

**Variables:**
```javascript
let x = 10;           // Mutable, block-scoped
const y = 20;         // Immutable, block-scoped
var z = 30;           // Avoid! Function-scoped
```

**Data Types:**
```javascript
string, number, bigint, boolean, undefined, null, symbol, object
```

**Destructuring & Spread:**
```javascript
const { name, age } = person;   // Object destructuring
const [a, b, ...rest] = arr;    // Array destructuring
const merged = { ...obj1, ...obj2 }; // Object spread
const combined = [...arr1, ...arr2]; // Array spread
```

**Functions:**
```javascript
function name() { }           // Declaration (hoisted)
const name = function() { };  // Expression
const name = () => { };       // Arrow (inherits this)
```

**Arrays:**
```javascript
arr.push(4);      // Add to end
arr.pop();        // Remove from end
arr.map(fn)       // Transform
arr.filter(fn)    // Select
arr.reduce(fn, init) // Accumulate
arr.find(fn)      // First match
```

**Objects:**
```javascript
let obj = { key: 'value' };
obj.key;                         // Dot notation
obj['key'];                      // Bracket notation
Object.keys(obj);                // ['key']
Object.entries(obj);             // [['key', 'value']]
```

**Classes:**
```javascript
class Animal extends Base {
    #privateField = 0;           // Private
    constructor(name) { super(); this.name = name; }
    speak() { return this.name; } // Method
    static create() { }          // Static
}
```

**Modules:**
```javascript
export function add() { }       // Named export
export default class App { }    // Default export
import App, { add } from './module.js';
```

**Async:**
```javascript
async function name() {
    const data = await fetch(url);
    return data.json();
}
const [a, b] = await Promise.all([p1, p2]); // Parallel
```

**DOM:**
```javascript
document.querySelector('.class')            // Select
el.classList.add('active')                  // Modify
el.addEventListener('click', fn)            // Listen
document.createElement('div')              // Create
```

**Regex:**
```javascript
/pattern/gi.test(str)           // Boolean match
str.match(/(\d+)/g)            // Find matches
str.replace(/old/g, 'new')     // Replace
```

---

**Created in the style of Head First books**

*Now go build something amazing with JavaScript!* 🚀