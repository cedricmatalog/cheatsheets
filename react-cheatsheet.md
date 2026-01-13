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

1. [Introduction: What is React?](#1-introduction-what-is-react)
2. [Components: Building Blocks](#2-components-building-blocks)
3. [JSX: HTML in JavaScript](#3-jsx-html-in-javascript)
4. [Props: Passing Data Down](#4-props-passing-data-down)
5. [State: Data That Changes](#5-state-data-that-changes)
6. [Events: Handling Interactions](#6-events-handling-interactions)
7. [Conditional Rendering: Show or Hide](#7-conditional-rendering-show-or-hide)
8. [Lists: Rendering Multiple Items](#8-lists-rendering-multiple-items)
9. [useEffect: Side Effects](#9-useeffect-side-effects)
10. [Custom Hooks: Reusable Logic](#10-custom-hooks-reusable-logic)
11. [Context: Sharing State](#11-context-sharing-state)
12. [Forms: User Input](#12-forms-user-input)
13. [Routing: Multiple Pages](#13-routing-multiple-pages)
14. [API Calls: Fetching Data](#14-api-calls-fetching-data)
15. [Advanced Patterns](#15-advanced-patterns)

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
// App.jsx
function App() {
    return (
        <div>
            <h1>Hello, React!</h1>
            <p>Welcome to your first React app</p>
        </div>
    );
}

export default App;
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
    return <footer><p>&copy; 2024</p></footer>;
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
                {hobbies.map((hobby, index) => (
                    <li key={index}>{hobby}</li>
                ))}
            </ul>

            {/* Ternary operator */}
            <p>Status: {user.age >= 18 ? 'Adult' : 'Minor'}</p>
        </div>
    );
}
```

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
    return <Greeting name="Alice" age={25} />;
}

// Child receives props
function Greeting(props) {
    return (
        <div>
            <h1>Hello, {props.name}!</h1>
            <p>You are {props.age} years old</p>
        </div>
    );
}
```

### Destructuring Props: Cleaner syntax

```jsx
// Without destructuring
function Greeting(props) {
    return <h1>Hello, {props.name}!</h1>;
}

// With destructuring (recommended!)
function Greeting({ name, age }) {
    return (
        <div>
            <h1>Hello, {name}!</h1>
            <p>You are {age} years old</p>
        </div>
    );
}
```

### Default Props: Fallback values

```jsx
function Greeting({ name = 'Guest', age = 18 }) {
    return (
        <div>
            <h1>Hello, {name}!</h1>
            <p>You are {age} years old</p>
        </div>
    );
}

// Usage
<Greeting />  // Uses defaults
<Greeting name="Alice" />  // Uses Alice, default age
<Greeting name="Bob" age={30} />  // Both specified
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

---

## 5. State: Data That Changes

### What is state?

State is data that changes over time. When state changes, React re-renders the component.

```jsx
import { useState } from 'react';

function Counter() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>
                Increment
            </button>
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
    // Number state
    const [count, setCount] = useState(0);

    // String state
    const [name, setName] = useState('Alice');

    // Boolean state
    const [isVisible, setIsVisible] = useState(true);

    // Object state
    const [user, setUser] = useState({
        name: 'Alice',
        age: 25
    });

    // Array state
    const [items, setItems] = useState([1, 2, 3]);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>+</button>

            <p>Name: {name}</p>
            <input value={name} onChange={(e) => setName(e.target.value)} />

            <p>Visible: {isVisible ? 'Yes' : 'No'}</p>
            <button onClick={() => setIsVisible(!isVisible)}>Toggle</button>
        </div>
    );
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

---

## 6. Events: Handling Interactions

### Handling Events in React

```jsx
function Button() {
    const handleClick = () => {
        alert('Button clicked!');
    };

    return <button onClick={handleClick}>Click me</button>;
}

// Inline function (for simple logic)
function Button() {
    return (
        <button onClick={() => alert('Clicked!')}>
            Click me
        </button>
    );
}
```

### Event Object: Getting event data

```jsx
function Form() {
    const handleSubmit = (event) => {
        event.preventDefault();  // Prevent page refresh
        console.log('Form submitted');
    };

    const handleChange = (event) => {
        console.log(event.target.value);  // Get input value
    };

    return (
        <form onSubmit={handleSubmit}>
            <input onChange={handleChange} />
            <button type="submit">Submit</button>
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
                onKeyPress={(e) => console.log('Key press:', e.key)}
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

---

## 8. Lists: Rendering Multiple Items

### Mapping Arrays

```jsx
function List() {
    const items = ['Apple', 'Banana', 'Cherry'];

    return (
        <ul>
            {items.map((item, index) => (
                <li key={index}>{item}</li>
            ))}
        </ul>
    );
}
```

### Keys: Important for performance

```jsx
// Bad: Using index as key (only if list never changes)
{items.map((item, index) => <li key={index}>{item}</li>)}

// Good: Using unique ID
{items.map(item => <li key={item.id}>{item.name}</li>)}
```

### Watch It!
⚠️ **Keys must be unique among siblings!** React uses keys to identify which items changed. Don't use array index unless the list never reorders.

---

## 9. useEffect: Side Effects

### What are side effects?

Side effects are anything that affects something outside the component: fetching data, subscriptions, timers, directly manipulating DOM.

```jsx
import { useEffect } from 'react';

function Example() {
    useEffect(() => {
        // This runs after render
        document.title = 'Hello!';
    });

    return <h1>Hello</h1>;
}
```

### useEffect with Dependencies

```jsx
// Runs after every render
useEffect(() => {
    console.log('Every render');
});

// Runs once (on mount)
useEffect(() => {
    console.log('Only once');
}, []);

// Runs when dependencies change
useEffect(() => {
    console.log('Count changed:', count);
}, [count]);
```

### Cleanup: Preventing memory leaks

```jsx
useEffect(() => {
    const timer = setInterval(() => {
        console.log('Tick');
    }, 1000);

    // Cleanup function
    return () => {
        clearInterval(timer);
    };
}, []);
```

### Fetching Data

```jsx
function UserProfile({ userId }) {
    const [user, setUser] = useState(null);
    const [loading, setLoading] = useState(true);

    useEffect(() => {
        setLoading(true);

        fetch(`https://api.example.com/users/${userId}`)
            .then(res => res.json())
            .then(data => {
                setUser(data);
                setLoading(false);
            });
    }, [userId]);

    if (loading) return <p>Loading...</p>;

    return <div>{user.name}</div>;
}
```

---

## Congratulations!

You've learned React fundamentals! But there's so much more to explore.

### What's next?

1. **Practice, practice, practice** - Build real projects!
2. **Learn React Router** - Multi-page applications
3. **Master useEffect** - Data fetching, subscriptions
4. **State Management** - Context API, Zustand
5. **React Query** - Server state management
6. **Next.js** - Full-stack React framework
7. **TypeScript** - Type-safe React
8. **Testing** - React Testing Library

### Final Challenge
🧠 Build a complete weather app with:
- Component composition
- State management (useState)
- API calls (useEffect + fetch)
- Conditional rendering
- Lists with keys
- Form input
- Loading states

### Additional Resources

- **React Docs (New):** https://react.dev/
- **React Docs (Legacy):** https://legacy.reactjs.org/
- **React Tutorial:** https://react.dev/learn/tutorial-tic-tac-toe
- **Frontend Roadmap:** https://roadmap.sh/react
- **TypeScript Roadmap:** https://roadmap.sh/typescript

---

## Quick Reference Card

**Component:**
```jsx
function Component() {
    return <div>Hello</div>;
}
```

**State:**
```jsx
const [state, setState] = useState(initial);
```

**Props:**
```jsx
function Greeting({ name }) {
    return <h1>Hello, {name}</h1>;
}
```

**Events:**
```jsx
<button onClick={handleClick}>Click</button>
```

**Conditional:**
```jsx
{condition && <Component />}
{condition ? <A /> : <B />}
```

**List:**
```jsx
{items.map(item => <li key={item.id}>{item.text}</li>)}
```

**Effect:**
```jsx
useEffect(() => {
    // Side effect
    return () => {/* cleanup */};
}, [dependencies]);
```

---

**Created in the style of Head First books**

*Now go build something amazing with React!* ⚛️