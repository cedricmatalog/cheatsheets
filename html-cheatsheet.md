# HTML Cheatsheet

> A comprehensive reference guide for HTML based on the roadmap.sh HTML roadmap

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [Your First HTML File](#2-your-first-html-file)
3. [Basic Tags](#3-basic-tags)
4. [Textual Tags](#4-textual-tags)
5. [Lists and Types](#5-lists-and-types)
6. [Table Tag](#6-table-tag)
7. [Embedding Media](#7-embedding-media)
8. [Using Forms](#8-using-forms)
9. [Semantic Markup](#9-semantic-markup)
10. [Styling Basics](#10-styling-basics)
11. [Including JavaScript](#11-including-javascript)
12. [Accessibility](#12-accessibility)
13. [Basics of SEO](#13-basics-of-seo)

---

## 1. Introduction

### What are markup languages?

Markup languages are used to annotate text so that computers can process and display it. HTML (HyperText Markup Language) is the standard markup language for creating web pages.

### What is HTTP?

HTTP (HyperText Transfer Protocol) is the protocol used for transmitting web pages over the internet. HTTPS is the secure version.

### DNS (Domain Name System)

DNS translates domain names (like example.com) into IP addresses that computers use to identify each other.

### Domain names

A domain name is a unique address that identifies a website on the internet (e.g., google.com, github.com).

### Browsers

Web browsers (Chrome, Firefox, Safari, Edge) are applications that retrieve and display web pages.

### Hosting

Web hosting is a service that stores your website files and makes them accessible on the internet.

### What is SEO?

SEO (Search Engine Optimization) is the practice of optimizing websites to rank higher in search engine results.

### How the web works

When you type a URL, your browser sends an HTTP request to a server, which responds with HTML, CSS, and JavaScript files that your browser renders as a web page.

---

## 2. Your First HTML File

### Tags and Attributes

HTML uses tags enclosed in angle brackets. Most tags have opening and closing pairs.

```html
<tagname attribute="value">Content</tagname>
```

### Case Insensitivity

HTML tags are case-insensitive, but lowercase is the standard convention.

```html
<DIV> and <div> are the same, but use <div>
```

### HTML Entities

Special characters that need to be encoded:

| Entity | Character | Description |
|--------|-----------|-------------|
| `&lt;` | < | Less than |
| `&gt;` | > | Greater than |
| `&amp;` | & | Ampersand |
| `&quot;` | " | Quotation mark |
| `&nbsp;` | (space) | Non-breaking space |
| `&copy;` | © | Copyright |
| `&reg;` | ® | Registered trademark |
| `&trade;` | ™ | Trademark |

### HTML Comments

```html
<!-- This is a comment and won't be displayed -->
```

### Whitespaces

Multiple spaces and line breaks are collapsed into a single space in HTML.

```html
<p>This    has     many     spaces</p>
<!-- Displays as: This has many spaces -->
```

### Basic HTML Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page Title</title>
</head>
<body>
    <!-- Your content here -->
</body>
</html>
```

---

## 3. Basic Tags

### Document Structure

#### `<!DOCTYPE html>`
Declares the document type and HTML version.

#### `<html>`
Root element of an HTML page.

```html
<html lang="en"></html>
```

#### `<head>`
Contains metadata about the document.

#### `<meta>`
Defines metadata like character set, viewport, description.

```html
<meta charset="UTF-8">
<meta name="description" content="Page description">
<meta name="keywords" content="HTML, CSS, JavaScript">
<meta name="author" content="Your Name">
```

#### `<title>`
Sets the page title shown in browser tab.

```html
<title>My Website</title>
```

#### `<body>`
Contains the visible page content.

### Text Content Tags

#### `<h1>` to `<h6>`
Heading tags, from most important (h1) to least important (h6).

```html
<h1>Main Heading</h1>
<h2>Subheading</h2>
<h3>Sub-subheading</h3>
<h4>Level 4 Heading</h4>
<h5>Level 5 Heading</h5>
<h6>Level 6 Heading</h6>
```

#### `<p>`
Paragraph tag.

```html
<p>This is a paragraph of text.</p>
```

#### `<br>`
Line break (self-closing tag).

```html
<p>Line one<br>Line two</p>
```

#### `<hr>`
Horizontal rule (divider line).

```html
<hr>
```

#### `<b>` / `<strong>`
Bold text. Use `<strong>` for semantic importance.

```html
<b>Bold text</b>
<strong>Important text</strong>
```

#### `<i>` / `<em>`
Italic text. Use `<em>` for emphasis.

```html
<i>Italic text</i>
<em>Emphasized text</em>
```

#### `<mark>`
Highlighted text.

```html
<mark>Highlighted text</mark>
```

#### `<sub>`
Subscript text.

```html
H<sub>2</sub>O
```

#### `<sup>`
Superscript text.

```html
x<sup>2</sup>
```

#### `<pre>`
Preformatted text (preserves spaces and line breaks).

```html
<pre>
    This    preserves
        all   formatting
</pre>
```

---

## 4. Textual Tags

### Grouping Text

#### `<div>`
Block-level container for grouping content.

```html
<div class="container">
    <p>Content here</p>
</div>
```

#### `<span>`
Inline container for styling or grouping text.

```html
<p>This is <span style="color: red;">red text</span>.</p>
```

### Standard Attributes

#### `id`
Unique identifier for an element.

```html
<div id="header"></div>
```

#### `class`
One or more class names for styling.

```html
<p class="important highlight">Text</p>
```

#### `style`
Inline CSS styling.

```html
<p style="color: blue; font-size: 16px;">Styled text</p>
```

#### Data Attributes
Custom data attributes for storing extra information.

```html
<div data-user-id="12345" data-role="admin">User Info</div>
```

### Links

#### `<a>`
Anchor tag for hyperlinks.

```html
<!-- External link -->
<a href="https://example.com">Visit Example</a>

<!-- Link in new tab -->
<a href="https://example.com" target="_blank">Open in new tab</a>

<!-- Email link -->
<a href="mailto:email@example.com">Send Email</a>

<!-- Phone link -->
<a href="tel:+1234567890">Call Us</a>

<!-- Anchor link (same page) -->
<a href="#section1">Go to Section 1</a>

<!-- Download link -->
<a href="file.pdf" download>Download PDF</a>
```

---

## 5. Lists and Types

### Ordered Lists

Numbered list using `<ol>`.

```html
<ol>
    <li>First item</li>
    <li>Second item</li>
    <li>Third item</li>
</ol>
```

**Output:**
1. First item
2. Second item
3. Third item

### Unordered Lists

Bulleted list using `<ul>`.

```html
<ul>
    <li>Item one</li>
    <li>Item two</li>
    <li>Item three</li>
</ul>
```

**Output:**
- Item one
- Item two
- Item three

### Definition Lists

List of terms and descriptions.

```html
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language</dd>

    <dt>CSS</dt>
    <dd>Cascading Style Sheets</dd>

    <dt>JavaScript</dt>
    <dd>Programming language for web interactivity</dd>
</dl>
```

### Nested Lists

```html
<ul>
    <li>Item 1
        <ul>
            <li>Sub-item 1.1</li>
            <li>Sub-item 1.2</li>
        </ul>
    </li>
    <li>Item 2</li>
    <li>Item 3
        <ol>
            <li>Nested ordered item</li>
        </ol>
    </li>
</ul>
```

---

## 6. Table Tag

### Basic Table Structure

```html
<table>
    <thead>
        <tr>
            <th>Header 1</th>
            <th>Header 2</th>
            <th>Header 3</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Row 1, Cell 1</td>
            <td>Row 1, Cell 2</td>
            <td>Row 1, Cell 3</td>
        </tr>
        <tr>
            <td>Row 2, Cell 1</td>
            <td>Row 2, Cell 2</td>
            <td>Row 2, Cell 3</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td colspan="3">Footer content</td>
        </tr>
    </tfoot>
</table>
```

### Table Tags

| Tag | Description |
|-----|-------------|
| `<table>` | Defines a table |
| `<thead>` | Table header section |
| `<tbody>` | Table body section |
| `<tfoot>` | Table footer section |
| `<tr>` | Table row |
| `<th>` | Table header cell |
| `<td>` | Table data cell |
| `<caption>` | Table caption |
| `<colgroup>` | Group of columns |
| `<col>` | Column properties |

### Spanning Cells

```html
<!-- Colspan - spans across columns -->
<td colspan="2">Spans 2 columns</td>

<!-- Rowspan - spans across rows -->
<td rowspan="3">Spans 3 rows</td>
```

### Complete Example

```html
<table border="1">
    <caption>Monthly Sales Report</caption>
    <thead>
        <tr>
            <th>Month</th>
            <th>Sales</th>
            <th>Revenue</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>January</td>
            <td>100</td>
            <td>$10,000</td>
        </tr>
        <tr>
            <td>February</td>
            <td>150</td>
            <td>$15,000</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>Total</td>
            <td>250</td>
            <td>$25,000</td>
        </tr>
    </tfoot>
</table>
```

---

## 7. Embedding Media

### Images

#### `<img>`
Embeds an image (self-closing tag).

```html
<img src="image.jpg" alt="Description of image" width="300" height="200">
```

**Important attributes:**
- `src` - Image source URL (required)
- `alt` - Alternative text for accessibility (required)
- `width` - Image width
- `height` - Image height
- `loading` - Lazy loading (`lazy` or `eager`)
- `fetchpriority` - Loading priority (`high`, `low`, `auto`)

#### `<figure>` and `<figcaption>`
Semantic way to group images with captions.

```html
<figure>
    <img src="photo.jpg" alt="A beautiful sunset">
    <figcaption>A beautiful sunset over the ocean</figcaption>
</figure>
```

#### img vs figure

- Use `<img>` for simple images
- Use `<figure>` when you need to associate a caption with the image or when the image is a self-contained unit of content

#### Priority Hints

Control resource loading priority.

```html
<!-- High priority (above-the-fold images) -->
<img src="hero.jpg" alt="Hero" fetchpriority="high">

<!-- Lazy loading (below-the-fold images) -->
<img src="thumbnail.jpg" alt="Thumbnail" loading="lazy">
```

### Audio

```html
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    <source src="audio.ogg" type="audio/ogg">
    Your browser does not support the audio element.
</audio>
```

**Attributes:**
- `controls` - Show playback controls
- `autoplay` - Start playing automatically
- `loop` - Loop the audio
- `muted` - Start muted
- `preload` - `auto`, `metadata`, or `none`

### Video

```html
<video width="640" height="360" controls>
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
    <track src="subtitles_en.vtt" kind="subtitles" srclang="en" label="English">
    Your browser does not support the video tag.
</video>
```

**Attributes:**
- `controls` - Show playback controls
- `autoplay` - Start playing automatically
- `loop` - Loop the video
- `muted` - Start muted
- `poster` - Image shown before video plays
- `preload` - `auto`, `metadata`, or `none`

### iframe

Embeds another webpage or content.

```html
<iframe src="https://example.com" width="600" height="400" title="Example Website"></iframe>

<!-- YouTube video embed -->
<iframe width="560" height="315"
    src="https://www.youtube.com/embed/VIDEO_ID"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen>
</iframe>
```

### CSP (Content Security Policy)

Security feature to prevent XSS attacks.

```html
<meta http-equiv="Content-Security-Policy"
      content="default-src 'self'; script-src 'self' https://trusted.com">
```

---

## 8. Using Forms

### Basic Form Structure

```html
<form action="/submit" method="POST">
    <!-- Form elements go here -->
</form>
```

**Form attributes:**
- `action` - URL where form data is sent
- `method` - HTTP method (`GET` or `POST`)
- `enctype` - Encoding type (use `multipart/form-data` for file uploads)
- `autocomplete` - Enable/disable autocomplete
- `novalidate` - Disable HTML5 validation

### Labels and Inputs

#### Text Input

```html
<label for="username">Username:</label>
<input type="text" id="username" name="username" placeholder="Enter username">
```

### Common Input Types

```html
<!-- Email -->
<input type="email" name="email" required>

<!-- Password -->
<input type="password" name="password">

<!-- Number -->
<input type="number" name="age" min="0" max="120">

<!-- Date -->
<input type="date" name="birthdate">

<!-- Time -->
<input type="time" name="appointment">

<!-- Color picker -->
<input type="color" name="favcolor">

<!-- Range slider -->
<input type="range" name="volume" min="0" max="100">

<!-- URL -->
<input type="url" name="website">

<!-- Tel -->
<input type="tel" name="phone">

<!-- Search -->
<input type="search" name="query">

<!-- Hidden -->
<input type="hidden" name="user_id" value="12345">
```

### Checkbox

```html
<input type="checkbox" name="subscribe" id="subscribe" value="yes">
<label for="subscribe">Subscribe to newsletter</label>

<!-- Multiple checkboxes -->
<fieldset>
    <legend>Select your interests:</legend>
    <input type="checkbox" name="interests" value="sports" id="sports">
    <label for="sports">Sports</label>

    <input type="checkbox" name="interests" value="music" id="music">
    <label for="music">Music</label>
</fieldset>
```

### Radio Buttons

```html
<fieldset>
    <legend>Gender:</legend>
    <input type="radio" name="gender" value="male" id="male">
    <label for="male">Male</label>

    <input type="radio" name="gender" value="female" id="female">
    <label for="female">Female</label>

    <input type="radio" name="gender" value="other" id="other">
    <label for="other">Other</label>
</fieldset>
```

### Textarea

```html
<label for="message">Message:</label>
<textarea name="message" id="message" rows="4" cols="50" placeholder="Enter your message"></textarea>
```

### Select Dropdown

```html
<!-- Single select -->
<label for="country">Country:</label>
<select name="country" id="country">
    <option value="">-- Select --</option>
    <option value="us">United States</option>
    <option value="uk">United Kingdom</option>
    <option value="ca">Canada</option>
</select>

<!-- Multiple select -->
<select name="languages" multiple>
    <option value="html">HTML</option>
    <option value="css">CSS</option>
    <option value="js">JavaScript</option>
</select>

<!-- Grouped options -->
<select name="category">
    <optgroup label="Fruits">
        <option value="apple">Apple</option>
        <option value="banana">Banana</option>
    </optgroup>
    <optgroup label="Vegetables">
        <option value="carrot">Carrot</option>
        <option value="potato">Potato</option>
    </optgroup>
</select>
```

### Buttons

```html
<!-- Submit button -->
<button type="submit">Submit</button>
<input type="submit" value="Submit">

<!-- Reset button -->
<button type="reset">Reset</button>

<!-- Regular button -->
<button type="button" onclick="doSomething()">Click Me</button>
```

### File Uploads

```html
<form action="/upload" method="POST" enctype="multipart/form-data">
    <label for="file">Choose file:</label>
    <input type="file" id="file" name="file" accept=".jpg,.png,.pdf">

    <!-- Multiple files -->
    <input type="file" name="files" multiple>

    <button type="submit">Upload</button>
</form>
```

### Form Validation

```html
<!-- Required field -->
<input type="text" name="username" required>

<!-- Pattern validation -->
<input type="text" name="code" pattern="[A-Za-z]{3}" title="3 letter code">

<!-- Min/Max length -->
<input type="text" name="username" minlength="3" maxlength="20">

<!-- Email validation -->
<input type="email" name="email" required>

<!-- Number range -->
<input type="number" name="age" min="18" max="100">

<!-- Custom validation message -->
<input type="text" name="username" required
       oninvalid="this.setCustomValidity('Please enter your username')"
       oninput="this.setCustomValidity('')">
```

### Complete Form Example

```html
<form action="/register" method="POST">
    <fieldset>
        <legend>Registration Form</legend>

        <label for="username">Username:</label>
        <input type="text" id="username" name="username" required minlength="3">

        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required>

        <label for="password">Password:</label>
        <input type="password" id="password" name="password" required minlength="8">

        <label for="age">Age:</label>
        <input type="number" id="age" name="age" min="13" max="120">

        <label for="country">Country:</label>
        <select id="country" name="country" required>
            <option value="">-- Select --</option>
            <option value="us">United States</option>
            <option value="uk">United Kingdom</option>
        </select>

        <input type="checkbox" id="terms" name="terms" required>
        <label for="terms">I agree to the terms and conditions</label>

        <button type="submit">Register</button>
    </fieldset>
</form>
```

### Limitations

**HTML Validation Limitations:**
- Client-side validation can be bypassed
- Always validate on the server side
- Limited customization of error messages
- Not all browsers support all HTML5 validation features
- Regex patterns can be complex and hard to maintain

---

## 9. Semantic Markup

### Layout Tags

Semantic HTML5 elements that give meaning to your page structure.

#### `<header>`
Introductory content or navigation.

```html
<header>
    <h1>Site Title</h1>
    <nav>
        <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/about">About</a></li>
        </ul>
    </nav>
</header>
```

#### `<nav>`
Navigation links.

```html
<nav>
    <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/about">About</a></li>
        <li><a href="/services">Services</a></li>
        <li><a href="/contact">Contact</a></li>
    </ul>
</nav>
```

#### `<main>`
Main content of the document (only one per page).

```html
<main>
    <h1>Page Title</h1>
    <article>
        <!-- Article content -->
    </article>
</main>
```

#### `<article>`
Self-contained content that could be distributed independently.

```html
<article>
    <h2>Article Title</h2>
    <p>Published on <time datetime="2026-01-13">January 13, 2026</time></p>
    <p>Article content...</p>
</article>
```

#### `<section>`
Thematic grouping of content.

```html
<section>
    <h2>Section Title</h2>
    <p>Section content...</p>
</section>
```

#### `<aside>`
Tangentially related content (sidebar, callouts).

```html
<aside>
    <h3>Related Links</h3>
    <ul>
        <li><a href="#">Link 1</a></li>
        <li><a href="#">Link 2</a></li>
    </ul>
</aside>
```

#### `<footer>`
Footer for a section or page.

```html
<footer>
    <p>&copy; 2026 My Website. All rights reserved.</p>
    <nav>
        <a href="/privacy">Privacy Policy</a> |
        <a href="/terms">Terms of Service</a>
    </nav>
</footer>
```

### Complete Semantic Page Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Semantic HTML Example</title>
</head>
<body>
    <header>
        <h1>Website Name</h1>
        <nav>
            <ul>
                <li><a href="/">Home</a></li>
                <li><a href="/about">About</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <article>
            <h2>Article Title</h2>
            <p>Article content...</p>
        </article>

        <section>
            <h2>Section Title</h2>
            <p>Section content...</p>
        </section>
    </main>

    <aside>
        <h3>Sidebar</h3>
        <p>Additional information...</p>
    </aside>

    <footer>
        <p>&copy; 2026 Website Name</p>
    </footer>
</body>
</html>
```

### Highlighting Changes

#### `<del>`
Deleted text (strikethrough).

```html
<p>Price: <del>$50</del> $30</p>
```

#### `<s>`
Text that is no longer accurate or relevant.

```html
<s>Out of stock</s>
```

#### `<ins>`
Inserted text (underlined).

```html
<p>My favorite color is <del>blue</del> <ins>red</ins>.</p>
```

### Quotation / Citation

#### `<blockquote>`
Block-level quotation.

```html
<blockquote cite="https://example.com">
    <p>This is a long quotation that spans multiple lines.</p>
</blockquote>
```

#### `<q>`
Inline quotation (adds quotation marks).

```html
<p>He said, <q>Hello world</q> and smiled.</p>
```

#### `<cite>`
Citation or reference to a creative work.

```html
<p><cite>The Great Gatsby</cite> by F. Scott Fitzgerald</p>
```

#### `<abbr>`
Abbreviation or acronym.

```html
<p><abbr title="HyperText Markup Language">HTML</abbr> is a markup language.</p>
```

#### `<dfn>`
Definition term.

```html
<p><dfn>HTML</dfn> is a markup language for web pages.</p>
```

#### `<address>`
Contact information.

```html
<address>
    Written by <a href="mailto:webmaster@example.com">John Doe</a>.<br>
    Visit us at: example.com<br>
    123 Main Street, City, Country
</address>
```

### Other Semantic Tags

```html
<!-- Code snippets -->
<code>const x = 10;</code>

<!-- Keyboard input -->
<kbd>Ctrl</kbd> + <kbd>C</kbd>

<!-- Sample output -->
<samp>Error: File not found</samp>

<!-- Variable -->
<var>x</var> = 5

<!-- Time -->
<time datetime="2026-01-13">January 13, 2026</time>

<!-- Progress bar -->
<progress value="70" max="100">70%</progress>

<!-- Meter -->
<meter value="0.7">70%</meter>

<!-- Details/Summary (collapsible) -->
<details>
    <summary>Click to expand</summary>
    <p>Hidden content goes here.</p>
</details>
```

---

## 10. Styling Basics

### Inline CSS

Styles applied directly to an element using the style attribute.

```html
<p style="color: red; font-size: 18px; font-weight: bold;">
    Styled text
</p>
```

**Note:** Inline styles have the highest specificity but are hard to maintain. Use sparingly.

### Internal CSS

Styles defined in a `<style>` tag within the `<head>`.

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }

        h1 {
            color: #333;
            text-align: center;
        }

        .highlight {
            background-color: yellow;
            padding: 5px;
        }

        #header {
            background-color: #007bff;
            color: white;
            padding: 20px;
        }
    </style>
</head>
<body>
    <div id="header">
        <h1>Welcome</h1>
    </div>
    <p class="highlight">This is highlighted text.</p>
</body>
</html>
```

### External CSS

Styles defined in a separate CSS file.

```html
<head>
    <link rel="stylesheet" href="styles.css">
    <link rel="stylesheet" href="responsive.css">
</head>
```

**styles.css:**
```css
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}

h1 {
    color: #333;
}

.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
}
```

**Best Practice:** Use external CSS files for better organization, reusability, and caching.

### CSS Specificity Order

1. Inline styles (highest)
2. IDs
3. Classes, attributes, pseudo-classes
4. Elements, pseudo-elements (lowest)

---

## 11. Including JavaScript

### Inline JavaScript

```html
<button onclick="alert('Hello!')">Click Me</button>

<a href="javascript:void(0)" onclick="doSomething()">Link</a>
```

**Note:** Inline JavaScript is not recommended for maintainability and security reasons.

### Internal JavaScript

```html
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript Example</title>
</head>
<body>
    <h1 id="heading">Hello World</h1>
    <button id="btn">Click Me</button>

    <script>
        console.log('Page loaded');

        document.getElementById('btn').addEventListener('click', function() {
            document.getElementById('heading').textContent = 'Button Clicked!';
        });
    </script>
</body>
</html>
```

### External JavaScript

```html
<!DOCTYPE html>
<html>
<head>
    <title>External JS Example</title>
    <!-- In head (blocks rendering) -->
    <script src="script.js"></script>
</head>
<body>
    <h1>Hello World</h1>

    <!-- Before closing body (recommended) -->
    <script src="script.js"></script>
</body>
</html>
```

### Script Loading Strategies

```html
<!-- Defer: Downloads asynchronously, executes after HTML parsing -->
<script src="script.js" defer></script>

<!-- Async: Downloads and executes asynchronously -->
<script src="script.js" async></script>

<!-- Module: Treats file as ES6 module -->
<script type="module" src="script.js"></script>

<!-- No blocking (traditional way) -->
<body>
    <!-- Content -->
    <script src="script.js"></script>
</body>
```

**Comparison:**

| Method | Download | Execution | Use Case |
|--------|----------|-----------|----------|
| Normal | Blocks HTML parsing | Immediately | Small scripts, dependencies |
| `defer` | Async, parallel | After HTML parsing, in order | Most scripts |
| `async` | Async, parallel | As soon as downloaded | Independent scripts, analytics |

**Best Practice:** Use `defer` for most scripts to avoid blocking page rendering.

---

## 12. Accessibility

### Core Principles (WCAG)

1. **Perceivable** - Information must be presentable to users
2. **Operable** - UI components must be operable
3. **Understandable** - Information and operation must be understandable
4. **Robust** - Content must be robust enough for assistive technologies

### Best Practices

#### Use Semantic HTML

```html
<!-- Good: Semantic and accessible -->
<button>Click Me</button>
<nav>Navigation</nav>
<main>Main content</main>

<!-- Bad: Non-semantic -->
<div onclick="doSomething()">Click Me</div>
<div>Navigation</div>
<div>Main content</div>
```

#### Alt Text for Images

```html
<!-- Descriptive image -->
<img src="logo.png" alt="Company Logo">

<!-- Decorative image (empty alt) -->
<img src="decorative.png" alt="">

<!-- Complex image -->
<img src="chart.png" alt="Bar chart showing sales increased 50% in Q4">
```

#### Form Labels

```html
<!-- Always associate labels with inputs -->
<label for="email">Email Address:</label>
<input type="email" id="email" name="email">

<!-- Or wrap the input -->
<label>
    Email Address:
    <input type="email" name="email">
</label>
```

#### ARIA Attributes

```html
<!-- Button with aria-label -->
<button aria-label="Close dialog">X</button>

<!-- Navigation with aria-label -->
<nav aria-label="Main navigation">...</nav>

<!-- Live region for dynamic content -->
<div role="alert" aria-live="polite">Error message</div>

<!-- Expandable section -->
<button aria-expanded="false" aria-controls="menu">Menu</button>
<div id="menu" hidden>Menu items...</div>

<!-- Required field -->
<input type="text" aria-required="true">

<!-- Invalid field -->
<input type="email" aria-invalid="true" aria-describedby="email-error">
<span id="email-error">Please enter a valid email</span>
```

#### Keyboard Navigation

```html
<!-- Ensure interactive elements are keyboard accessible -->
<button tabindex="0">Accessible Button</button>

<!-- Skip navigation for keyboard users -->
<a href="#main-content" class="skip-link">Skip to main content</a>

<!-- Modal with focus trap -->
<div role="dialog" aria-labelledby="dialog-title" aria-modal="true">
    <h2 id="dialog-title">Dialog Title</h2>
    <button>Close</button>
</div>
```

#### Color Contrast

- WCAG AA: Minimum contrast ratio of 4.5:1 for normal text
- WCAG AAA: Minimum contrast ratio of 7:1 for normal text
- Large text (18pt+): 3:1 ratio for AA

#### Accessible Links

```html
<!-- Good: Descriptive link text -->
<a href="/about">Learn more about our company</a>

<!-- Bad: Vague link text -->
<a href="/about">Click here</a>

<!-- Screen reader only text -->
<a href="/report.pdf">
    Download Report
    <span class="sr-only">(PDF, 2MB)</span>
</a>
```

#### Language Declaration

```html
<html lang="en">

<!-- For mixed language content -->
<p>The French word <span lang="fr">bonjour</span> means hello.</p>
```

#### Page Structure

```html
<!-- Logical heading hierarchy -->
<h1>Main Page Title</h1>
<h2>Section 1</h2>
<h3>Subsection 1.1</h3>
<h3>Subsection 1.2</h3>
<h2>Section 2</h2>

<!-- Skip to main content -->
<body>
    <a href="#main-content" class="skip-link">Skip to main content</a>
    <header>...</header>
    <main id="main-content">...</main>
</body>
```

#### Accessible Forms

```html
<form>
    <fieldset>
        <legend>Personal Information</legend>

        <label for="name">Name (required):</label>
        <input type="text" id="name" name="name" required aria-required="true">

        <label for="email">Email:</label>
        <input type="email" id="email" name="email" aria-describedby="email-help">
        <span id="email-help">We'll never share your email</span>
    </fieldset>
</form>
```

---

## 13. Basics of SEO

### Meta Tags

```html
<head>
    <!-- Title (most important for SEO) -->
    <title>Page Title | Site Name (50-60 characters)</title>

    <!-- Meta description -->
    <meta name="description" content="Clear, concise page description (150-160 characters)">

    <!-- Meta keywords (less important nowadays) -->
    <meta name="keywords" content="keyword1, keyword2, keyword3">

    <!-- Viewport for mobile -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!-- Character encoding -->
    <meta charset="UTF-8">

    <!-- Canonical URL (prevent duplicate content) -->
    <link rel="canonical" href="https://example.com/page">

    <!-- Robots meta tag -->
    <meta name="robots" content="index, follow">

    <!-- Author -->
    <meta name="author" content="Author Name">
</head>
```

### Open Graph (Social Media)

```html
<!-- Open Graph for Facebook, LinkedIn -->
<meta property="og:title" content="Page Title">
<meta property="og:description" content="Page description">
<meta property="og:image" content="https://example.com/image.jpg">
<meta property="og:url" content="https://example.com/page">
<meta property="og:type" content="website">
<meta property="og:site_name" content="Site Name">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:site" content="@username">
<meta name="twitter:title" content="Page Title">
<meta name="twitter:description" content="Page description">
<meta name="twitter:image" content="https://example.com/image.jpg">
```

### SEO Best Practices

#### 1. Semantic HTML Structure

Use proper heading hierarchy and semantic tags.

```html
<h1>Main Page Title (only one per page)</h1>
<h2>Section Heading</h2>
<h3>Subsection Heading</h3>
```

#### 2. Clean URLs

```html
<!-- Good: Descriptive URLs -->
https://example.com/products/red-shoes
https://example.com/blog/seo-tips

<!-- Bad: Non-descriptive URLs -->
https://example.com/page?id=123&cat=45
https://example.com/product/12345
```

#### 3. Image Optimization

```html
<img src="red-shoes.jpg"
     alt="Red running shoes with white stripes"
     width="800"
     height="600"
     loading="lazy">
```

**Image SEO Tips:**
- Use descriptive file names
- Add descriptive alt text
- Compress images for faster loading
- Use appropriate image formats (WebP, JPEG, PNG)
- Specify dimensions to prevent layout shift

#### 4. Internal Linking

```html
<!-- Link to related pages with descriptive anchor text -->
<a href="/related-article">Learn more about HTML semantics</a>

<!-- Breadcrumb navigation -->
<nav aria-label="Breadcrumb">
    <ol>
        <li><a href="/">Home</a></li>
        <li><a href="/category">Category</a></li>
        <li aria-current="page">Current Page</li>
    </ol>
</nav>
```

#### 5. Mobile-Friendly

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

#### 6. Page Speed Optimization

```html
<!-- Preload critical resources -->
<link rel="preload" href="critical.css" as="style">
<link rel="preload" href="font.woff2" as="font" type="font/woff2" crossorigin>

<!-- Preconnect to external domains -->
<link rel="preconnect" href="https://fonts.googleapis.com">

<!-- DNS prefetch -->
<link rel="dns-prefetch" href="https://cdn.example.com">

<!-- Lazy load images and iframes -->
<img src="image.jpg" loading="lazy">
<iframe src="video.html" loading="lazy"></iframe>

<!-- Defer non-critical JavaScript -->
<script src="script.js" defer></script>
```

#### 7. Structured Data (Schema.org)

```html
<!-- JSON-LD format -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Article Title",
  "description": "Article description",
  "image": "https://example.com/image.jpg",
  "author": {
    "@type": "Person",
    "name": "John Doe"
  },
  "datePublished": "2026-01-13",
  "dateModified": "2026-01-13"
}
</script>

<!-- Organization schema -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Company Name",
  "url": "https://example.com",
  "logo": "https://example.com/logo.png",
  "contactPoint": {
    "@type": "ContactPoint",
    "telephone": "+1-123-456-7890",
    "contactType": "Customer Service"
  }
}
</script>
```

#### 8. Content Quality

- Write unique, valuable content
- Use keywords naturally (don't keyword stuff)
- Keep content updated
- Use headings to structure content
- Write for humans, not just search engines

#### 9. HTML Sitemap

```html
<nav aria-label="Site map">
    <h2>Sitemap</h2>
    <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/about">About</a>
            <ul>
                <li><a href="/about/team">Team</a></li>
                <li><a href="/about/history">History</a></li>
            </ul>
        </li>
        <li><a href="/products">Products</a></li>
        <li><a href="/contact">Contact</a></li>
    </ul>
</nav>
```

#### 10. XML Sitemap

Create an XML sitemap file (sitemap.xml) and reference it:

```html
<head>
    <link rel="sitemap" type="application/xml" href="/sitemap.xml">
</head>
```

---

## Quick Reference

### Most Common Tags

| Tag | Purpose |
|-----|---------|
| `<div>` | Block container |
| `<span>` | Inline container |
| `<p>` | Paragraph |
| `<a>` | Link |
| `<img>` | Image |
| `<h1>` - `<h6>` | Headings |
| `<ul>`, `<ol>`, `<li>` | Lists |
| `<table>`, `<tr>`, `<td>` | Tables |
| `<form>`, `<input>` | Forms |
| `<button>` | Button |

### Document Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

</body>
</html>
```

### Common Attributes

| Attribute | Purpose |
|-----------|---------|
| `id` | Unique identifier |
| `class` | CSS class names |
| `style` | Inline styles |
| `src` | Source URL |
| `href` | Link URL |
| `alt` | Alternative text |
| `title` | Tooltip text |
| `data-*` | Custom data |

---

## Additional Resources

- **MDN Web Docs:** https://developer.mozilla.org/en-US/docs/Web/HTML
- **W3Schools:** https://www.w3schools.com/html/
- **HTML Living Standard:** https://html.spec.whatwg.org/
- **W3C HTML Validator:** https://validator.w3.org/
- **Frontend Developer Roadmap:** https://roadmap.sh/frontend
- **JavaScript Roadmap:** https://roadmap.sh/javascript
- **Can I Use (Browser Support):** https://caniuse.com/

---

## Frontend Learning Path

1. **HTML** - Structure (You are here!)
2. **CSS** - Styling and layout
3. **JavaScript** - Interactivity and logic
4. **Responsive Design** - Mobile-first approach
5. **Frameworks** - React, Vue, Angular
6. **Build Tools** - Webpack, Vite, npm
7. **Version Control** - Git, GitHub
8. **Testing** - Jest, Cypress
9. **Performance** - Optimization techniques
10. **Accessibility** - WCAG compliance

---

**Created from roadmap.sh HTML Roadmap**

Keep learning and building amazing websites!