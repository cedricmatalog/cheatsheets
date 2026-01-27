# Head First React Cheatsheet

> Your brain on React. Here you'll learn to build modern web apps the way your brain likes to learn - with conversational style, practical examples, and concepts that actually stick.

---

## How to Use This Cheatsheet

**We think of React as powerful, not puzzling.** You'll find Q&A sections, "Watch It!" warnings, "Brain Power" exercises, and lots of conversation. React has a learning curve, but we'll make it smooth.

**The activities are NOT optional.** The exercises and challenges are part of the learning experience. Create a React app and try the code!

**The redundancy is intentional.** React concepts build on each other. You'll see state, props, and re-rendering pop up again and again - that's how it sticks.

---

## Prerequisites

**Important:** Make sure you're comfortable with JavaScript ES6+ before learning React:
- Arrow functions
- Destructuring
- Array methods (map, filter, reduce)
- Spread operator
- Template literals
- Promises and async/await

If you need a refresher, check out the JavaScript cheatsheet first!

---

## Table of Contents

### Part 1: Fundamentals
1. [Introduction: What is React?](#1-introduction-what-is-react)
2. [Components: Building Blocks](#2-components-building-blocks)
3. [JSX: HTML in JavaScript](#3-jsx-html-in-javascript)
4. [Props: Passing Data Down](#4-props-passing-data-down)
5. [State: Data That Changes](#5-state-data-that-changes)
6. [Events: Handling Interactions](#6-events-handling-interactions)
7. [Conditional Rendering: Show or Hide](#7-conditional-rendering-show-or-hide)
8. [Lists & Keys: Rendering Collections](#8-lists--keys-rendering-collections)
9. [Forms: Controlled & Uncontrolled](#9-forms-controlled--uncontrolled)

### Part 2: Hooks Deep Dive
10. [Rules of Hooks](#10-rules-of-hooks)
11. [useEffect: Side Effects](#11-useeffect-side-effects)
12. [useRef, useLayoutEffect & useId](#12-useref-uselayouteffect--useid)
13. [Custom Hooks: Reusable Logic](#13-custom-hooks-reusable-logic)

### Part 3: Advanced Patterns
14. [Context: Sharing State](#14-context-sharing-state)
15. [Portals: Escaping the DOM](#15-portals-escaping-the-dom)
16. [forwardRef & useImperativeHandle](#16-forwardref--useimperativehandle)
17. [Error Boundaries](#17-error-boundaries)
18. [Common Patterns](#18-common-patterns)

### Part 4: Data & Navigation
19. [Routing: Navigation](#19-routing-navigation)
20. [API Calls: Fetching Data](#20-api-calls-fetching-data)
21. [State Management: Zustand](#21-state-management-zustand)

### Part 5: Performance
22. [Performance: memo, useMemo, useCallback](#22-performance-memo-usememo-usecallback)
23. [useReducer: Complex State](#23-usereducer-complex-state)
24. [Code Splitting & Lazy Loading](#24-code-splitting--lazy-loading)
25. [React 18+ Features](#25-react-18-features)

### Part 6: Production
26. [TypeScript with React](#26-typescript-with-react)
27. [Styling: CSS Solutions](#27-styling-css-solutions)
28. [Accessibility: Building for Everyone](#28-accessibility-building-for-everyone)
29. [Testing](#29-testing)
30. [Strict Mode](#30-strict-mode)
31. [React DevTools](#31-react-devtools)
32. [Common Pitfalls](#32-common-pitfalls)
33. [Server Components](#33-server-components)

---

## 1. Introduction: What is React?

### React: A library for building UIs

React is a JavaScript library created by Facebook (Meta) for building user interfaces. It's **component-based**, **declarative**, and makes building complex UIs manageable.

**Why React?**
- **Component-based:** Break UI into reusable pieces
- **Declarative:** Describe what you want, React handles how
- **Fast:** Virtual DOM makes updates efficient
- **Popular:** Huge ecosystem, lots of jobs

### Setting up React

```bash
# Create a new React app with Vite (fast, modern)
npm create vite@latest my-app -- --template react
cd my-app
npm install
npm run dev

# Or with Create React App (older, slower)
npx create-react-app my-app
cd my-app
npm start
```

### Your first React component

```jsx
// ProductCard.jsx
function ProductCard() {
    return (
        <div className="card">
            <img src="/sneakers.jpg" alt="Cool Sneakers" />
            <h3>Air Max 90</h3>
            <p>$129.99</p>
            <button>Add to Cart</button>
        </div>
    );
}

export default ProductCard;
```

### Brain Power
🧠 Why do you think React is called "React"? What does it react to?

**Answer:** React "reacts" to state changes! When data changes, React automatically updates the UI. You don't manually manipulate the DOM - React does it for you.

### Watch It!
⚠️ **React is a library, not a framework!** It only handles the view layer. For routing, state management, and other features, you'll add other libraries. (Next.js is a framework built on React.)

### There are NO Dumb Questions

**Q: What's the difference between React and other frameworks like Vue or Angular?**
**A:** React is a library (just UI), Vue/Angular are frameworks (everything included). React uses JSX, Vue uses templates, Angular uses TypeScript templates. All are great - React is most popular.

**Q: Do I need to learn class components?**
**A:** No! React recommends functional components with hooks (since 2019). You might see class components in old code, but start with functional.

**Q: What's the Virtual DOM?**
**A:** A JavaScript copy of the real DOM. React compares the virtual and real DOM, then only updates what changed. Much faster than updating everything!

### Interview Checkpoint 🛑
**Interviewer:** "Explain the Virtual DOM and how it aids performance."
**You:** "The Virtual DOM is a lightweight JavaScript representation of the real DOM. When state changes, React updates the Virtual DOM first, compares it to the previous version (diffing), and then efficiently updates only the changed elements in the real DOM (reconciliation). This minimizes slow browser reflows."

---

## 2. Components: Building Blocks

### What are components?

Components are reusable pieces of UI. Think of them as custom HTML elements.

```jsx
// Button component
function Button() {
    return <button>Click me</button>;
}

// Using the component
function App() {
    return (
        <div>
            <Button />
            <Button />
            <Button />
        </div>
    );
}
```

### Functional Components: The modern way

```jsx
// Named function (recommended)
function Welcome() {
    return <h1>Welcome to React</h1>;
}

// Arrow function
const Welcome = () => {
    return <h1>Welcome to React</h1>;
};

// Implicit return (single element)
const Welcome = () => <h1>Welcome to React</h1>;
```

### Component Composition: Building bigger from smaller

```jsx
function Header() {
    return <header><h1>My App</h1></header>;
}

function Main() {
    return <main><p>Welcome!</p></main>;
}

function Footer() {
    return <footer><p>&copy; {new Date().getFullYear()}</p></footer>;
}

function App() {
    return (
        <div>
            <Header />
            <Main />
            <Footer />
        </div>
    );
}
```

### Component Files: Organization

```
src/
├── components/
│   ├── Button.jsx
│   ├── Card.jsx
│   └── Header.jsx
├── App.jsx
└── main.jsx
```

```jsx
// Button.jsx
function Button() {
    return <button>Click me</button>;
}

export default Button;

// App.jsx
import Button from './components/Button';

function App() {
    return <Button />;
}
```

### Watch It!
⚠️ **Component names MUST start with a capital letter!** `<button>` is HTML, `<Button>` is a React component. Lowercase = HTML, Uppercase = React component.

### Brain Power
🧠 Why do you think React uses component composition instead of inheritance?

**Answer:** Composition is more flexible! Instead of "is-a" relationships (inheritance), you have "has-a" relationships. A Dashboard "has" a Header, not "is a" Header. Easier to reuse and understand.

### Complete Components Example

```jsx
function Avatar({ src, alt, size = 'md' }) {
    const sizes = { sm: 32, md: 48, lg: 64 };
    return <img src={src} alt={alt} width={sizes[size]} className="avatar" />;
}

function UserInfo({ name, role }) {
    return (
        <div className="user-info">
            <strong>{name}</strong>
            <span>{role}</span>
        </div>
    );
}

function UserCard({ user }) {
    return (
        <div className="user-card">
            <Avatar src={user.avatar} alt={user.name} size="lg" />
            <UserInfo name={user.name} role={user.role} />
        </div>
    );
}
```

### There are NO Dumb Questions

**Q: Should I use named functions or arrow functions for components?**
**A:** Either works! Named functions show up better in DevTools and stack traces. Arrow functions are shorter. Teams usually pick one and stay consistent.

**Q: How small should a component be?**
**A:** If a component does one thing and you can name it clearly, it's the right size. A 5-line component is fine. Don't over-split - if extracting a piece doesn't add clarity, keep it inline.

**Q: Can a component return `null`?**
**A:** Yes! Returning `null` renders nothing. Useful for conditional rendering: `if (!isVisible) return null;`

---

## 3. JSX: HTML in JavaScript

### What is JSX?

JSX looks like HTML but it's actually JavaScript. It gets compiled to `React.createElement()` calls.

```jsx
// JSX
const element = <h1>Hello, world!</h1>;

// Compiles to:
const element = React.createElement('h1', null, 'Hello, world!');
```

### JSX Rules: Important differences from HTML

```jsx
// 1. Use className instead of class
<div className="container">Content</div>

// 2. Use camelCase for attributes
<input type="text" onChange={handleChange} />
<label htmlFor="name">Name:</label>

// 3. Self-closing tags need slash
<img src="photo.jpg" />
<input type="text" />
<br />

// 4. Must return single parent element
// Wrong:
function App() {
    return (
        <h1>Title</h1>
        <p>Paragraph</p>
    );
}

// Right: Wrap in div
function App() {
    return (
        <div>
            <h1>Title</h1>
            <p>Paragraph</p>
        </div>
    );
}

// Or use Fragment (no extra DOM node)
function App() {
    return (
        <>
            <h1>Title</h1>
            <p>Paragraph</p>
        </>
    );
}
```

### JavaScript in JSX: Curly braces

```jsx
function Greeting() {
    const name = 'Alice';
    const age = 25;

    return (
        <div>
            <h1>Hello, {name}!</h1>
            <p>You are {age} years old</p>
            <p>Next year: {age + 1}</p>
            <p>Random: {Math.random()}</p>
        </div>
    );
}
```

### JSX Expressions: What works

```jsx
function Example() {
    const isLoggedIn = true;
    const user = { name: 'Alice', age: 25 };
    const numbers = [1, 2, 3, 4, 5];

    return (
        <div>
            {/* Variables */}
            <p>{user.name}</p>

            {/* Expressions */}
            <p>{2 + 2}</p>
            <p>{user.age > 18 ? 'Adult' : 'Minor'}</p>

            {/* Function calls */}
            <p>{user.name.toUpperCase()}</p>

            {/* Array methods */}
            <ul>
                {numbers.map(num => <li key={num}>{num}</li>)}
            </ul>

            {/* Conditionals (ternary) */}
            {isLoggedIn ? <p>Welcome back!</p> : <p>Please log in</p>}

            {/* Logical AND */}
            {isLoggedIn && <p>You are logged in</p>}

            {/* Comments */}
            {/* This is a comment in JSX */}
        </div>
    );
}
```

### Watch It!
⚠️ **You can't use if-else statements directly in JSX!** Use ternary operators `? :` or logical operators `&&` instead. Or put the logic outside the return statement.

```jsx
// Wrong:
return (
    <div>
        {if (isLoggedIn) { <p>Hi</p> }}  // Error!
    </div>
);

// Right:
if (isLoggedIn) {
    return <p>Hi</p>;
} else {
    return <p>Please log in</p>;
}

// Or use ternary:
return (
    <div>
        {isLoggedIn ? <p>Hi</p> : <p>Please log in</p>}
    </div>
);
```

### Complete JSX Example

```jsx
function UserCard() {
    const user = {
        name: 'Alice Johnson',
        age: 28,
        email: 'alice@example.com',
        avatar: 'https://via.placeholder.com/150',
        isOnline: true
    };

    const hobbies = ['Reading', 'Hiking', 'Photography'];

    return (
        <div className="user-card">
            <img src={user.avatar} alt={user.name} />
            <h2>{user.name}</h2>
            <p>Age: {user.age}</p>
            <p>Email: {user.email}</p>

            {/* Conditional rendering */}
            {user.isOnline && <span className="status-online">● Online</span>}

            {/* List rendering */}
            <h3>Hobbies:</h3>
            <ul>
                {hobbies.map((hobby) => (
                    <li key={hobby}>{hobby}</li>
                ))}
            </ul>

            {/* Ternary operator */}
            <p>Status: {user.age >= 18 ? 'Adult' : 'Minor'}</p>
        </div>
    );
}
```

### Brain Power
🧠 What does JSX actually compile to?

**Answer:** JSX is syntactic sugar for `React.createElement()` calls. `<div className="box">Hello</div>` becomes `React.createElement('div', { className: 'box' }, 'Hello')`. The build tool (Babel/SWC) handles this transformation.

### There are NO Dumb Questions

**Q: Why use JSX instead of just HTML?**
**A:** JSX is dynamic! You can use variables, expressions, and JavaScript logic right in your markup. HTML is static. Plus, JSX is type-checked and prevents XSS attacks.

**Q: Can I write React without JSX?**
**A:** Yes, but nobody does! JSX is much cleaner than `React.createElement()` calls.

**Q: Why className instead of class?**
**A:** `class` is a reserved keyword in JavaScript (for classes). JSX is JavaScript, so it uses `className` instead.

---

## 4. Props: Passing Data Down

### What are props?

Props (properties) are how you pass data from parent to child components. Think of them as function parameters.

```jsx
// Parent passes props
function App() {
    return <UserAvatar username="jdoe" imageUrl="/avatar.jpg" />;
}

// Child receives props
function UserAvatar(props) {
    return (
        <div className="avatar">
            <img src={props.imageUrl} alt={props.username} />
            <span>@{props.username}</span>
        </div>
    );
}
```

### Destructuring Props: Cleaner syntax

```jsx
// Without destructuring
function UserAvatar(props) {
    return <span>@{props.username}</span>;
}

// With destructuring (recommended!)
function UserAvatar({ username, imageUrl }) {
    return (
        <div className="avatar">
            <img src={imageUrl} alt={username} />
            <span>@{username}</span>
        </div>
    );
}
```

### Default Props: Fallback values

```jsx
function UserAvatar({ username = 'Guest', imageUrl = '/default.jpg' }) {
    return (
        <div className="avatar">
            <img src={imageUrl} alt={username} />
            <span>@{username}</span>
        </div>
    );
}

// Usage
<UserAvatar />  // Uses defaults
<UserAvatar username="alice" />  // Uses alice, default image
```

### Children Prop: Wrapping content

```jsx
function Card({ children }) {
    return (
        <div className="card">
            {children}
        </div>
    );
}

// Usage
function App() {
    return (
        <Card>
            <h2>Title</h2>
            <p>This is the content</p>
        </Card>
    );
}
```

### Props are Read-Only: Never modify!

```jsx
// Wrong! Never modify props
function Greeting({ name }) {
    name = 'Bob';  // ❌ DON'T DO THIS!
    return <h1>Hello, {name}</h1>;
}

// Right! Props are immutable
function Greeting({ name }) {
    return <h1>Hello, {name}</h1>;
}
```

### Watch It!
⚠️ **Props flow DOWN only!** Parent to child, never up. If a child needs to communicate with parent, parent passes down a function as a prop.

### Brain Power
🧠 Why do you think props are read-only? What would happen if children could modify props?

**Answer:** If children could modify props, it would cause chaos! Multiple children might change the same data. Props are one-way to keep data flow predictable and debuggable.

### Passing Functions as Props

```jsx
function Parent() {
    const handleClick = () => {
        alert('Button clicked!');
    };

    return <Button onClick={handleClick} />;
}

function Button({ onClick }) {
    return <button onClick={onClick}>Click me</button>;
}
```

### Complete Props Example

```jsx
// Reusable Button component
function Button({ text, color = 'blue', onClick }) {
    return (
        <button
            style={{ backgroundColor: color, color: 'white' }}
            onClick={onClick}
        >
            {text}
        </button>
    );
}

// Card component with children
function Card({ title, children }) {
    return (
        <div className="card">
            <h2>{title}</h2>
            <div className="card-content">
                {children}
            </div>
        </div>
    );
}

// Using the components
function App() {
    const handleClick = () => alert('Clicked!');

    return (
        <div>
            <Button text="Primary" color="blue" onClick={handleClick} />
            <Button text="Danger" color="red" onClick={handleClick} />
            <Button text="Success" color="green" onClick={handleClick} />

            <Card title="User Profile">
                <p>Name: Alice</p>
                <p>Age: 25</p>
                <Button text="Edit Profile" onClick={handleClick} />
            </Card>
        </div>
    );
}
```

### There are NO Dumb Questions

**Q: What's the difference between props and state?**
**A:** Props are passed FROM parent (like function parameters). State is managed WITHIN component (like function variables). Props are read-only, state can change.

**Q: Can I pass anything as props?**
**A:** Yes! Strings, numbers, booleans, objects, arrays, functions, even other components!

**Q: Why use destructuring for props?**
**A:** Cleaner code! `name` is clearer than `props.name`. Plus, you can see exactly what props a component uses.

### Interview Checkpoint 🛑
**Interviewer:** "What is Prop Drilling and how do you avoid it?"
**You:** "Prop Drilling happens when you pass data through many layers of components that don't need it, just to reach a deep child. To avoid it, I can use **Composition** (passing components as children), **Context API** (for global state), or state management libraries like **Redux/Zustand**."

---

## 5. State: Data That Changes

### What is state?

State is data that changes over time. When state changes, React re-renders the component.

```jsx
import { useState } from 'react';

function ItemQuantity() {
    const [quantity, setQuantity] = useState(1);

    return (
        <div className="quantity-selector">
            <button onClick={() => setQuantity(quantity - 1)}>-</button>
            <span>{quantity}</span>
            <button onClick={() => setQuantity(quantity + 1)}>+</button>
        </div>
    );
}
```

### useState: The state hook

```jsx
const [state, setState] = useState(initialValue);
```

- `state` - Current value
- `setState` - Function to update the value
- `initialValue` - Starting value

### State Examples

```jsx
function Examples() {
    // Number state (Quantity)
    const [quantity, setQuantity] = useState(1);

    // String state (Search query)
    const [search, setSearch] = useState('');

    // Boolean state (Modal open)
    const [isOpen, setIsOpen] = useState(false);

    // Object state (Form data)
    const [form, setForm] = useState({
        username: '',
        email: ''
    });

    // Array state (Shopping cart)
    const [cart, setCart] = useState([]);

    return <div>Examples component</div>;
}
```

### Updating State: Important rules

```jsx
// Wrong! Don't modify state directly
function Counter() {
    const [count, setCount] = useState(0);

    const increment = () => {
        count = count + 1;  // ❌ Doesn't work!
    };

    return <button onClick={increment}>+</button>;
}

// Right! Use setter function
function Counter() {
    const [count, setCount] = useState(0);

    const increment = () => {
        setCount(count + 1);  // ✅ Works!
    };

    return <button onClick={increment}>+</button>;
}
```

### Functional Updates: Safer state updates

```jsx
// Problem: Multiple updates might not work
function Counter() {
    const [count, setCount] = useState(0);

    const increment3Times = () => {
        setCount(count + 1);
        setCount(count + 1);
        setCount(count + 1);
        // Only increments by 1! (batched)
    };

    return <button onClick={increment3Times}>+3</button>;
}

// Solution: Use functional update
function Counter() {
    const [count, setCount] = useState(0);

    const increment3Times = () => {
        setCount(prev => prev + 1);
        setCount(prev => prev + 1);
        setCount(prev => prev + 1);
        // Increments by 3! ✅
    };

    return <button onClick={increment3Times}>+3</button>;
}
```

### Watch It!
⚠️ **State updates are asynchronous!** Don't rely on the state value immediately after calling setState. Use functional updates if you need the previous value.

### Updating Objects in State

```jsx
function UserProfile() {
    const [user, setUser] = useState({
        name: 'Alice',
        age: 25,
        email: 'alice@example.com'
    });

    // Wrong! Mutates state directly
    const updateName = () => {
        user.name = 'Bob';  // ❌ Don't do this!
        setUser(user);
    };

    // Right! Create new object
    const updateName = () => {
        setUser({
            ...user,  // Copy existing properties
            name: 'Bob'  // Override name
        });
    };

    // Multiple properties
    const updateUser = () => {
        setUser({
            ...user,
            name: 'Bob',
            age: 30
        });
    };

    return (
        <div>
            <p>{user.name} - {user.age}</p>
            <button onClick={updateName}>Change Name</button>
        </div>
    );
}
```

### Updating Arrays in State

```jsx
function TodoList() {
    const [todos, setTodos] = useState(['Buy milk', 'Walk dog']);

    // Add item
    const addTodo = (text) => {
        setTodos([...todos, text]);  // Spread existing, add new
    };

    // Remove item
    const removeTodo = (index) => {
        setTodos(todos.filter((_, i) => i !== index));
    };

    // Update item
    const updateTodo = (index, newText) => {
        setTodos(todos.map((todo, i) =>
            i === index ? newText : todo
        ));
    };

    return (
        <ul>
            {todos.map((todo, index) => (
                <li key={index}>
                    {todo}
                    <button onClick={() => removeTodo(index)}>Delete</button>
                </li>
            ))}
            <button onClick={() => addTodo('New todo')}>Add</button>
        </ul>
    );
}
```

### Brain Power
🧠 Why can't you modify state directly? Why do you need `setState`?

**Answer:** React needs to KNOW when state changes so it can re-render. If you mutate state directly, React doesn't know anything changed! `setState` triggers a re-render.

### Complete State Example

```jsx
function ShoppingCart() {
    const [items, setItems] = useState([
        { id: 1, name: 'Apple', price: 1.50, quantity: 2 },
        { id: 2, name: 'Banana', price: 0.75, quantity: 3 }
    ]);

    // Add item
    const addItem = (name, price) => {
        const newItem = {
            id: Date.now(),
            name,
            price,
            quantity: 1
        };
        setItems([...items, newItem]);
    };

    // Update quantity
    const updateQuantity = (id, newQuantity) => {
        setItems(items.map(item =>
            item.id === id
                ? { ...item, quantity: newQuantity }
                : item
        ));
    };

    // Remove item
    const removeItem = (id) => {
        setItems(items.filter(item => item.id !== id));
    };

    // Calculate total
    const total = items.reduce((sum, item) =>
        sum + (item.price * item.quantity), 0
    );

    return (
        <div>
            <h2>Shopping Cart</h2>
            {items.map(item => (
                <div key={item.id}>
                    <span>{item.name} - ${item.price}</span>
                    <input
                        type="number"
                        value={item.quantity}
                        onChange={(e) => updateQuantity(item.id, +e.target.value)}
                    />
                    <button onClick={() => removeItem(item.id)}>Remove</button>
                </div>
            ))}
            <p>Total: ${total.toFixed(2)}</p>
            <button onClick={() => addItem('Orange', 1.25)}>Add Orange</button>
        </div>
    );
}
```

### There are NO Dumb Questions

**Q: Why use `useState` instead of regular variables?**
**A:** Regular variables reset on every render! State persists between renders and triggers re-renders when changed.

**Q: How many useState hooks can I have?**
**A:** As many as you want! Separate concerns into different state variables.

**Q: Should I use one big state object or multiple useState calls?**
**A:** Multiple useState for unrelated data! One for related data (like user object with name, email, age).

### Interview Checkpoint 🛑
**Interviewer:** "Why is `setState` asynchronous?"
**You:** "React batches state updates for performance. If you update state 3 times in a row, React might only render once. This means you can't rely on the state value immediately after setting it. If the next state depends on the previous one, I always use the **functional update form**: `setCount(prev => prev + 1)`."

---

## 6. Events: Handling Interactions

### Handling Events in React

```jsx
function CheckoutButton() {
    const handleCheckout = () => {
        // Real-world: Redirect to Stripe or validate cart
        alert('Redirecting to payment...');
    };

    return <button onClick={handleCheckout}>Checkout Now</button>;
}

// Inline function (for simple logic)
function CloseButton() {
    return (
        <button onClick={() => console.log('Modal closed')}>
            X
        </button>
    );
}
```

### Event Object: Getting event data

```jsx
function SearchBar() {
    const handleSubmit = (event) => {
        event.preventDefault();  // Prevent page refresh
        const query = new FormData(event.target).get('search');
        console.log('Searching for:', query);
    };

    return (
        <form onSubmit={handleSubmit}>
            <input name="search" placeholder="Search products..." />
            <button type="submit">Search</button>
        </form>
    );
}
```

### Common Events

```jsx
function Events() {
    return (
        <div>
            {/* Click events */}
            <button onClick={() => console.log('Clicked')}>Click</button>
            <button onDoubleClick={() => console.log('Double')}>Double</button>

            {/* Input events */}
            <input onChange={(e) => console.log(e.target.value)} />
            <input onFocus={() => console.log('Focused')} />
            <input onBlur={() => console.log('Blurred')} />

            {/* Form events */}
            <form onSubmit={(e) => e.preventDefault()}>
                <button type="submit">Submit</button>
            </form>

            {/* Mouse events */}
            <div
                onMouseEnter={() => console.log('Mouse enter')}
                onMouseLeave={() => console.log('Mouse leave')}
            >
                Hover me
            </div>

            {/* Keyboard events */}
            <input
                onKeyDown={(e) => console.log('Key down:', e.key)}
                onKeyUp={(e) => console.log('Key up:', e.key)}
            />
        </div>
    );
}
```

### Watch It!
⚠️ **Don't call the function directly!** `onClick={handleClick()}` calls it immediately. `onClick={handleClick}` passes the function reference.

```jsx
// Wrong:
<button onClick={handleClick()}>Click</button>  // Calls immediately!

// Right:
<button onClick={handleClick}>Click</button>  // Passes function

// If you need arguments:
<button onClick={() => handleClick('arg')}>Click</button>
```

### Passing Arguments to Event Handlers

```jsx
function List() {
    const handleDelete = (id) => {
        console.log('Delete', id);
    };

    return (
        <ul>
            <li>
                Item 1
                <button onClick={() => handleDelete(1)}>Delete</button>
            </li>
            <li>
                Item 2
                <button onClick={() => handleDelete(2)}>Delete</button>
            </li>
        </ul>
    );
}
```

### Form Handling: Controlled Components

```jsx
function LoginForm() {
    const [email, setEmail] = useState('');
    const [password, setPassword] = useState('');

    const handleSubmit = (e) => {
        e.preventDefault();
        console.log('Login:', email, password);
    };

    return (
        <form onSubmit={handleSubmit}>
            <input
                type="email"
                value={email}
                onChange={(e) => setEmail(e.target.value)}
                placeholder="Email"
            />
            <input
                type="password"
                value={password}
                onChange={(e) => setPassword(e.target.value)}
                placeholder="Password"
            />
            <button type="submit">Login</button>
        </form>
    );
}
```

### Complete Event Example

```jsx
function TodoApp() {
    const [todos, setTodos] = useState([]);
    const [input, setInput] = useState('');

    const handleSubmit = (e) => {
        e.preventDefault();
        if (input.trim()) {
            setTodos([...todos, { id: Date.now(), text: input, done: false }]);
            setInput('');
        }
    };

    const handleToggle = (id) => {
        setTodos(todos.map(todo =>
            todo.id === id ? { ...todo, done: !todo.done } : todo
        ));
    };

    const handleDelete = (id) => {
        setTodos(todos.filter(todo => todo.id !== id));
    };

    return (
        <div>
            <form onSubmit={handleSubmit}>
                <input
                    value={input}
                    onChange={(e) => setInput(e.target.value)}
                    placeholder="Add todo..."
                />
                <button type="submit">Add</button>
            </form>

            <ul>
                {todos.map(todo => (
                    <li key={todo.id}>
                        <input
                            type="checkbox"
                            checked={todo.done}
                            onChange={() => handleToggle(todo.id)}
                        />
                        <span style={{
                            textDecoration: todo.done ? 'line-through' : 'none'
                        }}>
                            {todo.text}
                        </span>
                        <button onClick={() => handleDelete(todo.id)}>Delete</button>
                    </li>
                ))}
            </ul>
        </div>
    );
}
```

### Brain Power
🧠 Why does React use `onClick` instead of `onclick` or `addEventListener`?

**Answer:** React uses a synthetic event system that wraps native events. `onClick` (camelCase) is consistent with JSX conventions and provides cross-browser compatibility automatically. React also handles event cleanup for you when components unmount.

### There are NO Dumb Questions

**Q: Should I define handlers inside the component or outside?**
**A:** Inside! Handlers often need access to state and props via closures. Define them outside only if they're pure utility functions.

**Q: What's the difference between `onChange` in React vs HTML?**
**A:** In HTML, `onchange` fires on blur. In React, `onChange` fires on every keystroke (like `oninput`). This gives you real-time control.

**Q: How do I prevent the default browser behavior?**
**A:** Call `event.preventDefault()` at the start of your handler. Common for form submissions and link clicks.

---

## 7. Conditional Rendering: Show or Hide

### If-Else with Return

```jsx
function Greeting({ isLoggedIn }) {
    if (isLoggedIn) {
        return <h1>Welcome back!</h1>;
    } else {
        return <h1>Please log in</h1>;
    }
}
```

### Ternary Operator

```jsx
function Greeting({ isLoggedIn }) {
    return (
        <h1>
            {isLoggedIn ? 'Welcome back!' : 'Please log in'}
        </h1>
    );
}
```

### Logical AND (&&)

```jsx
function Notification({ hasMessages }) {
    return (
        <div>
            {hasMessages && <p>You have new messages!</p>}
        </div>
    );
}
```

### Multiple Conditions

```jsx
function Status({ status }) {
    return (
        <div>
            {status === 'loading' && <p>Loading...</p>}
            {status === 'error' && <p>Error occurred!</p>}
            {status === 'success' && <p>Success!</p>}
        </div>
    );
}

// Or with switch
function Status({ status }) {
    let message;

    switch (status) {
        case 'loading':
            message = 'Loading...';
            break;
        case 'error':
            message = 'Error occurred!';
            break;
        case 'success':
            message = 'Success!';
            break;
        default:
            message = 'Unknown status';
    }

    return <p>{message}</p>;
}
```

### Watch It!
⚠️ **Beware of `0` with `&&`!** JavaScript's `&&` returns the first falsy value. `0 && <Component />` renders `0`, not nothing!

```jsx
// Bug: Shows "0" when count is 0
{count && <p>You have {count} items</p>}

// Fix: Use explicit boolean
{count > 0 && <p>You have {count} items</p>}
```

### Brain Power
🧠 When would you use if-else vs ternary vs `&&`?

**Answer:**
- **if-else:** When you need to return completely different components or have complex logic
- **ternary `? :`:** When you have exactly two outcomes and want inline rendering
- **`&&`:** When you want to show something OR nothing (not two alternatives)

### Complete Conditional Rendering Example

```jsx
function DataDisplay({ status, data, error }) {
    // Early returns for different states
    if (status === 'loading') {
        return <div className="skeleton">Loading...</div>;
    }

    if (status === 'error') {
        return (
            <div className="error" role="alert">
                <h3>Something went wrong</h3>
                <p>{error.message}</p>
                <button onClick={() => window.location.reload()}>Retry</button>
            </div>
        );
    }

    return (
        <div>
            {data.length > 0 ? (
                <ul>
                    {data.map(item => <li key={item.id}>{item.name}</li>)}
                </ul>
            ) : (
                <p className="empty">No items found</p>
            )}

            {data.length > 10 && <button>Show More</button>}
        </div>
    );
}
```

### There are NO Dumb Questions

**Q: Why does `{false && <Component />}` render nothing but `{0 && <Component />}` renders "0"?**
**A:** React doesn't render `false`, `null`, or `undefined`. But `0` is a valid number to display! That's why `&&` with numeric conditions is dangerous.

**Q: Can I use `switch` statements in JSX?**
**A:** Not inline, but you can use them before the return statement, or create a mapping object: `const views = { loading: <Spinner />, error: <Error /> }; return views[status];`

---

## 8. Lists & Keys: Rendering Collections

### Mapping Arrays

```jsx
function TransactionHistory() {
    const transactions = [
        { id: 'tx_123', amount: 45.99, date: '2025-03-01' },
        { id: 'tx_124', amount: 12.50, date: '2025-03-02' },
        { id: 'tx_125', amount: 120.00, date: '2025-03-05' }
    ];

    return (
        <ul className="history">
            {transactions.map((tx) => (
                <li key={tx.id}>
                    <span>{tx.date}</span>
                    <strong>${tx.amount.toFixed(2)}</strong>
                </li>
            ))}
        </ul>
    );
}
```

### Keys: Important for performance

```jsx
// Bad: Using index as key (only if list never changes)
{items.map((item, index) => <li key={index}>{item}</li>)}

// Good: Using unique ID from database
{transactions.map(tx => <li key={tx.id}>{tx.amount}</li>)}
```

### Filtering and Sorting

```jsx
function ProductList({ products, category }) {
    // Filter and sort before rendering
    const filteredProducts = products
        .filter(p => category === 'all' || p.category === category)
        .sort((a, b) => a.price - b.price);

    return (
        <ul>
            {filteredProducts.map(product => (
                <li key={product.id}>
                    {product.name} - ${product.price}
                </li>
            ))}
        </ul>
    );
}
```

### Nested Lists

```jsx
function CategoryList({ categories }) {
    return (
        <div>
            {categories.map(category => (
                <div key={category.id}>
                    <h2>{category.name}</h2>
                    <ul>
                        {category.items.map(item => (
                            <li key={item.id}>{item.name}</li>
                        ))}
                    </ul>
                </div>
            ))}
        </div>
    );
}
```

### Watch It!
⚠️ **Keys must be unique among siblings!** React uses keys to identify which items changed. Don't use array index unless the list never reorders.

### Brain Power
🧠 Why are keys so important for performance?

**Answer:** Keys help React identify which items changed, were added, or removed. Without stable keys, React might re-render the entire list instead of just the changed items. With proper keys, React can efficiently update only what's necessary.

### There are NO Dumb Questions

**Q: Can I use random numbers as keys like `Math.random()`?**
**A:** Never! Random keys change on every render, defeating the purpose. React will think every item is new and re-render everything.

**Q: When is it OK to use index as key?**
**A:** Only when: (1) the list is static and won't change, (2) items have no stable IDs, AND (3) the list won't be reordered or filtered.

---

## 9. Forms: Controlled & Uncontrolled

### Controlled Components

React state is the "single source of truth". Every keystroke updates state.

```jsx
function ContactForm() {
    const [form, setForm] = useState({ name: '', email: '', message: '' });

    const handleChange = (e) => {
        const { name, value } = e.target;
        setForm(prev => ({ ...prev, [name]: value }));
    };

    const handleSubmit = (e) => {
        e.preventDefault();
        console.log('Submitting:', form);
    };

    return (
        <form onSubmit={handleSubmit}>
            <input
                name="name"
                value={form.name}
                onChange={handleChange}
                placeholder="Name"
            />
            <input
                name="email"
                type="email"
                value={form.email}
                onChange={handleChange}
                placeholder="Email"
            />
            <textarea
                name="message"
                value={form.message}
                onChange={handleChange}
                placeholder="Message"
            />
            <button type="submit">Send</button>
        </form>
    );
}
```

### Uncontrolled Components

Use refs to access DOM values directly. Less code, but less control.

```jsx
import { useRef } from 'react';

function QuickForm() {
    const nameRef = useRef();
    const emailRef = useRef();

    const handleSubmit = (e) => {
        e.preventDefault();
        console.log({
            name: nameRef.current.value,
            email: emailRef.current.value
        });
    };

    return (
        <form onSubmit={handleSubmit}>
            <input ref={nameRef} placeholder="Name" defaultValue="" />
            <input ref={emailRef} type="email" placeholder="Email" />
            <button type="submit">Submit</button>
        </form>
    );
}
```

### React Hook Form (Industry Standard)

For complex forms, use `react-hook-form` - it's performant and handles validation.

```bash
npm install react-hook-form
```

```jsx
import { useForm } from 'react-hook-form';

function SignupForm() {
    const {
        register,
        handleSubmit,
        watch,
        formState: { errors, isSubmitting }
    } = useForm();

    const onSubmit = async (data) => {
        await submitToAPI(data);
    };

    return (
        <form onSubmit={handleSubmit(onSubmit)}>
            <input
                {...register('email', {
                    required: 'Email is required',
                    pattern: {
                        value: /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$/i,
                        message: 'Invalid email address'
                    }
                })}
                placeholder="Email"
            />
            {errors.email && <span>{errors.email.message}</span>}

            <input
                {...register('password', {
                    required: 'Password is required',
                    minLength: { value: 8, message: 'Min 8 characters' }
                })}
                type="password"
                placeholder="Password"
            />
            {errors.password && <span>{errors.password.message}</span>}

            <button type="submit" disabled={isSubmitting}>
                {isSubmitting ? 'Signing up...' : 'Sign Up'}
            </button>
        </form>
    );
}
```

### Watch It!
⚠️ **Controlled vs. Uncontrolled!** Don't mix them. If you start with `value={state}`, always use it. Switching between controlled and uncontrolled causes bugs.

### Brain Power
🧠 When should you use controlled vs uncontrolled components?

**Answer:**
- **Controlled:** When you need instant validation, conditional fields, or to transform input (e.g., uppercase). More React-like.
- **Uncontrolled:** For simple forms where you only need values on submit. Less re-renders, better performance for large forms.

### There are NO Dumb Questions

**Q: Why does react-hook-form perform better than controlled forms?**
**A:** It uses uncontrolled inputs internally (refs), so typing doesn't trigger re-renders. Only validation and submission trigger updates.

**Q: How do I handle file inputs in React?**
**A:** File inputs are always uncontrolled (you can't set their value). Use a ref or `e.target.files` to access the selected file.

**Q: Should I validate on the client, server, or both?**
**A:** Both! Client-side for UX (instant feedback). Server-side for security (client validation can be bypassed).

---

## 10. Rules of Hooks

### The Two Rules

Hooks are JavaScript functions with special rules. Break them and React breaks.

```jsx
// ✅ Rule 1: Only call hooks at the TOP LEVEL
function GoodComponent() {
    const [count, setCount] = useState(0);  // ✅ Top level
    useEffect(() => { /* ... */ }, []);     // ✅ Top level
    return <div>{count}</div>;
}

// ❌ DON'T call hooks inside conditions
function BadComponent({ isLoggedIn }) {
    if (isLoggedIn) {
        const [user, setUser] = useState(null);  // ❌ Inside condition!
    }
    return <div>...</div>;
}

// ❌ DON'T call hooks inside loops
function BadComponent({ items }) {
    for (let item of items) {
        const [selected, setSelected] = useState(false);  // ❌ Inside loop!
    }
    return <div>...</div>;
}

// ❌ DON'T call hooks after early returns
function BadComponent({ loading }) {
    if (loading) return <p>Loading...</p>;
    const [data, setData] = useState(null);  // ❌ After return!
    return <div>{data}</div>;
}
```

```jsx
// ✅ Rule 2: Only call hooks from REACT FUNCTIONS
function MyComponent() {
    const [count, setCount] = useState(0);  // ✅ React component
    return <div>{count}</div>;
}

function useCustomHook() {
    const [state, setState] = useState(0);  // ✅ Custom hook (starts with "use")
    return state;
}

// ❌ DON'T call hooks from regular functions
function regularFunction() {
    const [count, setCount] = useState(0);  // ❌ Not a component or hook!
    return count;
}
```

### Why These Rules Exist

React tracks hooks by their **call order**. If you call hooks conditionally, the order might change between renders, and React loses track.

```jsx
// First render: isLoggedIn = true
useState()  // Hook 1: user
useState()  // Hook 2: theme
useEffect() // Hook 3: effect

// Second render: isLoggedIn = false (condition skips first hook)
useState()  // Hook 1: theme (WRONG! React thinks this is user)
useEffect() // Hook 2: effect (WRONG! React thinks this is theme)
// 💥 State is now completely broken
```

### Watch It!
⚠️ **Install the ESLint plugin!** It catches hook violations automatically.

```bash
npm install eslint-plugin-react-hooks --save-dev
```

### Brain Power
🧠 How do you conditionally use a hook's result without breaking the rules?

**Answer:** Call the hook unconditionally, then use its result conditionally:

```jsx
function Profile({ userId }) {
    // ✅ Always call the hook
    const user = useUser(userId);

    // ✅ Conditionally use the result
    if (!user) return <p>Loading...</p>;

    return <h1>{user.name}</h1>;
}
```

### There are NO Dumb Questions

**Q: Why can't React just figure out hooks regardless of call order?**
**A:** React stores hook state in a simple linked list. Each hook corresponds to a position. If the order changes, hook 1 might get hook 2's state. Named hooks would solve this but add runtime overhead.

**Q: Can I call a hook inside a try-catch?**
**A:** No! `try-catch` is a control flow construct. The hook might not execute if an error occurs before it, changing call order.

### Complete Rules of Hooks Example

```jsx
import { useState, useEffect, useCallback } from 'react';

// Custom hook - follows the rules internally
function useWindowSize() {
    const [size, setSize] = useState({ width: window.innerWidth, height: window.innerHeight });

    useEffect(() => {
        const handleResize = () => {
            setSize({ width: window.innerWidth, height: window.innerHeight });
        };
        window.addEventListener('resize', handleResize);
        return () => window.removeEventListener('resize', handleResize);
    }, []);  // ✅ Hook at top level of custom hook

    return size;
}

// Component using hooks correctly
function ResponsiveGallery({ images, columns = 3 }) {
    // ✅ All hooks at the top level, always called in the same order
    const [selected, setSelected] = useState(null);
    const [page, setPage] = useState(1);
    const { width } = useWindowSize();

    // ✅ Derived value (not a hook, just computation)
    const responsiveColumns = width < 768 ? 1 : width < 1024 ? 2 : columns;
    const visibleImages = images.slice(0, page * responsiveColumns * 3);

    // ✅ useCallback at top level
    const handleSelect = useCallback((img) => {
        setSelected(img);
    }, []);

    // ✅ Conditional rendering AFTER all hooks
    if (images.length === 0) {
        return <p>No images to display</p>;
    }

    return (
        <div style={{ columns: responsiveColumns }}>
            {visibleImages.map(img => (
                <img
                    key={img.id}
                    src={img.url}
                    alt={img.alt}
                    onClick={() => handleSelect(img)}
                    style={{ outline: selected?.id === img.id ? '3px solid blue' : 'none' }}
                />
            ))}
            {visibleImages.length < images.length && (
                <button onClick={() => setPage(p => p + 1)}>Load More</button>
            )}
        </div>
    );
}
```

---

## 11. useEffect: Side Effects

### What are side effects?

Side effects are anything that affects something outside the component: fetching data, subscriptions, timers, directly manipulating DOM.

```jsx
import { useEffect } from 'react';

function LiveChat() {
    useEffect(() => {
        const connection = createConnection();
        connection.connect();

        // Cleanup: Disconnect when component unmounts
        return () => {
            connection.disconnect();
        };
    }, []); // Empty array = run once on mount

    return <div>Status: Connected</div>;
}
```

### useEffect with Dependencies

```jsx
// Runs after every render (rarely needed)
useEffect(() => {
    console.log('Component rendered');
});

// Runs once (on mount) - e.g. API call
useEffect(() => {
    fetchUserData();
}, []);

// Runs when dependencies change - e.g. Search
useEffect(() => {
    fetchSearchResults(query);
}, [query]);
```

### Cleanup: Preventing memory leaks

```jsx
useEffect(() => {
    const timer = setInterval(() => {
        console.log('Auto-saving...');
    }, 5000);

    // Cleanup function
    return () => {
        clearInterval(timer);
    };
}, []);
```

### Fetching Data with useEffect

```jsx
function ProductDetails({ productId }) {
    const [product, setProduct] = useState(null);
    const [loading, setLoading] = useState(true);
    const [error, setError] = useState(null);

    useEffect(() => {
        const controller = new AbortController();

        async function fetchProduct() {
            try {
                setLoading(true);
                const res = await fetch(`/api/products/${productId}`, {
                    signal: controller.signal
                });
                const data = await res.json();
                setProduct(data);
                setError(null);
            } catch (err) {
                if (err.name !== 'AbortError') {
                    setError(err.message);
                }
            } finally {
                setLoading(false);
            }
        }

        fetchProduct();

        return () => controller.abort();  // Cancel on unmount or productId change
    }, [productId]);

    if (loading) return <p>Loading...</p>;
    if (error) return <p>Error: {error}</p>;

    return <div>{product.name} - ${product.price}</div>;
}
```

### Watch It!
⚠️ **Missing dependencies cause stale closures!** If your effect uses a value but doesn't include it in the dependency array, you'll see stale (old) values.

```jsx
// Bug: count is always 0 inside the effect
useEffect(() => {
    const id = setInterval(() => {
        console.log(count);  // Always logs initial value!
    }, 1000);
    return () => clearInterval(id);
}, []);  // ❌ Missing count dependency

// Fix: Include count in dependencies
useEffect(() => {
    const id = setInterval(() => {
        console.log(count);  // Logs current value
    }, 1000);
    return () => clearInterval(id);
}, [count]);  // ✅ Will re-run when count changes
```

### Brain Power
🧠 What's the difference between no dependency array, empty array `[]`, and array with values `[dep]`?

**Answer:**
- **No array:** Runs after EVERY render (rarely what you want)
- **Empty `[]`:** Runs ONCE on mount (like componentDidMount)
- **`[dep]`:** Runs on mount AND whenever `dep` changes

### There are NO Dumb Questions

**Q: Why use AbortController instead of a `cancelled` flag?**
**A:** AbortController actually cancels the network request (saving bandwidth), while a flag just ignores the response. AbortController is the modern standard for fetch cancellation.

**Q: Can I use async directly in useEffect?**
**A:** No! `useEffect(() => async () => {})` is wrong because async returns a Promise, but cleanup must be a function. Define an async function inside and call it.

**Q: Should I fetch data in useEffect or use a library?**
**A:** For production, use React Query or SWR. They handle caching, deduplication, retries, and background updates. `useEffect` fetching is fine for learning but error-prone in production.

---

## 12. useRef, useLayoutEffect & useId

### useRef: Persisting Values Without Re-renders

`useRef` holds a mutable value that persists across renders but doesn't trigger re-renders when changed.

```jsx
import { useRef, useEffect } from 'react';

// Use case 1: DOM access
function TextInput() {
    const inputRef = useRef(null);

    const focusInput = () => {
        inputRef.current.focus();
    };

    return (
        <>
            <input ref={inputRef} placeholder="Click button to focus" />
            <button onClick={focusInput}>Focus Input</button>
        </>
    );
}

// Use case 2: Storing previous values
function Counter() {
    const [count, setCount] = useState(0);
    const prevCountRef = useRef();

    useEffect(() => {
        prevCountRef.current = count;  // Update ref after render
    });

    return (
        <div>
            <p>Current: {count}, Previous: {prevCountRef.current}</p>
            <button onClick={() => setCount(c => c + 1)}>+</button>
        </div>
    );
}

// Use case 3: Storing interval/timeout IDs
function Timer() {
    const intervalRef = useRef(null);
    const [seconds, setSeconds] = useState(0);

    const start = () => {
        intervalRef.current = setInterval(() => {
            setSeconds(s => s + 1);
        }, 1000);
    };

    const stop = () => {
        clearInterval(intervalRef.current);
    };

    return (
        <div>
            <p>{seconds}s</p>
            <button onClick={start}>Start</button>
            <button onClick={stop}>Stop</button>
        </div>
    );
}
```

### useLayoutEffect: Synchronous DOM Measurements

Like `useEffect`, but fires synchronously after DOM mutations and before the browser paints. Use for DOM measurements.

```jsx
import { useLayoutEffect, useRef, useState } from 'react';

function Tooltip({ children, text }) {
    const [tooltipHeight, setTooltipHeight] = useState(0);
    const tooltipRef = useRef();

    // Measure BEFORE browser paints (prevents flicker)
    useLayoutEffect(() => {
        const height = tooltipRef.current.getBoundingClientRect().height;
        setTooltipHeight(height);
    }, []);

    return (
        <div style={{ position: 'relative' }}>
            {children}
            <div
                ref={tooltipRef}
                style={{ position: 'absolute', top: -tooltipHeight }}
            >
                {text}
            </div>
        </div>
    );
}
```

### useId: Accessible Unique IDs

Generates stable unique IDs that work with server-side rendering.

```jsx
import { useId } from 'react';

function FormField({ label }) {
    const id = useId();

    return (
        <div>
            <label htmlFor={id}>{label}</label>
            <input id={id} type="text" />
        </div>
    );
}

// Multiple IDs in same component
function PasswordField() {
    const id = useId();

    return (
        <>
            <label htmlFor={`${id}-password`}>Password</label>
            <input id={`${id}-password`} type="password" />

            <label htmlFor={`${id}-confirm`}>Confirm Password</label>
            <input id={`${id}-confirm`} type="password" />
        </>
    );
}
```

### Watch It!
⚠️ **useLayoutEffect blocks the browser!** Only use it when you need to measure DOM before paint. For most effects, use `useEffect`.

### Brain Power
🧠 When would you use `useRef` instead of `useState`?

**Answer:** When you need to store a value that:
1. Persists between renders
2. Doesn't need to trigger a re-render when it changes
3. Examples: DOM refs, interval IDs, previous values, mutable values in closures

### There are NO Dumb Questions

**Q: What's the difference between `useRef` and a module-level variable?**
**A:** A module variable is shared across all instances of a component. `useRef` gives each component instance its own value.

**Q: When would I use `useLayoutEffect` over `useEffect`?**
**A:** Only when you need to measure or mutate the DOM before the browser paints. Examples: tooltips positioning, scroll restoration, animations that must not flicker.

---

## 13. Custom Hooks: Reusable Logic

### What are custom hooks?

Custom hooks are JavaScript functions that start with `use` and can call other hooks. They let you extract and share stateful logic.

```jsx
// useLocalStorage.js - Persist state to localStorage
import { useState, useEffect } from 'react';

export function useLocalStorage(key, initialValue) {
    const [value, setValue] = useState(() => {
        const stored = localStorage.getItem(key);
        return stored ? JSON.parse(stored) : initialValue;
    });

    useEffect(() => {
        localStorage.setItem(key, JSON.stringify(value));
    }, [key, value]);

    return [value, setValue];
}

// Usage
function Settings() {
    const [theme, setTheme] = useLocalStorage('theme', 'light');
    return <button onClick={() => setTheme(t => t === 'light' ? 'dark' : 'light')}>{theme}</button>;
}
```

### Common Custom Hooks

```jsx
// useToggle - Boolean state with toggle function
function useToggle(initial = false) {
    const [value, setValue] = useState(initial);
    const toggle = useCallback(() => setValue(v => !v), []);
    return [value, toggle];
}

// useFetch - Data fetching with loading/error states
function useFetch(url) {
    const [data, setData] = useState(null);
    const [loading, setLoading] = useState(true);
    const [error, setError] = useState(null);

    useEffect(() => {
        const controller = new AbortController();

        setLoading(true);
        fetch(url, { signal: controller.signal })
            .then(res => res.json())
            .then(data => setData(data))
            .catch(err => {
                if (err.name !== 'AbortError') setError(err);
            })
            .finally(() => setLoading(false));

        return () => controller.abort();
    }, [url]);

    return { data, loading, error };
}

// useDebounce - Debounce a value
function useDebounce(value, delay) {
    const [debouncedValue, setDebouncedValue] = useState(value);

    useEffect(() => {
        const timer = setTimeout(() => setDebouncedValue(value), delay);
        return () => clearTimeout(timer);
    }, [value, delay]);

    return debouncedValue;
}

// Usage
function SearchInput() {
    const [query, setQuery] = useState('');
    const debouncedQuery = useDebounce(query, 300);

    useEffect(() => {
        if (debouncedQuery) searchAPI(debouncedQuery);
    }, [debouncedQuery]);

    return <input value={query} onChange={e => setQuery(e.target.value)} />;
}
```

### Brain Power
🧠 Why must custom hooks start with "use"?

**Answer:** The `use` prefix tells React (and ESLint) that this function follows the Rules of Hooks. Without it, React can't verify that hooks are called correctly inside it.

### Watch It!
⚠️ **Custom hooks share logic, not state!** Each component that calls a custom hook gets its own isolated state. The hook code is shared, but the values are independent.

### There are NO Dumb Questions

**Q: How do I test custom hooks?**
**A:** Use `renderHook` from `@testing-library/react-hooks`. It renders your hook in isolation so you can test its return values and state updates without a full component.

**Q: Can custom hooks call other custom hooks?**
**A:** Yes! That's a major benefit. You can compose hooks together. A `useAuth` hook might use `useFetch` and `useLocalStorage` internally.

**Q: Should I put each custom hook in its own file?**
**A:** Yes, one hook per file is the convention. Name the file the same as the hook: `useLocalStorage.js`. This makes hooks easy to find and import.

---

## 14. Context: Sharing State

### The Problem: Prop Drilling

Passing props through 5+ levels of components that don't use them is painful and hard to maintain.

### Creating and Using Context

```jsx
import { createContext, useContext, useState } from 'react';

// 1. Create Context with default value
const ThemeContext = createContext('light');

// 2. Create Provider component
function ThemeProvider({ children }) {
    const [theme, setTheme] = useState('light');

    const toggleTheme = () => {
        setTheme(t => t === 'light' ? 'dark' : 'light');
    };

    return (
        <ThemeContext.Provider value={{ theme, toggleTheme }}>
            {children}
        </ThemeContext.Provider>
    );
}

// 3. Create custom hook for consuming (recommended pattern)
function useTheme() {
    const context = useContext(ThemeContext);
    if (!context) {
        throw new Error('useTheme must be used within ThemeProvider');
    }
    return context;
}

// 4. Use in components
function ThemeToggle() {
    const { theme, toggleTheme } = useTheme();
    return (
        <button onClick={toggleTheme}>
            Current: {theme}
        </button>
    );
}

// 5. Wrap app with provider
function App() {
    return (
        <ThemeProvider>
            <Header />
            <Main />
            <ThemeToggle />
        </ThemeProvider>
    );
}
```

### Multiple Contexts

```jsx
function App() {
    return (
        <AuthProvider>
            <ThemeProvider>
                <CartProvider>
                    <MyApp />
                </CartProvider>
            </ThemeProvider>
        </AuthProvider>
    );
}
```

### Watch It!
⚠️ **Context causes re-renders!** When context value changes, ALL consumers re-render. Split contexts by update frequency, or use `useMemo` for the value.

```jsx
// Problem: New object every render = all consumers re-render
<ThemeContext.Provider value={{ theme, toggleTheme }}>

// Solution: Memoize the value
const value = useMemo(() => ({ theme, toggleTheme }), [theme]);
<ThemeContext.Provider value={value}>
```

### Brain Power
🧠 When should you use Context vs Props vs State Management Libraries?

**Answer:**
- **Props:** For 1-2 levels, or when intermediate components need the data
- **Context:** For truly global data (theme, auth, locale) that changes infrequently
- **Libraries (Zustand, Redux):** For complex state with frequent updates, or when you need devtools/middleware

### There are NO Dumb Questions

**Q: Why does context cause performance issues?**
**A:** When a context value changes, ALL components consuming that context re-render - even if they only use a small part of the value. Split contexts by concern (AuthContext, ThemeContext) rather than one giant AppContext.

**Q: What's the point of the `useTheme` wrapper hook?**
**A:** It adds error checking (throws if used outside Provider) and hides the context import. Consumers just import `useTheme` instead of knowing about `ThemeContext` directly.

**Q: Can I nest providers of the same context?**
**A:** Yes! Inner providers override outer ones. A component reads from the closest Provider above it in the tree.

### Interview Checkpoint 🛑
**Interviewer:** "When would you use Context API versus a state management library like Redux or Zustand?"
**You:** "Context is great for low-frequency updates like themes, auth, or locale - data that doesn't change often. For high-frequency updates (like a shopping cart or form state), Context causes performance issues because ALL consumers re-render on any change. State management libraries like Zustand use selectors to re-render only components that use the changed slice of state. I'd use Context for 'set once, read everywhere' data, and Zustand/Redux for complex, frequently-changing state."

---

## 15. Portals: Escaping the DOM

### What are Portals?

Portals let you render children into a different part of the DOM, outside the parent component's hierarchy. Perfect for modals, tooltips, and dropdowns.

```jsx
import { createPortal } from 'react-dom';

function Modal({ isOpen, onClose, children }) {
    if (!isOpen) return null;

    return createPortal(
        <div className="modal-overlay" onClick={onClose}>
            <div className="modal-content" onClick={e => e.stopPropagation()}>
                <button className="close-btn" onClick={onClose}>×</button>
                {children}
            </div>
        </div>,
        document.getElementById('modal-root')  // Render here instead of parent
    );
}

// In your HTML:
// <div id="root"></div>
// <div id="modal-root"></div>

// Usage
function App() {
    const [showModal, setShowModal] = useState(false);

    return (
        <div>
            <button onClick={() => setShowModal(true)}>Open Modal</button>
            <Modal isOpen={showModal} onClose={() => setShowModal(false)}>
                <h2>Modal Title</h2>
                <p>Modal content here</p>
            </Modal>
        </div>
    );
}
```

### Tooltip with Portal

```jsx
function Tooltip({ children, text, targetRef }) {
    const [position, setPosition] = useState({ top: 0, left: 0 });

    useLayoutEffect(() => {
        if (targetRef.current) {
            const rect = targetRef.current.getBoundingClientRect();
            setPosition({
                top: rect.bottom + window.scrollY,
                left: rect.left + window.scrollX
            });
        }
    }, [targetRef]);

    return createPortal(
        <div
            className="tooltip"
            style={{ position: 'absolute', ...position }}
        >
            {text}
        </div>,
        document.body
    );
}
```

### Watch It!
⚠️ **Events still bubble through React's tree!** Even though the portal is rendered elsewhere in the DOM, events bubble up through the React component tree, not the DOM tree.

### Brain Power
🧠 Why use portals instead of just CSS `position: fixed`?

**Answer:** CSS solutions can be blocked by:
1. `overflow: hidden` on parent containers
2. `z-index` stacking contexts
3. CSS `transform` creating new containing blocks

Portals render outside these constraints entirely.

### There are NO Dumb Questions

**Q: Do portals break event bubbling?**
**A:** No! Events still bubble through the React component tree, not the DOM tree. A click inside a portal still triggers onClick handlers on React ancestors.

**Q: What if the portal target element doesn't exist yet?**
**A:** The portal will fail silently. Ensure the target element exists in your HTML before the component mounts. Use `document.body` as a safe fallback.

**Q: Can I use portals for tooltips and dropdowns too?**
**A:** Yes! Any UI that needs to visually "escape" its container (overflow: hidden, z-index issues) benefits from portals. Libraries like Radix and Headless UI use portals internally.

---

## 16. forwardRef & useImperativeHandle

### forwardRef: Passing Refs to Child Components

By default, refs don't pass through components. `forwardRef` lets you expose a child's DOM node to the parent.

```jsx
import { forwardRef, useRef } from 'react';

// Wrap component with forwardRef
const FancyInput = forwardRef(function FancyInput(props, ref) {
    return (
        <input
            ref={ref}
            className="fancy-input"
            {...props}
        />
    );
});

// Parent can now access the input's DOM node
function Form() {
    const inputRef = useRef();

    const focusInput = () => {
        inputRef.current.focus();
    };

    return (
        <>
            <FancyInput ref={inputRef} placeholder="Type here..." />
            <button onClick={focusInput}>Focus</button>
        </>
    );
}
```

### useImperativeHandle: Custom Ref API

Customize what the ref exposes to parent components. Useful for exposing methods instead of DOM nodes.

```jsx
import { forwardRef, useImperativeHandle, useRef } from 'react';

const VideoPlayer = forwardRef(function VideoPlayer({ src }, ref) {
    const videoRef = useRef();

    // Expose custom methods instead of the raw DOM node
    useImperativeHandle(ref, () => ({
        play() {
            videoRef.current.play();
        },
        pause() {
            videoRef.current.pause();
        },
        restart() {
            videoRef.current.currentTime = 0;
            videoRef.current.play();
        }
    }), []);

    return <video ref={videoRef} src={src} />;
});

// Parent uses the custom API
function App() {
    const playerRef = useRef();

    return (
        <>
            <VideoPlayer ref={playerRef} src="/video.mp4" />
            <button onClick={() => playerRef.current.play()}>Play</button>
            <button onClick={() => playerRef.current.pause()}>Pause</button>
            <button onClick={() => playerRef.current.restart()}>Restart</button>
        </>
    );
}
```

### Watch It!
⚠️ **Don't overuse refs!** Refs are an "escape hatch" from React's declarative model. Prefer props and state for most communication. Use refs only for imperative actions like focus, scroll, or media playback.

### Brain Power
🧠 When would you use `useImperativeHandle` instead of just forwarding the ref?

**Answer:** When you want to:
1. Hide the underlying DOM node from parents
2. Expose only specific methods (encapsulation)
3. Create a cleaner API for complex components
4. Prevent parents from doing unexpected things with the DOM node

### There are NO Dumb Questions

**Q: Do I always need forwardRef for component libraries?**
**A:** Yes, if consumers might need to access the underlying DOM node (for focus management, measurements, etc.). It's standard practice for input, button, and container components in libraries.

**Q: Is forwardRef being replaced in React 19?**
**A:** React 19 lets you pass `ref` as a regular prop, making `forwardRef` unnecessary. But `forwardRef` still works and is needed for React 18 and earlier.

**Q: Can I forward a ref through multiple levels?**
**A:** Yes, each level needs `forwardRef`. Or use context to pass the ref down without prop drilling.

---

## 17. Error Boundaries

### Catching Errors in Components

Error boundaries catch JavaScript errors in child components and display a fallback UI. They're class components (no hook equivalent yet).

```jsx
import { Component } from 'react';

class ErrorBoundary extends Component {
    constructor(props) {
        super(props);
        this.state = { hasError: false, error: null };
    }

    static getDerivedStateFromError(error) {
        return { hasError: true, error };
    }

    componentDidCatch(error, errorInfo) {
        // Log to error reporting service (Sentry, LogRocket, etc.)
        console.error('Error caught:', error, errorInfo);
    }

    render() {
        if (this.state.hasError) {
            return this.props.fallback || <h1>Something went wrong.</h1>;
        }
        return this.props.children;
    }
}

// Usage
function App() {
    return (
        <ErrorBoundary fallback={<p>Error loading user data</p>}>
            <UserProfile />
        </ErrorBoundary>
    );
}
```

### react-error-boundary (Recommended)

```bash
npm install react-error-boundary
```

```jsx
import { ErrorBoundary } from 'react-error-boundary';

function ErrorFallback({ error, resetErrorBoundary }) {
    return (
        <div role="alert">
            <h2>Something went wrong</h2>
            <pre>{error.message}</pre>
            <button onClick={resetErrorBoundary}>Try again</button>
        </div>
    );
}

function App() {
    return (
        <ErrorBoundary
            FallbackComponent={ErrorFallback}
            onReset={() => {
                // Reset app state here if needed
            }}
        >
            <MyApp />
        </ErrorBoundary>
    );
}
```

### Watch It!
⚠️ **Error boundaries don't catch:**
- Event handler errors (use try-catch)
- Async code (promises, setTimeout)
- Server-side rendering errors
- Errors in the boundary itself

```jsx
// For event handlers, use try-catch
function Button() {
    const handleClick = () => {
        try {
            riskyOperation();
        } catch (error) {
            // Handle error
        }
    };
    return <button onClick={handleClick}>Click</button>;
}
```

### Brain Power
🧠 Where should you place error boundaries in your app?

**Answer:** At strategic levels:
1. Around the entire app (catch-all)
2. Around each major route/page
3. Around risky third-party components
This way one component crashing doesn't take down the whole app.

### There are NO Dumb Questions

**Q: Why are error boundaries class components?**
**A:** There's no hook equivalent for `componentDidCatch` or `getDerivedStateFromError` yet. The `react-error-boundary` library provides a functional wrapper around this class component pattern.

**Q: How do I catch async errors (like failed fetch)?**
**A:** Error boundaries don't catch async errors. Handle those with try-catch in your async code, or use React Query which has built-in error handling.

**Q: Can I recover from errors without a full page reload?**
**A:** Yes! Use `resetErrorBoundary` (from react-error-boundary) or `resetKeys` to reset the boundary when conditions change, re-mounting the children.

---

## 18. Common Patterns

### Compound Components

Compound components work together to form a complete UI. They share implicit state through Context, giving users flexibility in composition.

```jsx
import { createContext, useContext, useState } from 'react';

// 1. Create shared context
const TabsContext = createContext();

// 2. Parent component manages state
function Tabs({ children, defaultIndex = 0 }) {
    const [activeIndex, setActiveIndex] = useState(defaultIndex);

    return (
        <TabsContext.Provider value={{ activeIndex, setActiveIndex }}>
            <div className="tabs">{children}</div>
        </TabsContext.Provider>
    );
}

// 3. Child components consume context
function TabList({ children }) {
    return <div className="tab-list" role="tablist">{children}</div>;
}

function Tab({ children, index }) {
    const { activeIndex, setActiveIndex } = useContext(TabsContext);
    const isActive = activeIndex === index;

    return (
        <button
            role="tab"
            aria-selected={isActive}
            className={isActive ? 'tab active' : 'tab'}
            onClick={() => setActiveIndex(index)}
        >
            {children}
        </button>
    );
}

function TabPanels({ children }) {
    return <div className="tab-panels">{children}</div>;
}

function TabPanel({ children, index }) {
    const { activeIndex } = useContext(TabsContext);
    if (activeIndex !== index) return null;
    return <div role="tabpanel">{children}</div>;
}

// 4. Attach child components to parent (optional but common)
Tabs.TabList = TabList;
Tabs.Tab = Tab;
Tabs.TabPanels = TabPanels;
Tabs.TabPanel = TabPanel;

// Usage - flexible composition!
function App() {
    return (
        <Tabs defaultIndex={0}>
            <Tabs.TabList>
                <Tabs.Tab index={0}>Profile</Tabs.Tab>
                <Tabs.Tab index={1}>Settings</Tabs.Tab>
                <Tabs.Tab index={2}>Billing</Tabs.Tab>
            </Tabs.TabList>

            <Tabs.TabPanels>
                <Tabs.TabPanel index={0}>
                    <h2>Profile Content</h2>
                </Tabs.TabPanel>
                <Tabs.TabPanel index={1}>
                    <h2>Settings Content</h2>
                </Tabs.TabPanel>
                <Tabs.TabPanel index={2}>
                    <h2>Billing Content</h2>
                </Tabs.TabPanel>
            </Tabs.TabPanels>
        </Tabs>
    );
}
```

### Render Props

Pass a function as a prop to share code between components. Less common with hooks, but still useful for some patterns.

```jsx
import { useState, useEffect } from 'react';

// Render prop component - shares mouse position logic
function MouseTracker({ render }) {
    const [position, setPosition] = useState({ x: 0, y: 0 });

    useEffect(() => {
        const handleMouseMove = (e) => {
            setPosition({ x: e.clientX, y: e.clientY });
        };

        window.addEventListener('mousemove', handleMouseMove);
        return () => window.removeEventListener('mousemove', handleMouseMove);
    }, []);

    // Call the render prop with the state
    return render(position);
}

// Usage - consumer decides how to render
function App() {
    return (
        <div>
            {/* Render as text */}
            <MouseTracker
                render={({ x, y }) => (
                    <p>Mouse position: ({x}, {y})</p>
                )}
            />

            {/* Render as a following element */}
            <MouseTracker
                render={({ x, y }) => (
                    <div
                        style={{
                            position: 'fixed',
                            left: x + 10,
                            top: y + 10,
                            background: 'black',
                            color: 'white',
                            padding: '4px 8px',
                            borderRadius: '4px'
                        }}
                    >
                        Cursor tooltip
                    </div>
                )}
            />
        </div>
    );
}

// Alternative: "children as a function" pattern
function DataFetcher({ url, children }) {
    const [data, setData] = useState(null);
    const [loading, setLoading] = useState(true);

    useEffect(() => {
        fetch(url)
            .then(res => res.json())
            .then(data => {
                setData(data);
                setLoading(false);
            });
    }, [url]);

    return children({ data, loading });
}

// Usage
<DataFetcher url="/api/users">
    {({ data, loading }) =>
        loading ? <Spinner /> : <UserList users={data} />
    }
</DataFetcher>
```

### Higher-Order Components (HOCs)

HOCs are functions that take a component and return an enhanced component. Common in older codebases.

```jsx
import { useState, useEffect } from 'react';

// HOC that adds loading state
function withLoading(WrappedComponent) {
    return function WithLoadingComponent({ isLoading, ...props }) {
        if (isLoading) {
            return <div className="spinner">Loading...</div>;
        }
        return <WrappedComponent {...props} />;
    };
}

// HOC that adds authentication check
function withAuth(WrappedComponent) {
    return function WithAuthComponent(props) {
        const [user, setUser] = useState(null);
        const [checking, setChecking] = useState(true);

        useEffect(() => {
            checkAuth().then(user => {
                setUser(user);
                setChecking(false);
            });
        }, []);

        if (checking) return <div>Checking auth...</div>;
        if (!user) return <Navigate to="/login" />;

        return <WrappedComponent {...props} user={user} />;
    };
}

// HOC that adds logging
function withLogging(WrappedComponent) {
    function WithLoggingComponent(props) {
        useEffect(() => {
            console.log(`${WrappedComponent.name} mounted`);
            return () => console.log(`${WrappedComponent.name} unmounted`);
        }, []);

        return <WrappedComponent {...props} />;
    }

    // Important: Set displayName for DevTools
    WithLoggingComponent.displayName =
        `WithLogging(${WrappedComponent.displayName || WrappedComponent.name})`;

    return WithLoggingComponent;
}

// Usage
function Dashboard({ user }) {
    return <h1>Welcome, {user.name}</h1>;
}

// Compose HOCs (read right to left: withAuth runs first)
const EnhancedDashboard = withLogging(withAuth(Dashboard));

// In your app
<EnhancedDashboard />
```

### Watch It!
⚠️ **HOCs have downsides!** They can cause "wrapper hell," make debugging harder (anonymous components), and have issues with refs. Prefer hooks for new code - most HOC patterns can be replaced with custom hooks.

```jsx
// Instead of withLoading HOC, use a custom hook
function useLoading(asyncFn) {
    const [loading, setLoading] = useState(false);
    const [error, setError] = useState(null);

    const execute = async (...args) => {
        setLoading(true);
        try {
            const result = await asyncFn(...args);
            return result;
        } catch (err) {
            setError(err);
        } finally {
            setLoading(false);
        }
    };

    return { loading, error, execute };
}
```

### Brain Power
🧠 When would you still use a HOC instead of a hook?

**Answer:** HOCs are useful when you need to:
1. Wrap a component you don't control (third-party library)
2. Add behavior that requires wrapping JSX (like error boundaries)
3. Work with class components that can't use hooks
4. Maintain legacy codebases that already use HOC patterns

For new code, custom hooks are almost always better.

### There are NO Dumb Questions

**Q: What's the difference between compound components and render props?**
**A:** Compound components share state implicitly via Context - users arrange predefined child components. Render props share state explicitly via function - users have complete control over rendering. Compound components are more declarative; render props are more flexible.

**Q: Can I use both patterns together?**
**A:** Yes! Many libraries do. For example, a Tabs compound component might also accept a render prop for custom tab rendering: `<Tab render={({ isActive }) => ...} />`.

**Q: Why do HOCs need displayName?**
**A:** Without displayName, React DevTools shows HOC wrappers as "Unknown" or "Anonymous," making debugging difficult. Always set displayName to `WithXxx(ComponentName)` format.

### Interview Checkpoint 🛑
**Interviewer:** "Explain the compound component pattern and when you'd use it."
**You:** "Compound components are a set of components that work together, sharing implicit state through Context. Think of `<select>` and `<option>` - they're separate elements but work as one unit. I'd use this pattern for complex UI widgets like tabs, accordions, or menus where users need flexibility in composition but components need to coordinate. The parent manages state, children consume it via Context, and users get a clean declarative API."

---

## 19. Routing: Navigation

### React Router Setup

```bash
npm install react-router-dom
```

```jsx
import {
    BrowserRouter,
    Routes,
    Route,
    Link,
    NavLink,
    Navigate,
    Outlet
} from 'react-router-dom';

function App() {
    return (
        <BrowserRouter>
            <nav>
                <NavLink to="/" className={({ isActive }) => isActive ? 'active' : ''}>
                    Home
                </NavLink>
                <NavLink to="/products">Products</NavLink>
                <NavLink to="/about">About</NavLink>
            </nav>

            <Routes>
                <Route path="/" element={<Home />} />
                <Route path="/products" element={<Products />} />
                <Route path="/products/:id" element={<ProductDetail />} />
                <Route path="/about" element={<About />} />
                <Route path="*" element={<NotFound />} />
            </Routes>
        </BrowserRouter>
    );
}
```

### Router Hooks

```jsx
import {
    useParams,
    useNavigate,
    useLocation,
    useSearchParams
} from 'react-router-dom';

function ProductDetail() {
    // Get URL params (/products/:id)
    const { id } = useParams();

    // Programmatic navigation
    const navigate = useNavigate();

    // Current location object
    const location = useLocation();  // { pathname, search, hash, state }

    // Query string params (?sort=price&page=1)
    const [searchParams, setSearchParams] = useSearchParams();
    const sort = searchParams.get('sort');
    const page = searchParams.get('page');

    return (
        <div>
            <h1>Product {id}</h1>
            <p>Sort: {sort}, Page: {page}</p>

            <button onClick={() => navigate('/products')}>
                Back to Products
            </button>

            <button onClick={() => navigate(-1)}>
                Go Back
            </button>

            <button onClick={() => setSearchParams({ sort: 'name', page: '2' })}>
                Change Filters
            </button>
        </div>
    );
}
```

### Nested Routes & Layouts

```jsx
function App() {
    return (
        <Routes>
            <Route path="/" element={<Layout />}>
                <Route index element={<Home />} />
                <Route path="products" element={<Products />} />
                <Route path="products/:id" element={<ProductDetail />} />
            </Route>
            <Route path="/login" element={<Login />} />
        </Routes>
    );
}

function Layout() {
    return (
        <div>
            <Header />
            <main>
                <Outlet />  {/* Child routes render here */}
            </main>
            <Footer />
        </div>
    );
}
```

### Protected Routes

```jsx
function ProtectedRoute({ children }) {
    const { user } = useAuth();
    const location = useLocation();

    if (!user) {
        return <Navigate to="/login" state={{ from: location }} replace />;
    }

    return children;
}

// Usage
<Route
    path="/dashboard"
    element={
        <ProtectedRoute>
            <Dashboard />
        </ProtectedRoute>
    }
/>
```

### URL State: Syncing State with the URL

Store filter/sort/pagination state in the URL for shareable links and back button support.

```jsx
import { useSearchParams } from 'react-router-dom';

function ProductFilters() {
    const [searchParams, setSearchParams] = useSearchParams();

    // Read state from URL
    const category = searchParams.get('category') || 'all';
    const sort = searchParams.get('sort') || 'popular';
    const page = parseInt(searchParams.get('page') || '1', 10);

    // Update URL (replaces state management for these values!)
    const setCategory = (newCategory) => {
        setSearchParams(prev => {
            prev.set('category', newCategory);
            prev.set('page', '1');  // Reset page on category change
            return prev;
        });
    };

    const setSort = (newSort) => {
        setSearchParams(prev => {
            prev.set('sort', newSort);
            return prev;
        });
    };

    const setPage = (newPage) => {
        setSearchParams(prev => {
            prev.set('page', String(newPage));
            return prev;
        });
    };

    return (
        <div>
            <select value={category} onChange={e => setCategory(e.target.value)}>
                <option value="all">All</option>
                <option value="electronics">Electronics</option>
                <option value="clothing">Clothing</option>
            </select>

            <select value={sort} onChange={e => setSort(e.target.value)}>
                <option value="popular">Popular</option>
                <option value="price-low">Price: Low to High</option>
                <option value="price-high">Price: High to Low</option>
            </select>

            <ProductList category={category} sort={sort} page={page} />

            <Pagination page={page} onPageChange={setPage} />
        </div>
    );
}

// URL looks like: /products?category=electronics&sort=price-low&page=2
// Users can bookmark, share, and use back/forward buttons!
```

**When to use URL state:**
- Filters, sorting, pagination
- Search queries
- Tab selection
- Any state users might want to bookmark or share

### Watch It!
⚠️ **Never call `navigate()` during render!** Calling it unconditionally in a component body causes infinite loops. Use it inside event handlers or `useEffect`. For declarative redirects, use the `<Navigate>` component instead.

### Brain Power
🧠 Why use `<Link>` or `<NavLink>` instead of `<a href>`?

**Answer:** `<a>` causes a full page reload. `<Link>` uses JavaScript to update the URL and swap components without reloading - that's what makes it a Single Page Application (SPA).

### There are NO Dumb Questions

**Q: How do I pass data between routes?**
**A:** Use URL params (`:id`), search params (`?key=value`), or the `state` prop on `<Navigate>` / `navigate()` for data that shouldn't be in the URL.

**Q: What's the difference between `<Navigate>` and `navigate()`?**
**A:** `<Navigate>` is a component for declarative redirects (render it to redirect). `navigate()` is imperative (call it in event handlers or effects).

**Q: How do I handle 404 pages?**
**A:** Add a catch-all route with `path="*"` as the last route. It matches any URL that doesn't match earlier routes.

---

## 20. API Calls: Fetching Data

### React Query (TanStack Query)

Don't use `useEffect` for data fetching in production. Use React Query for caching, retries, background updates, and loading states.

```bash
npm install @tanstack/react-query
```

```jsx
import { QueryClient, QueryClientProvider, useQuery, useMutation, useQueryClient } from '@tanstack/react-query';

// Setup
const queryClient = new QueryClient();

function App() {
    return (
        <QueryClientProvider client={queryClient}>
            <UserList />
        </QueryClientProvider>
    );
}

// Fetching data
function UserList() {
    const { data, isLoading, error, refetch } = useQuery({
        queryKey: ['users'],
        queryFn: () => fetch('/api/users').then(res => res.json()),
        staleTime: 5 * 60 * 1000,  // Data is fresh for 5 minutes
    });

    if (isLoading) return <p>Loading...</p>;
    if (error) return <p>Error: {error.message}</p>;

    return (
        <ul>
            {data.map(user => <li key={user.id}>{user.name}</li>)}
            <button onClick={() => refetch()}>Refresh</button>
        </ul>
    );
}

// Mutations (POST, PUT, DELETE)
function AddUser() {
    const queryClient = useQueryClient();

    const mutation = useMutation({
        mutationFn: (newUser) => fetch('/api/users', {
            method: 'POST',
            body: JSON.stringify(newUser)
        }),
        onSuccess: () => {
            // Invalidate and refetch users list
            queryClient.invalidateQueries({ queryKey: ['users'] });
        }
    });

    return (
        <button
            onClick={() => mutation.mutate({ name: 'New User' })}
            disabled={mutation.isPending}
        >
            {mutation.isPending ? 'Adding...' : 'Add User'}
        </button>
    );
}
```

### Watch It!
⚠️ **Avoid Fetch Waterfalls!** Don't fetch user, wait, then fetch posts. Fetch in parallel:

```jsx
// Bad: Sequential (waterfall)
const user = await fetchUser(id);
const posts = await fetchPosts(user.id);

// Good: Parallel
const [user, posts] = await Promise.all([
    fetchUser(id),
    fetchPosts(id)
]);
```

### Brain Power
🧠 Why use React Query instead of useEffect for fetching?

**Answer:** React Query handles: caching, background updates, deduplication, retry logic, loading/error states, pagination, optimistic updates, and garbage collection. Building this yourself is error-prone and time-consuming.

### There are NO Dumb Questions

**Q: Do I still need useEffect for fetching if I use React Query?**
**A:** No! React Query replaces the useEffect + useState pattern entirely. It manages loading, error, and data states internally.

**Q: What does `staleTime` actually do?**
**A:** It controls how long data is considered "fresh." During this period, React Query returns cached data instantly without refetching. After staleTime, data is refetched in the background on the next access.

**Q: How do I handle authentication headers?**
**A:** Set default headers in the `queryFn` or configure a global fetch wrapper. React Query doesn't manage headers - it just calls your fetch function.

---

## 21. State Management: Zustand

### Why Zustand?

Context API re-renders all consumers. Redux has boilerplate. Zustand is simple, fast, and scales well.

```bash
npm install zustand
```

### Basic Store

```jsx
import { create } from 'zustand';

// Create store
const useStore = create((set, get) => ({
    // State
    count: 0,
    user: null,

    // Actions
    increment: () => set((state) => ({ count: state.count + 1 })),
    decrement: () => set((state) => ({ count: state.count - 1 })),
    setUser: (user) => set({ user }),

    // Computed / derived (use get())
    doubleCount: () => get().count * 2,
}));

// Use in components
function Counter() {
    const count = useStore((state) => state.count);
    const increment = useStore((state) => state.increment);

    return <button onClick={increment}>Count: {count}</button>;
}

// Or destructure multiple values
function UserProfile() {
    const { user, setUser } = useStore();

    return user ? <p>{user.name}</p> : <p>Not logged in</p>;
}
```

### Persisting State

```jsx
import { persist } from 'zustand/middleware';

const useStore = create(
    persist(
        (set) => ({
            theme: 'light',
            setTheme: (theme) => set({ theme }),
        }),
        {
            name: 'app-storage',  // localStorage key
        }
    )
);
```

### Watch It!
⚠️ **Select only what you need!** Selecting the whole store causes re-renders on ANY change:

```jsx
// Bad: Re-renders when ANY state changes
const state = useStore();

// Good: Only re-renders when count changes
const count = useStore((state) => state.count);
```

### Brain Power
🧠 Why does Zustand use selectors instead of returning the whole store?

**Answer:** Zustand uses object reference equality to decide re-renders. If you select the whole store, ANY change triggers a re-render. Selectors let each component subscribe to only the slice it needs.

### There are NO Dumb Questions

**Q: How is Zustand different from Redux?**
**A:** Zustand has no boilerplate (no reducers, actions, dispatch). You mutate state directly with `set()`. No Provider needed - stores are global by default.

**Q: Can I use Zustand with TypeScript?**
**A:** Yes, it has excellent TypeScript support. Type your store: `create<StoreType>()((set) => ({ ... }))`.

**Q: How do I access the store outside React components?**
**A:** Call `useStore.getState()` or `useStore.setState()` directly. Unlike Context, Zustand stores work outside the React tree.

---

## 22. Performance: memo, useMemo, useCallback

### React.memo: Memoize Components

Prevents re-renders when props haven't changed.

```jsx
import { memo } from 'react';

const ExpensiveList = memo(function ExpensiveList({ items, onSelect }) {
    console.log('ExpensiveList rendered');
    return (
        <ul>
            {items.map(item => (
                <li key={item.id} onClick={() => onSelect(item.id)}>
                    {item.name}
                </li>
            ))}
        </ul>
    );
});
```

### useMemo: Memoize Values

Caches expensive calculations.

```jsx
const sortedItems = useMemo(() => {
    console.log('Sorting items...');
    return [...items].sort((a, b) => a.name.localeCompare(b.name));
}, [items]);  // Only recalculate when items change
```

### useCallback: Memoize Functions

Prevents function recreation, preserving referential equality.

```jsx
const handleSelect = useCallback((id) => {
    setSelectedId(id);
}, []);  // Stable reference across renders
```

### The Optimization Pattern

```jsx
import { useState, useMemo, useCallback, memo } from 'react';

function ProductPage() {
    const [filter, setFilter] = useState('');
    const [cart, setCart] = useState([]);

    // Memoize filtered products
    const filteredProducts = useMemo(() =>
        products.filter(p => p.name.includes(filter)),
        [products, filter]
    );

    // Memoize callback
    const addToCart = useCallback((product) => {
        setCart(c => [...c, product]);
    }, []);

    return (
        <>
            <input value={filter} onChange={e => setFilter(e.target.value)} />
            <ProductList items={filteredProducts} onAdd={addToCart} />
        </>
    );
}

// Memoized child - won't re-render unless props change
const ProductList = memo(function ProductList({ items, onAdd }) {
    return items.map(item => (
        <div key={item.id}>
            {item.name}
            <button onClick={() => onAdd(item)}>Add</button>
        </div>
    ));
});
```

### Watch It!
⚠️ **Don't optimize prematurely!** Memoization has costs (memory, complexity). Only optimize when you have actual performance problems. Use React DevTools Profiler to find slow renders.

### Brain Power
🧠 Why must you combine `memo` with `useCallback`/`useMemo` for them to work?

**Answer:** `memo` does a shallow comparison of props. If a parent re-renders and creates a new function or object (which happens every render), the prop reference changes and `memo` re-renders anyway. `useCallback`/`useMemo` preserve references.

### There are NO Dumb Questions

**Q: When should I NOT use memo?**
**A:** When props change on almost every render anyway, when the component is cheap to render, or when the component accepts `children` (children are always a new reference).

**Q: What's the difference between useMemo and useCallback?**
**A:** `useMemo` memoizes a computed value. `useCallback` memoizes a function. `useCallback(fn, deps)` is equivalent to `useMemo(() => fn, deps)`.

**Q: Does React.memo do a deep comparison?**
**A:** No, shallow only (compares prop references). For deep comparison, pass a custom `areEqual` function as the second argument to `memo()`, but this can be expensive.

### Interview Checkpoint 🛑
**Interviewer:** "A component is re-rendering too often. How would you debug and fix it?"
**You:** "First, I'd use React DevTools Profiler to identify which components are slow and why they're re-rendering. Common causes are: (1) parent re-rendering - fix with `React.memo`, (2) new object/function props every render - fix with `useMemo`/`useCallback`, (3) context changes - fix by splitting contexts or using selectors. I'd only add memoization after confirming there's a real performance problem - premature optimization adds complexity without benefit."

---

## 23. useReducer: Complex State

### When useState Isn't Enough

Use `useReducer` when state logic is complex or involves multiple sub-values.

```jsx
import { useReducer, useState } from 'react';

// Reducer function (pure, no side effects)
function todoReducer(state, action) {
    switch (action.type) {
        case 'ADD':
            return [...state, {
                id: Date.now(),
                text: action.text,
                completed: false
            }];
        case 'TOGGLE':
            return state.map(todo =>
                todo.id === action.id
                    ? { ...todo, completed: !todo.completed }
                    : todo
            );
        case 'DELETE':
            return state.filter(todo => todo.id !== action.id);
        case 'CLEAR_COMPLETED':
            return state.filter(todo => !todo.completed);
        default:
            return state;
    }
}

function TodoApp() {
    const [todos, dispatch] = useReducer(todoReducer, []);
    const [input, setInput] = useState('');

    const handleSubmit = (e) => {
        e.preventDefault();
        if (input.trim()) {
            dispatch({ type: 'ADD', text: input });
            setInput('');
        }
    };

    return (
        <div>
            <form onSubmit={handleSubmit}>
                <input value={input} onChange={e => setInput(e.target.value)} />
                <button type="submit">Add</button>
            </form>

            <ul>
                {todos.map(todo => (
                    <li key={todo.id}>
                        <span
                            style={{ textDecoration: todo.completed ? 'line-through' : 'none' }}
                            onClick={() => dispatch({ type: 'TOGGLE', id: todo.id })}
                        >
                            {todo.text}
                        </span>
                        <button onClick={() => dispatch({ type: 'DELETE', id: todo.id })}>×</button>
                    </li>
                ))}
            </ul>

            <button onClick={() => dispatch({ type: 'CLEAR_COMPLETED' })}>
                Clear Completed
            </button>
        </div>
    );
}
```

### Watch It!
⚠️ **Never mutate state in your reducer!** Always return a new object/array. `state.push(item)` mutates - use `[...state, item]` instead. Reducers must be pure functions: same input = same output, no side effects.

### Brain Power
🧠 When should you use `useReducer` vs `useState`?

**Answer:**
- **useState:** Simple values, independent updates, few state variables
- **useReducer:** Complex objects, related state changes, state machine logic, when next state depends on previous

### There are NO Dumb Questions

**Q: Can I use useReducer with Context for global state?**
**A:** Yes! `useReducer` + Context is a lightweight Redux alternative. Put the reducer in a Provider and pass `dispatch` through context. But for complex apps, Zustand is simpler.

**Q: Should my reducer handle async logic?**
**A:** No! Reducers must be pure functions. Handle async logic outside the reducer (in event handlers or effects), then dispatch the result.

**Q: What's the `default` case for?**
**A:** It catches unrecognized action types. Return the current state unchanged. In TypeScript, you can use `never` to ensure exhaustive matching.

### Interview Checkpoint 🛑
**Interviewer:** "When would you choose useReducer over useState?"
**You:** "I use `useReducer` when: (1) state updates depend on previous state in complex ways, (2) multiple state values change together (like a form with validation), (3) the state logic is complex enough to benefit from a named action pattern, or (4) I want to extract state logic for testing. For simple counters or toggles, `useState` is cleaner. A good rule: if your `setState` calls are getting complicated with spread operators and conditionals, it's time for `useReducer`."

---

## 24. Code Splitting & Lazy Loading

### React.lazy: Load Components On Demand

```jsx
import { lazy, Suspense } from 'react';

// Instead of: import Dashboard from './Dashboard';
const Dashboard = lazy(() => import('./Dashboard'));
const Settings = lazy(() => import('./Settings'));

function App() {
    return (
        <Suspense fallback={<div>Loading...</div>}>
            <Routes>
                <Route path="/" element={<Home />} />
                <Route path="/dashboard" element={<Dashboard />} />
                <Route path="/settings" element={<Settings />} />
            </Routes>
        </Suspense>
    );
}
```

### Route-Based Splitting

```jsx
const routes = [
    { path: '/', component: lazy(() => import('./pages/Home')) },
    { path: '/products', component: lazy(() => import('./pages/Products')) },
    { path: '/checkout', component: lazy(() => import('./pages/Checkout')) },
];

function App() {
    return (
        <Suspense fallback={<PageLoader />}>
            <Routes>
                {routes.map(({ path, component: Component }) => (
                    <Route key={path} path={path} element={<Component />} />
                ))}
            </Routes>
        </Suspense>
    );
}
```

### Named Exports with Lazy

```jsx
// For named exports, create an intermediate module
// Dashboard.lazy.js
export { Dashboard as default } from './Dashboard';

// App.jsx
const Dashboard = lazy(() => import('./Dashboard.lazy'));
```

### Watch It!
⚠️ **Don't lazy load everything!** Only split large components or routes that aren't needed immediately. Over-splitting creates too many network requests.

### Brain Power
🧠 Where is the best place to put Suspense boundaries?

**Answer:** Around route-level components (each page loads independently) and around expensive below-the-fold components. The fallback UI replaces everything inside the boundary, so don't wrap too much or too little.

### There are NO Dumb Questions

**Q: What happens if the lazy-loaded chunk fails to download?**
**A:** The Suspense boundary throws an error, which can be caught by an Error Boundary above it. Combine them for a robust loading pattern.

**Q: Can I prefetch lazy components?**
**A:** Yes! Call the import function early: `const preload = () => import('./Dashboard')`. Trigger it on hover or route change for instant navigation.

**Q: Does React.lazy work with Server-Side Rendering?**
**A:** Not directly. For SSR, use framework-specific solutions like Next.js `dynamic()` or `@loadable/component`.

---

## 25. React 18+ Features

### useTransition: Non-Blocking Updates

Mark state updates as low-priority so the UI stays responsive.

```jsx
import { useTransition, useState } from 'react';

function SearchResults() {
    const [query, setQuery] = useState('');
    const [results, setResults] = useState([]);
    const [isPending, startTransition] = useTransition();

    const handleChange = (e) => {
        // Urgent: Update input immediately
        setQuery(e.target.value);

        // Non-urgent: Can be interrupted
        startTransition(() => {
            setResults(filterLargeList(e.target.value));
        });
    };

    return (
        <div>
            <input value={query} onChange={handleChange} />
            {isPending && <span>Updating...</span>}
            <ul>
                {results.map(item => <li key={item.id}>{item.name}</li>)}
            </ul>
        </div>
    );
}
```

### useDeferredValue: Deferred Rendering

Defer re-rendering of a value until more urgent updates are done.

```jsx
import { useDeferredValue, useState } from 'react';

function SearchResults({ query }) {
    // Defers the value - UI stays responsive while filtering
    const deferredQuery = useDeferredValue(query);
    const isStale = query !== deferredQuery;

    const results = filterLargeList(deferredQuery);

    return (
        <ul style={{ opacity: isStale ? 0.5 : 1 }}>
            {results.map(item => <li key={item.id}>{item.name}</li>)}
        </ul>
    );
}
```

### Suspense for Data Fetching

Show fallback UI while waiting for data (works with React Query, Relay, etc.).

```jsx
import { Suspense } from 'react';

function App() {
    return (
        <Suspense fallback={<LoadingSpinner />}>
            <UserProfile />
        </Suspense>
    );
}

// UserProfile uses a Suspense-enabled data source
function UserProfile() {
    const user = useSuspenseQuery(['user'], fetchUser); // React Query example
    return <h1>{user.name}</h1>;
}
```

### React 19 Features

#### use() Hook: Reading Resources in Render

```jsx
import { use, Suspense } from 'react';

// Read a promise directly during render
function UserProfile({ userPromise }) {
    const user = use(userPromise);  // Suspends until resolved
    return <h1>{user.name}</h1>;
}

// Read context conditionally (unlike useContext!)
function Theme({ showTheme }) {
    if (showTheme) {
        const theme = use(ThemeContext);  // Can be called conditionally!
        return <p>Theme: {theme}</p>;
    }
    return null;
}

// Usage with Suspense
function App() {
    const userPromise = fetchUser(1);  // Start fetching

    return (
        <Suspense fallback={<p>Loading...</p>}>
            <UserProfile userPromise={userPromise} />
        </Suspense>
    );
}
```

#### Server Actions & useActionState

```jsx
'use client';

import { useActionState } from 'react';

// Server Action (defined with 'use server')
async function submitForm(previousState, formData) {
    'use server';
    const name = formData.get('name');

    if (!name) return { error: 'Name is required' };

    await saveToDatabase({ name });
    return { success: true, message: `Saved ${name}` };
}

function ContactForm() {
    const [state, formAction, isPending] = useActionState(submitForm, null);

    return (
        <form action={formAction}>
            <input name="name" placeholder="Your name" />
            <button type="submit" disabled={isPending}>
                {isPending ? 'Saving...' : 'Submit'}
            </button>
            {state?.error && <p className="error">{state.error}</p>}
            {state?.success && <p className="success">{state.message}</p>}
        </form>
    );
}
```

#### useOptimistic: Optimistic UI Updates

```jsx
import { useOptimistic } from 'react';

function TodoList({ todos, addTodo }) {
    const [optimisticTodos, addOptimistic] = useOptimistic(
        todos,
        (currentTodos, newTodo) => [...currentTodos, { ...newTodo, pending: true }]
    );

    async function handleSubmit(formData) {
        const newTodo = { text: formData.get('text'), id: Date.now() };
        addOptimistic(newTodo);  // Show immediately
        await addTodo(newTodo);  // Actually save
    }

    return (
        <div>
            <form action={handleSubmit}>
                <input name="text" />
                <button type="submit">Add</button>
            </form>
            <ul>
                {optimisticTodos.map(todo => (
                    <li key={todo.id} style={{ opacity: todo.pending ? 0.5 : 1 }}>
                        {todo.text}
                    </li>
                ))}
            </ul>
        </div>
    );
}
```

#### useFormStatus: Form Pending State in Children

Access form submission state from any child component without prop drilling.

```jsx
'use client';

import { useFormStatus } from 'react-dom';

// Child component that needs to know form state
function SubmitButton() {
    const { pending, data, method, action } = useFormStatus();

    return (
        <button type="submit" disabled={pending}>
            {pending ? 'Submitting...' : 'Submit'}
        </button>
    );
}

// Progress indicator anywhere in the form
function FormProgress() {
    const { pending } = useFormStatus();
    return pending ? <div className="spinner" /> : null;
}

// Parent form component
function ContactForm({ submitAction }) {
    return (
        <form action={submitAction}>
            <input name="email" type="email" placeholder="Email" required />
            <textarea name="message" placeholder="Message" required />
            <FormProgress />
            <SubmitButton />
        </form>
    );
}
```

#### React Compiler (React Forget)

React Compiler automatically memoizes your components - no more manual `useMemo`, `useCallback`, or `memo`.

```jsx
// Before React Compiler: Manual memoization
function ProductList({ products, onSelect }) {
    const sortedProducts = useMemo(() =>
        [...products].sort((a, b) => a.name.localeCompare(b.name)),
        [products]
    );

    const handleSelect = useCallback((id) => {
        onSelect(id);
    }, [onSelect]);

    return <MemoizedList items={sortedProducts} onSelect={handleSelect} />;
}

// After React Compiler: Just write normal code!
function ProductList({ products, onSelect }) {
    const sortedProducts = [...products].sort((a, b) =>
        a.name.localeCompare(b.name)
    );

    const handleSelect = (id) => {
        onSelect(id);
    };

    // Compiler automatically optimizes re-renders
    return <List items={sortedProducts} onSelect={handleSelect} />;
}
```

**Status:** React Compiler is in beta (as of early 2025). It's used in production at Meta. To try it: `npm install babel-plugin-react-compiler`.

#### Advanced use() Patterns

```jsx
import { use, Suspense } from 'react';

// Pattern 1: Error handling with use()
function UserProfile({ userPromise }) {
    try {
        const user = use(userPromise);
        return <h1>{user.name}</h1>;
    } catch (error) {
        // Caught by nearest error boundary
        throw error;
    }
}

// Pattern 2: Multiple resources in sequence
function Dashboard({ userPromise }) {
    const user = use(userPromise);

    // Can use resolved value to create dependent promise
    const postsPromise = fetchPosts(user.id);
    const posts = use(postsPromise);

    return (
        <div>
            <h1>{user.name}'s Dashboard</h1>
            <ul>{posts.map(p => <li key={p.id}>{p.title}</li>)}</ul>
        </div>
    );
}

// Pattern 3: Conditional context reading (impossible with useContext!)
function ThemeDisplay({ showTheme }) {
    if (!showTheme) {
        return <p>Theme hidden</p>;
    }

    // use() can be called conditionally!
    const theme = use(ThemeContext);
    return <p>Current theme: {theme}</p>;
}

// Pattern 4: Promise caching (important!)
function App() {
    // Create promise OUTSIDE component or in useMemo
    // Otherwise, new promise on every render = infinite loop!
    const userPromise = useMemo(() => fetchUser(1), []);

    return (
        <Suspense fallback={<p>Loading...</p>}>
            <UserProfile userPromise={userPromise} />
        </Suspense>
    );
}
```

### Watch It!
⚠️ **Don't wrap everything in `startTransition`!** Only use it for expensive, non-urgent updates (filtering large lists, complex re-renders). Wrapping simple state updates adds overhead without benefit. If the update is fast, just use regular `setState`.

### Brain Power
🧠 When should you use `useTransition` vs `useDeferredValue`?
**Answer:** Use `useTransition` when you control the state update (wrapping `setState`). Use `useDeferredValue` when you receive a value as a prop and want to defer rendering based on it.

### There are NO Dumb Questions

**Q: What's the difference between `use()` and `useContext()`?**
**A:** `use()` can be called conditionally (inside if/loops), while `useContext()` must follow the Rules of Hooks. `use()` also works with promises, not just context.

**Q: Do I need a framework for Server Actions?**
**A:** Yes, currently. Server Actions require a bundler that supports the `'use server'` directive (Next.js 14+, or a custom setup with React's bundler plugins).

**Q: Why is `useFormStatus` a separate hook from `useActionState`?**
**A:** They serve different purposes! `useActionState` manages the form's action and state at the form level. `useFormStatus` lets any nested child component access the pending state without prop drilling. This separation follows React's composition model.

**Q: When will React Compiler be stable?**
**A:** React Compiler is in beta and used in production at Meta. It's expected to become the default in future React versions. You can try it now with the Babel plugin, but it's optional - your existing code will continue to work.

---

## 26. TypeScript with React

### Why TypeScript?

TypeScript catches bugs at compile time, provides better IDE support, and makes refactoring safer.

### Typing Props

```tsx
// Basic props
interface ButtonProps {
    text: string;
    onClick: () => void;
    disabled?: boolean;  // Optional
}

function Button({ text, onClick, disabled = false }: ButtonProps) {
    return <button onClick={onClick} disabled={disabled}>{text}</button>;
}

// Props with children
interface CardProps {
    title: string;
    children: React.ReactNode;
}

function Card({ title, children }: CardProps) {
    return (
        <div>
            <h2>{title}</h2>
            {children}
        </div>
    );
}
```

### Typing State

```tsx
// Primitive state - inferred
const [count, setCount] = useState(0);  // number
const [name, setName] = useState('');   // string

// Object state - explicit type
interface User {
    id: number;
    name: string;
    email: string;
}

const [user, setUser] = useState<User | null>(null);

// Array state
const [items, setItems] = useState<string[]>([]);
const [users, setUsers] = useState<User[]>([]);
```

### Typing Events

```tsx
function Form() {
    const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
        console.log(e.target.value);
    };

    const handleSubmit = (e: React.FormEvent<HTMLFormElement>) => {
        e.preventDefault();
    };

    const handleClick = (e: React.MouseEvent<HTMLButtonElement>) => {
        console.log('Clicked');
    };

    return (
        <form onSubmit={handleSubmit}>
            <input onChange={handleChange} />
            <button onClick={handleClick}>Submit</button>
        </form>
    );
}
```

### Typing Hooks

```tsx
// useRef
const inputRef = useRef<HTMLInputElement>(null);
const countRef = useRef<number>(0);

// useReducer
type Action =
    | { type: 'INCREMENT' }
    | { type: 'DECREMENT' }
    | { type: 'SET'; payload: number };

function reducer(state: number, action: Action): number {
    switch (action.type) {
        case 'INCREMENT': return state + 1;
        case 'DECREMENT': return state - 1;
        case 'SET': return action.payload;
    }
}

// Context
interface AuthContextType {
    user: User | null;
    login: (user: User) => void;
    logout: () => void;
}

const AuthContext = createContext<AuthContextType | null>(null);
```

### Watch It!
⚠️ **Don't overuse `any`!** It defeats the purpose of TypeScript. Use `unknown` if you really don't know the type, or create proper types.

### Brain Power
🧠 Why type component props with `interface` instead of `type`?

**Answer:** Both work, but `interface` can be extended (`extends`) and merged (declaration merging). Convention in React: use `interface` for props and component contracts, `type` for unions, intersections, and utility types.

### There are NO Dumb Questions

**Q: Do I need to type every single prop?**
**A:** Yes, that's the point. TypeScript catches prop typos and missing required props at compile time. Use `?` for optional props with sensible defaults.

**Q: How do I type a component that accepts all HTML attributes?**
**A:** Extend from React's built-in types: `interface ButtonProps extends React.ButtonHTMLAttributes<HTMLButtonElement> { variant: 'primary' | 'secondary'; }`.

**Q: What's the difference between `React.FC` and regular function typing?**
**A:** `React.FC` implicitly adds `children` and has issues with generics. Most teams now prefer typing props directly: `function Button(props: ButtonProps)`.

---

## 27. Styling: CSS Solutions

### CSS Modules (Scoped Styles)

```css
/* Button.module.css */
.button {
    padding: 10px 20px;
    border-radius: 4px;
}

.primary {
    background: blue;
    color: white;
}

.danger {
    background: red;
    color: white;
}
```

```jsx
import styles from './Button.module.css';

function Button({ variant = 'primary', children }) {
    return (
        <button className={`${styles.button} ${styles[variant]}`}>
            {children}
        </button>
    );
}
```

### Tailwind CSS

```jsx
function Card({ title, children }) {
    return (
        <div className="bg-white rounded-lg shadow-md p-6 hover:shadow-lg transition-shadow">
            <h2 className="text-xl font-bold text-gray-800 mb-4">{title}</h2>
            <div className="text-gray-600">{children}</div>
        </div>
    );
}
```

### Styled Components

```jsx
import styled from 'styled-components';

const Button = styled.button`
    padding: 10px 20px;
    border-radius: 4px;
    background: ${props => props.$primary ? 'blue' : 'gray'};
    color: white;

    &:hover {
        opacity: 0.9;
    }
`;

// Usage
<Button $primary>Primary</Button>
<Button>Secondary</Button>
```

### Inline Styles (Use Sparingly)

```jsx
function Box({ color, size }) {
    return (
        <div style={{
            backgroundColor: color,
            width: size,
            height: size,
            borderRadius: '4px'
        }} />
    );
}
```

### Animation with Framer Motion

The most popular React animation library. Declarative, spring-based animations.

```bash
npm install framer-motion
```

```jsx
import { motion, AnimatePresence } from 'framer-motion';

// Basic animation
function FadeIn({ children }) {
    return (
        <motion.div
            initial={{ opacity: 0, y: 20 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.3 }}
        >
            {children}
        </motion.div>
    );
}

// Hover and tap animations
function AnimatedButton({ children, onClick }) {
    return (
        <motion.button
            onClick={onClick}
            whileHover={{ scale: 1.05 }}
            whileTap={{ scale: 0.95 }}
            transition={{ type: 'spring', stiffness: 400 }}
        >
            {children}
        </motion.button>
    );
}

// Exit animations (AnimatePresence required)
function Modal({ isOpen, onClose, children }) {
    return (
        <AnimatePresence>
            {isOpen && (
                <motion.div
                    className="modal-overlay"
                    initial={{ opacity: 0 }}
                    animate={{ opacity: 1 }}
                    exit={{ opacity: 0 }}
                    onClick={onClose}
                >
                    <motion.div
                        className="modal-content"
                        initial={{ scale: 0.9, opacity: 0 }}
                        animate={{ scale: 1, opacity: 1 }}
                        exit={{ scale: 0.9, opacity: 0 }}
                        onClick={e => e.stopPropagation()}
                    >
                        {children}
                    </motion.div>
                </motion.div>
            )}
        </AnimatePresence>
    );
}

// List animations with stagger
function AnimatedList({ items }) {
    return (
        <motion.ul>
            {items.map((item, i) => (
                <motion.li
                    key={item.id}
                    initial={{ opacity: 0, x: -20 }}
                    animate={{ opacity: 1, x: 0 }}
                    transition={{ delay: i * 0.1 }}  // Stagger
                >
                    {item.name}
                </motion.li>
            ))}
        </motion.ul>
    );
}
```

### Watch It!
⚠️ **Pick one approach per project!** Mixing CSS Modules, Tailwind, and styled-components creates confusion. Choose one and stick with it.

### Brain Power
🧠 Which styling approach has the best runtime performance?

**Answer:** CSS Modules and Tailwind have zero runtime cost (styles are extracted at build time). Styled-components and CSS-in-JS have runtime overhead (generating styles on each render). For performance-critical apps, prefer build-time solutions.

### There are NO Dumb Questions

**Q: Can I use Tailwind with component libraries?**
**A:** Yes! Libraries like shadcn/ui are built on Tailwind. You can also combine Tailwind for layout/spacing with a component library for complex widgets.

**Q: Why not just use inline styles for everything?**
**A:** Inline styles can't handle pseudo-classes (`:hover`), media queries, or animations. They also skip the CSS cascade, making theming difficult.

**Q: Are styled-components still recommended?**
**A:** They work but are losing popularity to zero-runtime solutions (Tailwind, CSS Modules). The runtime cost of generating styles on each render adds up in large apps.

---

## 28. Accessibility: Building for Everyone

### Semantic HTML

```jsx
// Bad: div soup
<div onClick={handleClick}>Click me</div>

// Good: semantic elements
<button onClick={handleClick}>Click me</button>

// Use proper headings
<main>
    <h1>Page Title</h1>
    <section>
        <h2>Section Title</h2>
    </section>
</main>
```

### ARIA Attributes

```jsx
function Modal({ isOpen, onClose, title, children }) {
    if (!isOpen) return null;

    return (
        <div
            role="dialog"
            aria-modal="true"
            aria-labelledby="modal-title"
        >
            <h2 id="modal-title">{title}</h2>
            <div>{children}</div>
            <button onClick={onClose} aria-label="Close modal">×</button>
        </div>
    );
}

function LoadingButton({ isLoading, children, ...props }) {
    return (
        <button
            {...props}
            aria-busy={isLoading}
            disabled={isLoading}
        >
            {isLoading ? 'Loading...' : children}
        </button>
    );
}
```

### Focus Management

```jsx
function SearchModal({ isOpen, onClose }) {
    const inputRef = useRef();

    useEffect(() => {
        if (isOpen) {
            inputRef.current?.focus();  // Focus on open
        }
    }, [isOpen]);

    // Trap focus inside modal
    const handleKeyDown = (e) => {
        if (e.key === 'Escape') onClose();
    };

    return (
        <div onKeyDown={handleKeyDown}>
            <input ref={inputRef} placeholder="Search..." />
        </div>
    );
}
```

### Keyboard Navigation

```jsx
function Menu({ items }) {
    const [activeIndex, setActiveIndex] = useState(0);

    const handleKeyDown = (e) => {
        switch (e.key) {
            case 'ArrowDown':
                setActiveIndex(i => Math.min(i + 1, items.length - 1));
                break;
            case 'ArrowUp':
                setActiveIndex(i => Math.max(i - 1, 0));
                break;
            case 'Enter':
                items[activeIndex].onClick();
                break;
        }
    };

    return (
        <ul role="menu" onKeyDown={handleKeyDown}>
            {items.map((item, index) => (
                <li
                    key={item.id}
                    role="menuitem"
                    tabIndex={index === activeIndex ? 0 : -1}
                >
                    {item.label}
                </li>
            ))}
        </ul>
    );
}
```

### Live Regions: Announcing Dynamic Content

```jsx
function Notifications() {
    const [message, setMessage] = useState('');

    const saveItem = async () => {
        await save();
        setMessage('Item saved successfully');  // Screen reader announces this
    };

    return (
        <div>
            <button onClick={saveItem}>Save</button>
            {/* aria-live announces content changes to screen readers */}
            <div aria-live="polite" role="status">
                {message}
            </div>
        </div>
    );
}

// For urgent announcements (errors, alerts)
<div aria-live="assertive" role="alert">
    {error && `Error: ${error}`}
</div>
```

### Skip Navigation Links

```jsx
function App() {
    return (
        <>
            {/* Hidden until focused - lets keyboard users skip nav */}
            <a href="#main-content" className="skip-link">
                Skip to main content
            </a>
            <nav>...</nav>
            <main id="main-content" tabIndex={-1}>
                {/* Page content */}
            </main>
        </>
    );
}
```

### Watch It!
⚠️ **Test with a screen reader!** VoiceOver (Mac), NVDA (Windows), or browser extensions. What looks right might not sound right.

### Brain Power
🧠 Why is `<div onClick>` worse than `<button onClick>` for accessibility?

**Answer:** `<button>` gives you for free: keyboard activation (Enter/Space), focus indication, screen reader announcement as "button", and disabled state. A `<div>` gets none of these unless you manually add `role="button"`, `tabIndex`, `onKeyDown`, and `aria-disabled`.

### There are NO Dumb Questions

**Q: When should I use aria-label vs aria-labelledby?**
**A:** Use `aria-label` for a short inline label (icon buttons). Use `aria-labelledby` to reference visible text elsewhere on the page as the label.

**Q: How do I make a custom dropdown accessible?**
**A:** Don't build one from scratch. Use a library like Radix, Headless UI, or React Aria that handles ARIA roles, keyboard navigation, and focus management correctly.

**Q: Is `tabIndex={0}` always safe to use?**
**A:** It makes any element focusable and adds it to the natural tab order. Only use it on interactive elements. Adding focus to non-interactive elements confuses keyboard users.

---

## 29. Testing

### React Testing Library + Vitest

```bash
npm install -D vitest @testing-library/react @testing-library/jest-dom jsdom
```

```jsx
// Button.test.jsx
import { render, screen, fireEvent } from '@testing-library/react';
import { describe, it, expect, vi } from 'vitest';
import Button from './Button';

describe('Button', () => {
    it('renders with text', () => {
        render(<Button>Click me</Button>);
        expect(screen.getByText('Click me')).toBeInTheDocument();
    });

    it('calls onClick when clicked', () => {
        const handleClick = vi.fn();
        render(<Button onClick={handleClick}>Click</Button>);

        fireEvent.click(screen.getByText('Click'));

        expect(handleClick).toHaveBeenCalledTimes(1);
    });

    it('is disabled when disabled prop is true', () => {
        render(<Button disabled>Click</Button>);
        expect(screen.getByText('Click')).toBeDisabled();
    });
});
```

### Testing Async Components

```jsx
import { render, screen, waitFor } from '@testing-library/react';

it('loads and displays user data', async () => {
    render(<UserProfile userId="123" />);

    // Wait for loading to finish
    await waitFor(() => {
        expect(screen.queryByText('Loading...')).not.toBeInTheDocument();
    });

    expect(screen.getByText('John Doe')).toBeInTheDocument();
});
```

### Testing Custom Hooks

```jsx
import { renderHook, act } from '@testing-library/react';
import { useCounter } from './useCounter';

describe('useCounter', () => {
    it('starts with initial value', () => {
        const { result } = renderHook(() => useCounter(10));
        expect(result.current.count).toBe(10);
    });

    it('increments the count', () => {
        const { result } = renderHook(() => useCounter(0));

        // Wrap state updates in act()
        act(() => {
            result.current.increment();
        });

        expect(result.current.count).toBe(1);
    });

    it('resets to initial value', () => {
        const { result } = renderHook(() => useCounter(5));

        act(() => {
            result.current.increment();
            result.current.increment();
            result.current.reset();
        });

        expect(result.current.count).toBe(5);
    });

    // Testing hooks that depend on props
    it('updates when initial value changes', () => {
        const { result, rerender } = renderHook(
            ({ initial }) => useCounter(initial),
            { initialProps: { initial: 0 } }
        );

        expect(result.current.count).toBe(0);

        rerender({ initial: 100 });
        // Note: depends on hook implementation
    });
});
```

### Mocking Patterns

```jsx
import { render, screen, waitFor } from '@testing-library/react';
import { vi, describe, it, expect, beforeEach } from 'vitest';
import UserProfile from './UserProfile';

// Mock an entire module
vi.mock('./api', () => ({
    fetchUser: vi.fn()
}));

import { fetchUser } from './api';

describe('UserProfile', () => {
    beforeEach(() => {
        vi.clearAllMocks();
    });

    it('displays user data on successful fetch', async () => {
        // Setup mock return value
        fetchUser.mockResolvedValue({
            id: 1,
            name: 'John Doe',
            email: 'john@example.com'
        });

        render(<UserProfile userId={1} />);

        await waitFor(() => {
            expect(screen.getByText('John Doe')).toBeInTheDocument();
        });

        expect(fetchUser).toHaveBeenCalledWith(1);
    });

    it('displays error message on failed fetch', async () => {
        fetchUser.mockRejectedValue(new Error('Network error'));

        render(<UserProfile userId={1} />);

        await waitFor(() => {
            expect(screen.getByText(/error/i)).toBeInTheDocument();
        });
    });

    // Mock timers
    it('auto-refreshes data every 30 seconds', async () => {
        vi.useFakeTimers();
        fetchUser.mockResolvedValue({ id: 1, name: 'John' });

        render(<UserProfile userId={1} autoRefresh />);

        expect(fetchUser).toHaveBeenCalledTimes(1);

        // Fast-forward 30 seconds
        await act(() => vi.advanceTimersByTime(30000));

        expect(fetchUser).toHaveBeenCalledTimes(2);

        vi.useRealTimers();
    });
});
```

### End-to-End Testing with Playwright

For testing full user flows across your entire application:

```bash
npm install -D @playwright/test
npx playwright install
```

```js
// e2e/login.spec.js
import { test, expect } from '@playwright/test';

test.describe('Login Flow', () => {
    test('user can log in successfully', async ({ page }) => {
        await page.goto('/login');

        // Fill in the form
        await page.fill('[name="email"]', 'user@example.com');
        await page.fill('[name="password"]', 'password123');
        await page.click('button[type="submit"]');

        // Verify redirect to dashboard
        await expect(page).toHaveURL('/dashboard');
        await expect(page.locator('h1')).toContainText('Welcome');
    });

    test('shows error for invalid credentials', async ({ page }) => {
        await page.goto('/login');

        await page.fill('[name="email"]', 'wrong@example.com');
        await page.fill('[name="password"]', 'wrongpassword');
        await page.click('button[type="submit"]');

        await expect(page.locator('.error')).toContainText('Invalid credentials');
        await expect(page).toHaveURL('/login');  // Stay on login page
    });
});
```

**When to use E2E tests:**
- Critical user journeys (signup, checkout, core workflows)
- Integration with external services
- Multi-page flows that unit tests can't cover

### Watch It!
⚠️ **Don't test implementation details!** Avoid testing internal state, method names, or component structure. If you refactor a component but it looks the same to users, your tests shouldn't break. Test behavior: "when I click X, I see Y."

### Brain Power
🧠 Why test "what the user sees" instead of internal state?

**Answer:** Users don't see state - they see the UI. Testing behavior (click button, see result) is resilient to refactoring. Testing implementation (state changed) breaks when you rename variables.

### There are NO Dumb Questions

**Q: Should I use Vitest or Jest?**
**A:** Vitest is recommended for new projects (faster, ESM-native, works with Vite). Jest is fine for existing projects. Both have nearly identical APIs.

**Q: How do I test components that use Context or Router?**
**A:** Wrap the component in the required providers during testing: `render(<BrowserRouter><ThemeProvider><MyComponent /></ThemeProvider></BrowserRouter>)`. Create a test utility wrapper for this.

**Q: What's the difference between `getBy`, `queryBy`, and `findBy`?**
**A:** `getBy` throws if not found (use for elements that should exist). `queryBy` returns null if not found (use for asserting absence). `findBy` waits asynchronously (use for elements that appear after loading).

### Interview Checkpoint 🛑
**Interviewer:** "How do you decide what to test in a React application?"
**You:** "I follow the testing trophy: mostly integration tests, some unit tests, few E2E tests. I test user-facing behavior, not implementation details. Priority order: (1) critical user paths (login, checkout, core features), (2) components with complex logic or many states, (3) edge cases that have caused bugs before. I avoid testing: styling, third-party libraries, or internal component state. The goal is confidence that the app works, not 100% coverage."

---

## 30. Strict Mode

### What is Strict Mode?

A development tool that helps find bugs by intentionally double-invoking functions.

```jsx
import { StrictMode } from 'react';
import { createRoot } from 'react-dom/client';

createRoot(document.getElementById('root')).render(
    <StrictMode>
        <App />
    </StrictMode>
);
```

### What It Catches

1. **Impure renders:** Components should return the same JSX for the same props
2. **Missing cleanup:** Effects without cleanup functions
3. **Deprecated APIs:** Legacy lifecycle methods

```jsx
// This bug is caught by Strict Mode
useEffect(() => {
    const id = setInterval(() => console.log('tick'), 1000);
    // Missing cleanup! Strict Mode runs twice, creating 2 intervals
}, []);

// Fixed
useEffect(() => {
    const id = setInterval(() => console.log('tick'), 1000);
    return () => clearInterval(id);  // Cleanup
}, []);
```

### Common Bugs Strict Mode Reveals

```jsx
// Bug: Side effect in render (runs twice in Strict Mode)
function BadComponent() {
    // ❌ Mutating external variable during render
    externalArray.push('item');  // Doubled in Strict Mode!
    return <div>{externalArray.length}</div>;
}

// Fix: Move side effects to useEffect
function GoodComponent() {
    useEffect(() => {
        externalArray.push('item');  // Only runs once per mount
        return () => { externalArray.pop(); };  // Cleanup
    }, []);
    return <div>{externalArray.length}</div>;
}
```

```jsx
// Bug: Missing cleanup causes memory leaks
function ChatRoom({ roomId }) {
    useEffect(() => {
        const connection = createConnection(roomId);
        connection.connect();
        // ❌ No cleanup! Strict Mode creates 2 connections
    }, [roomId]);

    // Fix: Always clean up
    useEffect(() => {
        const connection = createConnection(roomId);
        connection.connect();
        return () => connection.disconnect();  // ✅ Cleanup
    }, [roomId]);
}
```

### Watch It!
⚠️ **"Why does my component render twice?"** That's Strict Mode! It only happens in development to help find bugs. Production renders normally.

### Brain Power
🧠 Why does Strict Mode remount components (mount → unmount → mount)?

**Answer:** It simulates what happens when a user navigates away and back (like React's future Offscreen API). If your component breaks when remounted, it has a cleanup bug that would cause issues in production.

### There are NO Dumb Questions

**Q: Should I remove StrictMode in production?**
**A:** You don't need to - it automatically does nothing in production builds. The double-rendering only happens in development mode.

**Q: Can I use StrictMode on just part of my app?**
**A:** Yes! Wrap only specific subtrees. Useful when gradually adding StrictMode to a legacy codebase.

**Q: My API call fires twice in development. Is that a bug?**
**A:** It's Strict Mode testing your cleanup. Add an AbortController to your useEffect so the first call gets cancelled. In production, it only fires once.

---

## 31. React DevTools

### Essential Debugging Tool

Install the browser extension for Chrome/Firefox/Edge.

### Components Tab
- Inspect component tree and hierarchy
- View and edit props/state live
- Search components by name
- See which components re-rendered

### Profiler Tab
- Record render sessions
- Find slow components
- See why components re-rendered
- Identify render frequency

### Pro Tips

```jsx
// Name components for easier debugging
const MemoizedList = memo(function ProductList({ items }) {
    return <ul>{items.map(i => <li key={i.id}>{i.name}</li>)}</ul>;
});

// displayName for HOCs and forwardRef
const Input = forwardRef(function Input(props, ref) {
    return <input ref={ref} {...props} />;
});
Input.displayName = 'Input';
```

### Debugging Performance with Profiler

```jsx
// 1. Open Profiler tab → Click Record → Interact with app → Stop

// 2. Flamegraph shows render time per component
//    - Gray = didn't render
//    - Green = fast render
//    - Yellow/Red = slow render

// 3. "Why did this render?" shows:
//    - Props changed (which ones)
//    - State changed
//    - Parent rendered
//    - Context changed

// 4. Programmatic profiling
import { Profiler } from 'react';

function onRender(id, phase, actualDuration) {
    console.log(`${id} ${phase} render took ${actualDuration}ms`);
}

<Profiler id="ProductList" onRender={onRender}>
    <ProductList items={items} />
</Profiler>
```

### Watch It!
⚠️ **Enable "Highlight updates"** in DevTools settings. If you see constant flashing, you have unnecessary re-renders!

### Brain Power
🧠 How do you identify the root cause of unnecessary re-renders?

**Answer:** In the Profiler, check "Why did this render?" for each slow component. Common causes: parent re-rendering (fix with memo), new object/function props (fix with useMemo/useCallback), or context changes (fix by splitting context).

### There are NO Dumb Questions

**Q: Why do I see "Anonymous" components in DevTools?**
**A:** Arrow function components without names show as "Anonymous." Always use named functions: `const List = memo(function List() { ... })` instead of `memo(() => ...)`.

**Q: Can I edit state directly in DevTools?**
**A:** Yes! In the Components tab, click any state value to edit it live. Great for testing edge cases without writing code.

**Q: DevTools shows gray (didn't render) but my component is slow. Why?**
**A:** The component might be expensive on its initial render. Or a child component is slow. Drill down into the flamegraph to find the actual bottleneck.

---

## 32. Common Pitfalls

### Stale Closures

```jsx
// Bug: count is always 0 in the interval
function Counter() {
    const [count, setCount] = useState(0);

    useEffect(() => {
        const id = setInterval(() => {
            console.log(count);  // Always 0!
            setCount(count + 1); // Always sets to 1
        }, 1000);
        return () => clearInterval(id);
    }, []);  // Empty deps = stale closure

    // Fix: Use functional update
    useEffect(() => {
        const id = setInterval(() => {
            setCount(c => c + 1);  // Uses latest value
        }, 1000);
        return () => clearInterval(id);
    }, []);
}
```

### Infinite useEffect Loops

```jsx
// Bug: Infinite loop!
useEffect(() => {
    setData(fetchData());  // Updates state
}, [data]);  // Runs when data changes... which just happened!

// Fix: Remove dependency or add condition
useEffect(() => {
    if (!data) {
        setData(fetchData());
    }
}, [data]);
```

### Object/Array Dependencies

```jsx
// Bug: Runs every render (new object each time)
const options = { page: 1 };
useEffect(() => {
    fetchData(options);
}, [options]);  // New object reference every render!

// Fix: Memoize or use primitive values
const options = useMemo(() => ({ page: 1 }), []);
// Or just use the primitive
useEffect(() => {
    fetchData({ page });
}, [page]);
```

### Mutating State

```jsx
// Bug: Mutating state directly
const [items, setItems] = useState([1, 2, 3]);

const addItem = () => {
    items.push(4);    // Mutates original array!
    setItems(items);  // Same reference, no re-render
};

// Fix: Create new array
const addItem = () => {
    setItems([...items, 4]);  // New array
};
```

### Missing Keys or Duplicate Keys

```jsx
// Bug: No key
{items.map(item => <li>{item.name}</li>)}

// Bug: Index as key (problems with reordering)
{items.map((item, i) => <li key={i}>{item.name}</li>)}

// Fix: Unique stable ID
{items.map(item => <li key={item.id}>{item.name}</li>)}
```

### Brain Power
🧠 What do all these pitfalls have in common?

**Answer:** They all involve misunderstanding React's rendering model. React relies on: immutable state (new references trigger renders), stable dependency references (for hooks), and predictable hook call order. Understanding these three principles prevents most bugs.

### There are NO Dumb Questions

**Q: How do I debug a stale closure?**
**A:** Add the variable to the useEffect dependency array. If ESLint's exhaustive-deps rule warns about a missing dependency, it's almost always right. Use functional updates (`setCount(c => c + 1)`) when you need the latest value without adding it as a dependency.

**Q: Why does React not detect state mutations?**
**A:** React uses reference equality (`===`). Mutating an array and calling `setState(sameArray)` passes the same reference - React thinks nothing changed. Always create new objects/arrays.

**Q: What's the safest way to update nested state?**
**A:** Spread at each level: `setUser({ ...user, address: { ...user.address, city: 'New York' } })`. For deeply nested state, consider Immer or flattening your state structure.

---

## 33. Server Components

### What Are Server Components?

React Server Components (RSC) run on the server, reducing JavaScript sent to the client. Used in Next.js 13+ App Router.

```jsx
// This component runs on the server (default in Next.js App Router)
async function ProductList() {
    // Direct database access - no API needed!
    const products = await db.products.findMany();

    return (
        <ul>
            {products.map(p => <li key={p.id}>{p.name}</li>)}
        </ul>
    );
}
```

### Client vs Server Components

```jsx
// Server Component (default) - can't use hooks or browser APIs
async function ServerComponent() {
    const data = await fetchFromDatabase();
    return <div>{data.title}</div>;
}

// Client Component - add "use client" directive at the TOP of the file
'use client';

import { useState } from 'react';

function ClientComponent() {
    const [count, setCount] = useState(0);
    return <button onClick={() => setCount(c => c + 1)}>{count}</button>;
}
```

### The Boundary Pattern: Composing Server & Client

```jsx
// Server Component can render Client Components as children
// page.jsx (Server Component)
import { AddToCartButton } from './AddToCartButton';  // Client Component

async function ProductPage({ params }) {
    const product = await db.products.findUnique({ where: { id: params.id } });

    return (
        <div>
            <h1>{product.name}</h1>
            <p>{product.description}</p>
            {/* Pass server data as props to client component */}
            <AddToCartButton productId={product.id} price={product.price} />
        </div>
    );
}
```

```jsx
// AddToCartButton.jsx (Client Component)
'use client';

import { useState } from 'react';

export function AddToCartButton({ productId, price }) {
    const [added, setAdded] = useState(false);

    return (
        <button onClick={() => { addToCart(productId); setAdded(true); }}>
            {added ? 'Added!' : `Add to Cart - $${price}`}
        </button>
    );
}
```

### Server Actions with 'use server'

```jsx
// actions.js - Server-side functions callable from client
'use server';

import { db } from './db';
import { revalidatePath } from 'next/cache';

export async function addProduct(formData) {
    const name = formData.get('name');
    const price = parseFloat(formData.get('price'));

    await db.products.create({ data: { name, price } });

    revalidatePath('/products');  // Refresh the page data
}

export async function deleteProduct(id) {
    await db.products.delete({ where: { id } });
    revalidatePath('/products');
}
```

```jsx
// Using Server Actions in forms (works without JavaScript!)
'use client';

import { addProduct } from './actions';

function AddProductForm() {
    return (
        <form action={addProduct}>
            <input name="name" placeholder="Product name" required />
            <input name="price" type="number" step="0.01" required />
            <button type="submit">Add Product</button>
        </form>
    );
}
```

### When to Use Each

| Server Components | Client Components |
|-------------------|-------------------|
| Fetch data | useState, useEffect |
| Access backend resources | Event handlers (onClick) |
| Keep sensitive info server-side | Browser APIs |
| Large dependencies (zero client JS) | Interactivity |
| SEO-critical content | Real-time updates |

### React Meta-Frameworks Comparison

| Feature | Next.js | Remix | Astro |
|---------|---------|-------|-------|
| **Server Components** | Yes (App Router) | Partial (loaders) | Yes (islands) |
| **Data Fetching** | fetch in RSC, Server Actions | Loaders + Actions | Astro.glob, fetch |
| **Routing** | File-based | File-based | File-based |
| **Rendering** | SSR, SSG, ISR | SSR only | SSG by default, SSR opt-in |
| **Styling** | Any (CSS Modules, Tailwind) | Any | Any + scoped by default |
| **Best For** | Full-stack apps, enterprise | Form-heavy apps, web standards | Content sites, blogs, docs |
| **Learning Curve** | Medium | Medium | Low (if you know React) |

**Quick Guide:**
- **Next.js:** The default choice for most React apps. Full-featured, great DX, huge ecosystem.
- **Remix:** Best for apps with lots of forms and mutations. Embraces web standards.
- **Astro:** Best for content-heavy sites. Ships zero JS by default, add React where needed.

```jsx
// Next.js 14+ App Router
// app/products/page.tsx
export default async function ProductsPage() {
    const products = await db.products.findMany();  // Server Component
    return <ProductList products={products} />;
}

// Remix
// routes/products.tsx
export async function loader() {
    return json(await db.products.findMany());
}
export default function Products() {
    const products = useLoaderData();
    return <ProductList products={products} />;
}

// Astro with React island
// pages/products.astro
---
const products = await db.products.findMany();
---
<Layout>
    <ProductList client:load products={products} />
</Layout>
```

### Watch It!
⚠️ **You can't import a Server Component into a Client Component!** The boundary flows one way. Pass Server Components as `children` props to Client Components instead.

```jsx
// ❌ Can't do this
'use client';
import ServerComponent from './ServerComponent';  // Error!

// ✅ Pass as children instead
// layout.jsx (Server Component)
<ClientWrapper>
    <ServerComponent />  {/* Rendered on server, passed as children */}
</ClientWrapper>
```

### Brain Power
🧠 Why can't Server Components use useState or useEffect?

**Answer:** Server Components render once on the server and send HTML to the client. There's no "re-render" on the server - no state updates, no effects, no event handlers. They're essentially static after the initial render. Use Client Components for anything interactive.

### There are NO Dumb Questions

**Q: Do I need Next.js to use Server Components?**
**A:** Currently yes. Next.js 13+ (App Router) is the primary framework supporting RSC. Other frameworks (Remix, Waku) are adding support, but it's not available in plain React (Vite/CRA) yet.

**Q: What can I pass as props from Server to Client Components?**
**A:** Only serializable values: strings, numbers, booleans, arrays, plain objects, and Date. You cannot pass functions, class instances, or React elements as props across the boundary.

**Q: How do Server Actions compare to API routes?**
**A:** Server Actions are typed, colocated with your components, and work with progressive enhancement (forms work without JS). API routes are better for third-party integrations or when you need a REST/GraphQL endpoint.

---

## Congratulations!

You've completed a comprehensive React journey - from JSX basics to Server Components!

### Your Learning Path

**Beginner → Intermediate:**
1. Build 3+ projects with useState and useEffect
2. Master React Router for multi-page apps
3. Learn form handling with react-hook-form

**Intermediate → Advanced:**
4. Add TypeScript to a project
5. Use React Query for data fetching
6. Implement performance optimizations (memo, useMemo)

**Advanced → Production:**
7. Learn Next.js for full-stack React
8. Write tests with React Testing Library
9. Set up CI/CD and deployment

### Final Challenge
🧠 Build a full-stack task manager with:
- TypeScript for type safety
- React Query for API calls
- Zustand for client state
- React Router for navigation
- React Hook Form for inputs
- Error boundaries for resilience
- Accessibility best practices
- Unit tests for critical paths

### Additional Resources

- **React Docs:** https://react.dev/
- **React Tutorial:** https://react.dev/learn/tutorial-tic-tac-toe
- **TypeScript Handbook:** https://www.typescriptlang.org/docs/
- **Testing Library:** https://testing-library.com/docs/react-testing-library/intro/
- **React Roadmap:** https://roadmap.sh/react
- **Next.js Docs:** https://nextjs.org/docs

---

## Quick Reference Card

```jsx
// Component
function Component({ prop }) {
    return <div>{prop}</div>;
}

// State
const [state, setState] = useState(initial);
const [state, dispatch] = useReducer(reducer, initial);

// Refs
const ref = useRef(null);
<input ref={ref} />

// Effects
useEffect(() => {
    // Side effect
    return () => { /* cleanup */ };
}, [dependencies]);

// Context
const value = useContext(MyContext);

// Memoization
const memoized = useMemo(() => compute(a, b), [a, b]);
const callback = useCallback(() => fn(a), [a]);
const MemoComp = memo(Component);

// Events
<button onClick={handleClick}>Click</button>
<input onChange={(e) => setValue(e.target.value)} />
<form onSubmit={(e) => { e.preventDefault(); }}>

// Conditional
{condition && <Component />}
{condition ? <A /> : <B />}

// Lists
{items.map(item => <li key={item.id}>{item.name}</li>)}

// Portals
{createPortal(<Modal />, document.body)}

// Lazy Loading
const LazyComp = lazy(() => import('./Component'));
<Suspense fallback={<Loading />}><LazyComp /></Suspense>
```

---

**Created in the style of Head First books**

*Now go build something amazing with React!*