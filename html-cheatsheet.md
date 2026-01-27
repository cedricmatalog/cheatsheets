# Head First HTML Cheatsheet

> Your brain on HTML. Here you'll learn HTML the way your brain likes to learn - with conversational style, puzzles, and practical examples that stick.

---

## How to Use This Cheatsheet

**We think of this as learning, not a reference manual.** You'll find Q&A sections, "Watch It!" warnings, "Brain Power" exercises, and lots of conversation. It might seem strange at first, but your brain will thank you later.

**The activities are NOT optional.** The exercises and challenges are part of the learning experience. Don't skip them.

**The redundancy is intentional.** One distinct difference in a Head First cheatsheet is that we want you to really *get it*. And we want you to finish the guide remembering what you've learned. So you'll see some of the same concepts come up more than once.

---

## Table of Contents

1. [Introduction: How the Web Really Works](#1-introduction-how-the-web-really-works)
2. [Getting Started: Your First HTML File](#2-getting-started-your-first-html-file)
3. [Basic Tags: The Building Blocks](#3-basic-tags-the-building-blocks)
4. [Working with Text: Making Words Come Alive](#4-working-with-text-making-words-come-alive)
5. [Lists: Organizing Information](#5-lists-organizing-information)
6. [Tables: Structured Data](#6-tables-structured-data)
7. [Media Time: Images, Audio, and Video](#7-media-time-images-audio-and-video)
8. [Forms: Talking to Your Users](#8-forms-talking-to-your-users)
9. [Semantic HTML: Meaning Matters](#9-semantic-html-meaning-matters)
10. [Styling: Making It Pretty](#10-styling-making-it-pretty)
11. [JavaScript: Adding Behavior](#11-javascript-adding-behavior)
12. [Accessibility: Building for Everyone](#12-accessibility-building-for-everyone)
13. [SEO: Getting Found](#13-seo-getting-found)

---

## 1. Introduction: How the Web Really Works

### What are markup languages?

Think of a markup language like a highlighter and sticky notes for your text. You're not changing the words - you're adding annotations that say "this is a heading," "this is a paragraph," "this is important."

HTML isn't the only markup language out there:
- **SGML** - The grandparent of HTML (very complex, mostly historical)
- **XML** - A strict, flexible markup language used for data (think config files and APIs)
- **HTML** - Built for web pages (what we're learning!)
- **Markdown** - A lightweight markup for writing (fun fact: this cheatsheet is written in it!)

The key idea? Markup languages *describe* content. They don't *execute* logic. You're telling the computer "what this is," not "what to do."

### Frontend Development: The Big Three

Every webpage you see is built with three technologies working together - think of them as a band:

| Technology | Role | Analogy |
|-----------|------|---------|
| **HTML** | Structure & content | The skeleton |
| **CSS** | Styling & layout | The skin & clothes |
| **JavaScript** | Behavior & interactivity | The muscles & brain |

```
HTML (structure) + CSS (style) + JavaScript (behavior) = Complete Webpage
```

Here's the thing: you can have HTML without CSS or JavaScript (it'll look ugly, but it works!). But you *can't* have a webpage without HTML. It's always the starting point.

### Brain Power
🧠 Open any website, right-click, and hit "View Source." Can you spot where HTML ends and CSS/JavaScript begin? What patterns do you notice?

### What's HTML, anyway?

HTML stands for **HyperText Markup Language**, but what does that actually mean? Think of HTML as the skeleton of every webpage you've ever visited. It's not a programming language (it can't make decisions or do math), but it's incredibly powerful for *structuring* content.

**HyperText** = Text with links (you know, those blue underlined things you click)
**Markup** = Special tags that tell browsers how to display stuff
**Language** = A set of rules for writing those tags

### Brain Power
🧠 Before you read on, think about this: When you visit a webpage, what actually happens? Write down your guess.

### How the web really works (the short version)

1. **You type a URL** in your browser (like `https://example.com`)
2. **DNS translates** the domain name into an IP address (like finding someone's street address from their name)
3. **Your browser sends an HTTP request** to that server (saying "Hey, send me that webpage!")
4. **The server responds** with HTML, CSS, and JavaScript files
5. **Your browser renders** everything into the beautiful (or not so beautiful) page you see

```
You type URL → DNS lookup → HTTP Request → Server responds → Browser renders
```

### Domain names: Your website's address

Imagine if every time you wanted to visit a website, you had to type `172.217.164.110` instead of `google.com`. Yikes! That's why we have domain names - they're human-friendly addresses for websites.

Here's how a URL breaks down:

```
https://blog.example.com/page
  ↑       ↑      ↑      ↑  ↑
protocol subdomain domain TLD path
```

- **TLD (Top-Level Domain):** `.com`, `.org`, `.net`, `.io`, etc.
- **Domain:** The name you buy from a registrar (GoDaddy, Namecheap, etc.)
- **Subdomain:** Optional prefix (like `www`, `blog`, `api`)

You buy domain names from **registrars**, and they cost around $10-50/year. Think of it like renting a street address for your online house.

### Browsers: Your HTML interpreter

You write the HTML, but the **browser** is the one reading it and turning it into something visual. Each browser has its own **rendering engine** (the thing that actually paints pixels on screen):

| Browser | Engine | Notes |
|---------|--------|-------|
| Chrome | Blink | Most popular (~65% market share) |
| Firefox | Gecko | Privacy-focused |
| Safari | WebKit | Apple devices |
| Edge | Blink | Microsoft's browser |

### Sharpen your pencil

Try this right now! Press **F12** (or right-click → "Inspect") on any webpage. You just opened **DevTools** - your new best friend:
- **Elements tab** - See and edit HTML/CSS live (try changing some text!)
- **Console tab** - JavaScript errors and output
- **Network tab** - See every file being loaded
- **Lighthouse tab** - Performance and accessibility audits

Go ahead, break something. You can't hurt anything - just refresh to undo!

### Hosting: Where your website lives

So you've written an amazing HTML page. Now what? It's just sitting on your computer! For the world to see it, your files need to live on a **server** - a computer that's always on and connected to the internet. This is called **hosting**.

| Type | Good For | Examples |
|------|----------|---------|
| **Static hosting** | HTML/CSS/JS only sites | GitHub Pages, Netlify, Vercel |
| **Shared hosting** | Small sites, beginners | Bluehost, HostGator |
| **VPS** | More control, medium traffic | DigitalOcean, Linode |
| **Cloud hosting** | Scalable, high traffic | AWS, Google Cloud, Azure |

**For learning HTML:** Use static hosting! GitHub Pages is free - just push your HTML files to a repository and boom, you have a live website.

### Brain Power
🧠 What's the difference between a domain name and hosting? Think of it this way: if your website were a physical store, which one is the street address and which one is the actual building?

### There are NO Dumb Questions

**Q: What's the difference between HTTP and HTTPS?**
**A:** The 'S' stands for Secure. HTTPS encrypts the data between your browser and the server. Always use HTTPS for anything involving passwords, credit cards, or personal data.

**Q: Do I need to understand DNS to write HTML?**
**A:** Not really! But it helps to know the big picture. Focus on HTML first, you can dive deeper into networking later.

**Q: Is HTML case-sensitive?**
**A:** Nope! `<DIV>`, `<Div>`, and `<div>` are all the same. But the convention is lowercase, so stick with that.

**Q: What's the difference between a domain and hosting?**
**A:** A domain is your address (where people find you). Hosting is the actual building (where your files live). You need both for a live website.

**Q: Does my HTML look different in different browsers?**
**A:** Sometimes! Browsers have slightly different default styles. That's why developers use "CSS resets" to start from a consistent baseline. Always test in multiple browsers.

### Watch It!
⚠️ **Markup languages ≠ Programming languages**. HTML can't make decisions, can't loop, can't do calculations. For that, you need JavaScript. HTML is about structure and content, not logic.

### What you need to get started

- A text editor (Notepad, VS Code, Sublime Text - pick your favorite)
- A web browser (you already have one!)
- Your brain (you've got that too!)

That's it. No special software, no expensive tools. Just text and a browser.

---

## 2. Getting Started: Your First HTML File

### The anatomy of an HTML element

Every HTML element has the same basic structure:

```html
<tagname attribute="value">Content goes here</tagname>
 ↑                          ↑                  ↑
Opening tag            The content        Closing tag
```

Some tags are **self-closing** (they don't have content):

```html
<img src="photo.jpg" alt="My photo">
<br>
<hr>
```

### Brain Power
🧠 Why do you think some tags need closing tags and others don't? What's the pattern?

### Your first HTML file

Let's build a simple webpage. Open your text editor and type this:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My First Webpage</title>
</head>
<body>
    <h1>Hello, World!</h1>
    <p>This is my first webpage. Pretty cool, huh?</p>
</body>
</html>
```

Save it as `index.html` and open it in your browser. Congratulations! You're officially a web developer.

### Let's break it down

```html
<!DOCTYPE html>
```
This tells the browser "Hey, this is HTML5!" Always put this at the very top.

```html
<html lang="en">
```
The root element. Everything goes inside here. `lang="en"` tells screen readers the language is English.

```html
<head>
```
The head contains *metadata* - information about the page, not content that users see.

```html
<meta charset="UTF-8">
```
This ensures your page displays characters correctly (including emojis! 😀)

```html
<title>My First Webpage</title>
```
What shows up in the browser tab. Super important for SEO!

```html
<body>
```
Everything users actually see goes here.

### HTML Entities: Special characters need special treatment

Want to display `<` or `>` on your page? You can't just type them - the browser will think they're tags! Use entities instead:

| What You Want | What You Type | Entity Name |
|---------------|---------------|-------------|
| < | `&lt;` | Less than |
| > | `&gt;` | Greater than |
| & | `&amp;` | Ampersand |
| " | `&quot;` | Quote |
| (space) | `&nbsp;` | Non-breaking space |
| © | `&copy;` | Copyright |

```html
<p>The formula is: 5 &lt; 10 &amp; 10 &gt; 5</p>
<!-- Displays as: The formula is: 5 < 10 & 10 > 5 -->
```

### Comments: Notes to yourself (and other developers)

```html
<!-- This is a comment. Browsers ignore it completely. -->
<!-- Use comments to explain tricky code or leave TODOs -->
```

### Watch It!
⚠️ **Comments are visible in the page source!** Anyone can right-click and "View Source" to see your comments. Don't put passwords or sensitive info in comments.

### Whitespace: The browser's gonna smoosh it anyway

```html
<p>This    has     many     spaces</p>
<p>This has many spaces</p>
```

Both render exactly the same! The browser collapses multiple spaces into one. Same goes for line breaks.

**Want to preserve formatting?** Use the `<pre>` tag:

```html
<pre>
    This    preserves
        all   your
            formatting!
</pre>
```

### Exercise: Fix This HTML

What's wrong with this code?

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Page
</head>
<body>
    <h1>Welcome</h1>
    <p>I love HTML & CSS!</p>
    <img src="photo.jpg">
</body>
```

**Answers:**
1. Missing closing `</title>` tag
2. `&` should be `&amp;`
3. `<img>` should have an `alt` attribute for accessibility
4. Missing closing `</html>` tag

### There are NO Dumb Questions

**Q: Why do I need `<!DOCTYPE html>`? Can't I just skip it?**
**A:** Technically yes, but browsers might render your page in "quirks mode" which causes weird bugs. Just include it. It's one line.

**Q: What's the difference between `<head>` and `<header>`?**
**A:** Totally different! `<head>` is metadata (title, meta tags, links to CSS). `<header>` is a semantic tag for the top of your page content (logo, navigation).

**Q: Can I have multiple `<html>` tags?**
**A:** No! One per page. It's the root element - there can only be one.

---

## 3. Basic Tags: The Building Blocks

Before you build anything complex, you need to know the basic bricks. These tags are the ones you'll use on every single page you ever build - headings for titles, paragraphs for text, and a handful of formatting tags to add emphasis.

### Headings: Size matters

HTML has six levels of headings, from `<h1>` (biggest, most important) to `<h6>` (smallest, least important).

```html
<h1>Most Important - Use Only Once Per Page</h1>
<h2>Major Section Heading</h2>
<h3>Subsection Heading</h3>
<h4>Sub-subsection</h4>
<h5>Rarely Used</h5>
<h6>Almost Never Used</h6>
```

### Watch It!
⚠️ **Don't skip heading levels!** Don't go from `<h1>` to `<h4>`. Screen readers use headings to navigate. Think of them as a table of contents, not font sizes.

### Brain Power
🧠 Why do you think you should only have one `<h1>` per page? Think about SEO and accessibility.

### Paragraphs: The workhorse of the web

```html
<p>This is a paragraph. Most of your text will be in paragraphs.</p>
<p>Each paragraph gets its own line with space above and below.</p>
```

### Line breaks and horizontal rules

```html
<p>First line<br>Second line</p>

<p>Above the line</p>
<hr>
<p>Below the line</p>
```

`<br>` is for line breaks within text. `<hr>` is a horizontal rule (divider).

### Text formatting: Bold, italic, and more

```html
<!-- Bold text -->
<b>This is bold</b>
<strong>This is important (also bold, but with meaning)</strong>

<!-- Italic text -->
<i>This is italic</i>
<em>This is emphasized (also italic, but with meaning)</em>

<!-- Other formatting -->
<mark>Highlighted text</mark>
<small>Fine print</small>
<del>Deleted text</del>
<ins>Inserted text</ins>
<sub>Subscript: H<sub>2</sub>O</sub>
<sup>Superscript: E=mc<sup>2</sup></sup>
```

### b vs strong, i vs em: What's the difference?

**Short answer:** Use `<strong>` and `<em>` instead of `<b>` and `<i>`.

**Longer answer:** `<b>` and `<i>` are *presentational* - they just make text bold/italic. `<strong>` and `<em>` are *semantic* - they convey meaning. Screen readers will emphasize `<strong>` and `<em>` differently. Search engines care about meaning, not presentation.

### Sharpen your pencil

Match the tag to its purpose:

1. `<h1>` → _____
2. `<p>` → _____
3. `<strong>` → _____
4. `<mark>` → _____
5. `<sub>` → _____

A. Highlighted text
B. Main heading
C. Important text
D. Paragraph
E. Subscript

**Answers:** 1-B, 2-D, 3-C, 4-A, 5-E

### There are NO Dumb Questions

**Q: Can I use `<h1>` just to make text bigger?**
**A:** No! Headings convey document structure, not font size. Use CSS for sizing. Screen readers and search engines rely on heading hierarchy to understand your page.

**Q: What's the difference between `<br>` and starting a new `<p>`?**
**A:** `<br>` is a line break within a block of text (like in a poem or address). `<p>` starts a new paragraph with spacing. Don't use `<br><br>` to fake paragraph spacing - use actual `<p>` tags.

**Q: Does formatting like `<strong>` actually help SEO?**
**A:** Slightly! Search engines give a small weight boost to text in `<strong>` and `<em>` tags. But don't abuse it - marking everything as strong helps nothing.

---

## 4. Working with Text: Making Words Come Alive

### The `<div>` and `<span>`: Containers for everything

```html
<div>
    <h2>This is a section</h2>
    <p>Divs are block-level containers.</p>
</div>

<p>You can style <span style="color: red;">individual words</span> with span.</p>
```

**Key difference:**
- `<div>` = Block-level (takes full width, starts on new line)
- `<span>` = Inline (only takes needed width, stays in line)

### Brain Power
🧠 When would you use `<div>` vs `<span>`? Think about layout vs. inline styling.

### The Big Three Attributes: id, class, and style

```html
<!-- id: Unique identifier (only one per page) -->
<div id="header">Site Header</div>

<!-- class: Reusable identifier (use multiple times) -->
<p class="highlight">Important paragraph</p>
<p class="highlight">Another important paragraph</p>

<!-- style: Inline CSS (avoid if possible) -->
<p style="color: blue; font-size: 18px;">Styled text</p>
```

### Watch It!
⚠️ **IDs must be unique!** You can't have two elements with `id="header"`. But you can have a million elements with `class="highlight"`.

### Standard (global) attributes: The universal toolkit

Here's something cool: some attributes work on *any* HTML element. These are called **global attributes**, and they're like a Swiss Army knife you always have in your pocket.

You already know `id`, `class`, and `style`. But check out these other handy ones:

| Attribute | What It Does | Example |
|-----------|-------------|---------|
| `title` | Shows a tooltip on hover | `title="More info"` |
| `hidden` | Hides element completely | `<div hidden>` |
| `tabindex` | Controls keyboard tab order | `tabindex="0"` |
| `contenteditable` | Lets users edit the content! | `contenteditable="true"` |
| `draggable` | Makes element draggable | `draggable="true"` |
| `lang` | Declares element's language | `lang="fr"` |
| `dir` | Text direction (LTR/RTL) | `dir="rtl"` |
| `translate` | Should translators skip this? | `translate="no"` |
| `spellcheck` | Enable browser spell check | `spellcheck="true"` |

```html
<!-- title gives a tooltip - hover over this! -->
<abbr title="HyperText Markup Language">HTML</abbr>

<!-- hidden removes element from view AND accessibility tree -->
<div hidden>This won't show up at all</div>

<!-- contenteditable lets users type right in the element -->
<p contenteditable="true">Click me and start typing!</p>

<!-- tabindex="0" makes any element keyboard-focusable -->
<div tabindex="0">I can receive keyboard focus now</div>
```

### Sharpen your pencil

Try adding `contenteditable="true"` to a `<p>` tag in your HTML file and open it in the browser. Click on it and start typing. Mind blown? Now try `draggable="true"` on an image. What happens when you drag it?

### Watch It!
⚠️ **`hidden` is not security!** It hides elements visually and from screen readers, but anyone can see hidden elements in the source code. Don't hide sensitive data this way.

### Data attributes: Your own custom attributes

Want to store custom data on elements? Use data attributes!

```html
<div data-user-id="12345" data-role="admin" data-status="active">
    User Information
</div>
```

You can access these in JavaScript:
```javascript
let userId = element.dataset.userId; // "12345"
```

### Links: The "hyper" in hypertext

```html
<!-- Basic link -->
<a href="https://example.com">Visit Example</a>

<!-- Open in new tab -->
<a href="https://example.com" target="_blank">Open in new tab</a>

<!-- Email link -->
<a href="mailto:hello@example.com">Send us an email</a>

<!-- Phone link -->
<a href="tel:+1234567890">Call us</a>

<!-- Anchor link (jump to section) -->
<a href="#section2">Jump to Section 2</a>
<!-- Later in the page: -->
<h2 id="section2">Section 2</h2>

<!-- Download link -->
<a href="document.pdf" download>Download PDF</a>
```

### Watch It!
⚠️ **Always use descriptive link text!** Don't write "click here". Write "Download our annual report" instead. It's better for accessibility and SEO.

### There are NO Dumb Questions

**Q: What's `target="_blank"` and why do I see it everywhere?**
**A:** It opens the link in a new tab. Use it for external links, but sparingly - let users decide how to open links.

**Q: Can I have a link inside a link?**
**A:** Nope! Links can't be nested. HTML won't allow it.

**Q: What happens if I link to `#top`?**
**A:** It jumps to the top of the page. You don't need an element with `id="top"` - it's a special anchor.

### Interview: The `<a>` Tag

**Head First: Welcome, `<a>` tag! Thanks for joining us.**

`<a>` Tag: Happy to be here! I'm the most important tag on the web, you know.

**HF: Bold claim! Why do you say that?**

`<a>`: Without me, there's no "hyper" in hypertext. No links, no web. Just isolated documents.

**HF: Fair point. What's your `href` attribute do?**

`<a>`: It's where the link goes! Can be a URL, email, phone number, or anchor. I'm versatile.

**HF: What about `target="_blank"`?**

`<a>`: *Sighs* Look, I'll open a new tab if you insist, but maybe let users decide? They know how to use Ctrl+click.

**HF: Any pet peeves?**

`<a>`: When people write "click here" as link text. Be descriptive! And add `rel="noopener"` with `target="_blank"` for security.

---

## 5. Lists: Organizing Information

Lists are everywhere on the web - navigation menus, feature lists, step-by-step instructions, even this cheatsheet's table of contents. If you can think of it as "a collection of related items," it's probably a list.

### Three types of lists (but you'll use two of them)

1. **Ordered lists** (`<ol>`) - Numbered
2. **Unordered lists** (`<ul>`) - Bulleted
3. **Definition lists** (`<dl>`) - Terms and definitions

### Ordered lists: When sequence matters

```html
<h3>Recipe Instructions:</h3>
<ol>
    <li>Preheat oven to 350°F</li>
    <li>Mix dry ingredients</li>
    <li>Add wet ingredients</li>
    <li>Bake for 30 minutes</li>
</ol>
```

**Output:**
1. Preheat oven to 350°F
2. Mix dry ingredients
3. Add wet ingredients
4. Bake for 30 minutes

### Unordered lists: When order doesn't matter

```html
<h3>Shopping List:</h3>
<ul>
    <li>Milk</li>
    <li>Eggs</li>
    <li>Bread</li>
    <li>Coffee</li>
</ul>
```

**Output:**
- Milk
- Eggs
- Bread
- Coffee

### Brain Power
🧠 When should you use `<ol>` vs `<ul>`? What about navigation menus - ordered or unordered?

### Definition lists: The forgotten list

```html
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language - the structure of web pages</dd>

    <dt>CSS</dt>
    <dd>Cascading Style Sheets - the styling of web pages</dd>

    <dt>JavaScript</dt>
    <dd>The programming language of the web</dd>
</dl>
```

### Nested lists: Lists inside lists

```html
<ul>
    <li>Frontend
        <ul>
            <li>HTML</li>
            <li>CSS</li>
            <li>JavaScript</li>
        </ul>
    </li>
    <li>Backend
        <ul>
            <li>Node.js</li>
            <li>Python</li>
            <li>Ruby</li>
        </ul>
    </li>
</ul>
```

### Watch It!
⚠️ **Only `<li>` can be direct children of `<ul>` or `<ol>`!** Don't put `<p>` or `<div>` directly inside. Put them inside the `<li>` instead.

```html
<!-- Wrong! -->
<ul>
    <p>Don't do this</p>
</ul>

<!-- Right! -->
<ul>
    <li><p>Do this instead</p></li>
</ul>
```

### Exercise: Build a nested list

Create a nested list showing:
- Web Technologies
  - HTML
  - CSS
  - JavaScript
    - React
    - Vue
    - Angular

**Your code here:**
```html
<!-- Try it yourself before looking at the answer! -->
```

**Answer:**
```html
<ul>
    <li>Web Technologies
        <ul>
            <li>HTML</li>
            <li>CSS</li>
            <li>JavaScript
                <ul>
                    <li>React</li>
                    <li>Vue</li>
                    <li>Angular</li>
                </ul>
            </li>
        </ul>
    </li>
</ul>
```

### There are NO Dumb Questions

**Q: Should navigation menus use `<ul>` or `<ol>`?**
**A:** `<ul>` (unordered list)! Navigation items don't have a sequence. Screen readers announce "list with 5 items," which helps users understand the menu structure.

**Q: Can I put anything inside an `<li>`?**
**A:** Yes! List items can contain paragraphs, images, links, even other lists. That's how nested lists work - a `<ul>` or `<ol>` inside an `<li>`.

**Q: Why not just use `<br>` tags to make a list?**
**A:** Semantics! A real list tells browsers and screen readers "these items are related." Line breaks are just visual - they carry no meaning. Plus, lists are way easier to style with CSS.

---

## 6. Tables: Structured Data

### When to use tables

**Good uses:**
- Actual tabular data (spreadsheet-like info)
- Calendars
- Pricing comparisons
- Sports scores

**Bad uses:**
- Page layout (that's what CSS is for!)
- Anything that's not actually data

### Basic table anatomy

```html
<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Age</th>
            <th>City</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Alice</td>
            <td>25</td>
            <td>New York</td>
        </tr>
        <tr>
            <td>Bob</td>
            <td>30</td>
            <td>London</td>
        </tr>
    </tbody>
</table>
```

### Table tags exposed

| Tag | What It Does |
|-----|--------------|
| `<table>` | Wraps the entire table |
| `<thead>` | Table header section (optional but recommended) |
| `<tbody>` | Table body section (optional but recommended) |
| `<tfoot>` | Table footer section (for totals, etc.) |
| `<tr>` | Table row |
| `<th>` | Table header cell (bold and centered by default) |
| `<td>` | Table data cell |
| `<caption>` | Table title/caption |

### Brain Power
🧠 Why have separate `<thead>`, `<tbody>`, and `<tfoot>` sections? Think about printing long tables...

### Spanning cells: colspan and rowspan

```html
<table border="1">
    <tr>
        <th colspan="2">Name</th>
        <th>Age</th>
    </tr>
    <tr>
        <td>First</td>
        <td>Last</td>
        <td rowspan="2">25</td>
    </tr>
    <tr>
        <td>Alice</td>
        <td>Smith</td>
    </tr>
</table>
```

**colspan** = spans across columns (horizontal)
**rowspan** = spans across rows (vertical)

### Complete table example

```html
<table>
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
        <tr>
            <td>March</td>
            <td>200</td>
            <td>$20,000</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <th>Total</th>
            <td>450</td>
            <td>$45,000</td>
        </tr>
    </tfoot>
</table>
```

### Watch It!
⚠️ **Tables are NOT responsive by default.** On mobile, wide tables will break your layout. You'll need CSS to make them mobile-friendly.

### There are NO Dumb Questions

**Q: Why use `<th>` instead of `<td>` for headers?**
**A:** Accessibility! Screen readers announce header cells differently. Plus, browsers style them bold and centered by default.

**Q: Can I nest tables?**
**A:** Yes, but... just because you *can* doesn't mean you *should*. It gets messy fast. Consider restructuring your data instead.

**Q: What happened to the `border` attribute? I see it in old code.**
**A:** It's deprecated (not recommended). Use CSS instead: `table { border: 1px solid black; }`

---

## 7. Media Time: Images, Audio, and Video

### Images: A picture is worth 1,000 words (or bytes)

```html
<img src="photo.jpg" alt="A sunset over the ocean" width="800" height="600">
```

### The src and alt attributes are REQUIRED

**src** = Source URL of the image
**alt** = Alternative text (for screen readers and when images don't load)

### Watch It!
⚠️ **Always, ALWAYS include `alt` text!** It's crucial for accessibility. Describe what's in the image. If it's decorative, use an empty alt: `alt=""`.

### Image formats: Which one should I use?

| Format | Best For | File Size |
|--------|----------|-----------|
| JPEG | Photos, complex images | Medium |
| PNG | Graphics, transparency | Larger |
| SVG | Logos, icons, scalable graphics | Small |
| WebP | Modern alternative (smaller files) | Smallest |
| GIF | Simple animations | Small |

### Lazy loading: Don't load images until needed

```html
<img src="hero.jpg" alt="Hero image" loading="eager">
<img src="footer-image.jpg" alt="Footer" loading="lazy">
```

- `loading="eager"` = Load immediately (default, for above-the-fold images)
- `loading="lazy"` = Load when scrolled into view (for below-the-fold images)

### Priority hints: Tell the browser what's important

```html
<!-- High priority (critical for LCP) -->
<img src="hero.jpg" alt="Hero" fetchpriority="high">

<!-- Low priority (not critical) -->
<img src="thumbnail.jpg" alt="Thumbnail" fetchpriority="low">
```

### Figure and figcaption: Images with captions

```html
<figure>
    <img src="chart.png" alt="Sales increased 50% in Q4">
    <figcaption>Figure 1: Q4 Sales Growth</figcaption>
</figure>
```

### img vs figure: When to use which?

**Use `<img>` when:**
- Simple image, no caption needed
- Image is part of the text flow
- Decorative images

**Use `<figure>` when:**
- Image has a caption
- Image is a self-contained unit
- Diagrams, charts, code examples with captions

### Brain Power
🧠 Why do you think lazy loading improves page performance? What happens to images "below the fold"?

### Audio: Making noise on the web

```html
<audio controls>
    <source src="song.mp3" type="audio/mpeg">
    <source src="song.ogg" type="audio/ogg">
    Your browser doesn't support audio playback.
</audio>
```

### Audio attributes you should know

```html
<audio controls autoplay loop muted preload="auto">
    <source src="audio.mp3" type="audio/mpeg">
</audio>
```

- `controls` = Show play/pause/volume controls
- `autoplay` = Start playing automatically (annoying, use sparingly!)
- `loop` = Repeat forever
- `muted` = Start muted (required if using autoplay)
- `preload` = "auto", "metadata", or "none"

### Watch It!
⚠️ **Autoplaying audio is annoying!** Most browsers block autoplay unless the audio is muted. Don't be that person.

### Video: YouTube isn't your only option

```html
<video width="640" height="360" controls poster="preview.jpg">
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
    <track src="subtitles.vtt" kind="subtitles" srclang="en" label="English">
    Your browser doesn't support video playback.
</video>
```

- `poster` = Image shown before video plays
- `<track>` = Subtitles/captions (important for accessibility!)

### iframe: Embedding other websites

```html
<!-- Embed a webpage -->
<iframe src="https://example.com" width="600" height="400"></iframe>

<!-- Embed a YouTube video -->
<iframe width="560" height="315"
    src="https://www.youtube.com/embed/VIDEO_ID"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media"
    allowfullscreen>
</iframe>
```

### Watch It!
⚠️ **iframes are a security risk!** Only embed content you trust. Use CSP (Content Security Policy) headers to restrict what iframes can do.

### CSP (Content Security Policy): Your page's bouncer

Imagine your webpage is a party. CSP is the bouncer at the door - it decides who gets in (which resources can load) and who gets turned away. Without CSP, *anyone* can sneak scripts, styles, or iframes onto your page. Scary, right?

You set CSP via a meta tag or HTTP header:

```html
<!-- Via meta tag -->
<meta http-equiv="Content-Security-Policy"
      content="default-src 'self'; img-src https:; script-src 'self' https://trusted-cdn.com;">
```

**Think of each directive as a rule for the bouncer:**

| Directive | "Only let in..." |
|-----------|-----------------|
| `default-src` | ...these sources for everything (fallback rule) |
| `script-src` | ...JavaScript from these places |
| `style-src` | ...CSS from these places |
| `img-src` | ...images from these places |
| `frame-src` | ...iframes from these places |
| `font-src` | ...fonts from these places |
| `connect-src` | ...AJAX/fetch requests to these places |

```html
<!-- Only allow scripts from your own domain -->
<meta http-equiv="Content-Security-Policy" content="script-src 'self';">

<!-- Allow images from anywhere over HTTPS -->
<meta http-equiv="Content-Security-Policy" content="img-src https:;">

<!-- Block all iframes (no one gets in!) -->
<meta http-equiv="Content-Security-Policy" content="frame-src 'none';">
```

**Why should you care?**
- Prevents XSS (Cross-Site Scripting) attacks - the #1 web vulnerability
- Stops unauthorized scripts from running on your page
- Controls which external resources can load
- Your users are safer, even if your server gets compromised

### Brain Power
🧠 Why would you want to restrict where scripts can load from? Think about what happens if an attacker injects a `<script src="https://evil.com/steal-passwords.js">` tag into your page...

### Watch It!
⚠️ **CSP can break your own site!** If you set a strict policy, your own scripts might get blocked. Start with `Content-Security-Policy-Report-Only` to test without breaking anything.

### There are NO Dumb Questions

**Q: Why provide multiple `<source>` elements?**
**A:** Different browsers support different formats. The browser will use the first one it can play.

**Q: What's the difference between `width/height` attributes and CSS?**
**A:** Both work, but attributes prevent layout shift (browser reserves space before image loads). Use both!

**Q: Can I style the video player controls?**
**A:** Not easily. Native controls vary by browser. For custom controls, you'll need JavaScript.

**Q: Do I really need CSP for a simple static site?**
**A:** It's a good habit! Even static sites can be targets. CSP is like wearing a seatbelt - you hope you never need it, but you're glad it's there when something goes wrong.

**Q: What's the difference between the CSP meta tag and the HTTP header?**
**A:** The HTTP header is more powerful (supports more directives). The meta tag is easier to add but has some limitations. For production, use the HTTP header.

---

## 8. Forms: Talking to Your Users

### Forms: Where users talk back

Forms are how users send data to your server. Every login, search box, comment section, and checkout page uses forms.

### Basic form anatomy

```html
<form action="/submit" method="POST">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name">

    <button type="submit">Submit</button>
</form>
```

- `action` = Where to send the data (URL)
- `method` = How to send it ("GET" or "POST")

### GET vs POST: What's the difference?

**GET:**
- Data appears in URL (`?name=John&age=30`)
- Use for searches and filtering
- Bookmarkable, shareable
- Not secure (passwords visible in URL!)

**POST:**
- Data sent in request body (not visible in URL)
- Use for forms that change data
- More secure
- Can send files

### Brain Power
🧠 When would you use GET vs POST? Think about a search form vs a login form.

### Input types: More than just text boxes

```html
<!-- Text input -->
<input type="text" name="username">

<!-- Email (with validation!) -->
<input type="email" name="email">

<!-- Password (hidden characters) -->
<input type="password" name="password">

<!-- Number (with spinner) -->
<input type="number" name="age" min="0" max="120">

<!-- Date picker -->
<input type="date" name="birthdate">

<!-- Color picker -->
<input type="color" name="favorite-color">

<!-- Range slider -->
<input type="range" name="volume" min="0" max="100">

<!-- File upload -->
<input type="file" name="avatar" accept="image/*">

<!-- Hidden (invisible to user) -->
<input type="hidden" name="user_id" value="12345">
```

### Labels: Always, always, ALWAYS use them

```html
<!-- Method 1: Using "for" attribute -->
<label for="email">Email:</label>
<input type="email" id="email" name="email">

<!-- Method 2: Wrapping the input -->
<label>
    Email:
    <input type="email" name="email">
</label>
```

### Watch It!
⚠️ **Forms without labels are inaccessible!** Screen readers can't tell users what each field is for. Always use labels.

### Checkboxes: Check all that apply

```html
<fieldset>
    <legend>Select your interests:</legend>

    <input type="checkbox" id="sports" name="interests" value="sports">
    <label for="sports">Sports</label>

    <input type="checkbox" id="music" name="interests" value="music">
    <label for="music">Music</label>

    <input type="checkbox" id="reading" name="interests" value="reading">
    <label for="reading">Reading</label>
</fieldset>
```

### Radio buttons: Choose one

```html
<fieldset>
    <legend>Select your gender:</legend>

    <input type="radio" id="male" name="gender" value="male">
    <label for="male">Male</label>

    <input type="radio" id="female" name="gender" value="female">
    <label for="female">Female</label>

    <input type="radio" id="other" name="gender" value="other">
    <label for="other">Other</label>
</fieldset>
```

**Key point:** Radio buttons with the same `name` are grouped - only one can be selected.

### Brain Power
🧠 What's the difference between checkboxes and radio buttons? When would you use each?

### Textarea: For longer text

```html
<label for="message">Message:</label>
<textarea id="message" name="message" rows="5" cols="50"></textarea>
```

### Select: Dropdowns and multi-select

```html
<!-- Single select -->
<label for="country">Country:</label>
<select id="country" name="country">
    <option value="">-- Select --</option>
    <option value="us">United States</option>
    <option value="uk">United Kingdom</option>
    <option value="ca">Canada</option>
</select>

<!-- Multi-select (hold Ctrl/Cmd) -->
<select name="languages" multiple>
    <option value="html">HTML</option>
    <option value="css">CSS</option>
    <option value="js">JavaScript</option>
</select>

<!-- Grouped options -->
<select name="tech">
    <optgroup label="Frontend">
        <option value="html">HTML</option>
        <option value="css">CSS</option>
    </optgroup>
    <optgroup label="Backend">
        <option value="node">Node.js</option>
        <option value="python">Python</option>
    </optgroup>
</select>
```

### Form validation: HTML's got your back

```html
<!-- Required field -->
<input type="text" name="username" required>

<!-- Email validation -->
<input type="email" name="email" required>

<!-- Min/max length -->
<input type="text" name="username" minlength="3" maxlength="20">

<!-- Number range -->
<input type="number" name="age" min="18" max="100">

<!-- Pattern (regex) -->
<input type="text" name="zipcode" pattern="[0-9]{5}" title="5-digit zip code">
```

### Watch It!
⚠️ **Client-side validation is NOT enough!** Users can bypass HTML validation. Always validate on the server too.

### File uploads: enctype is CRUCIAL

```html
<form action="/upload" method="POST" enctype="multipart/form-data">
    <label for="file">Choose file:</label>
    <input type="file" id="file" name="file" accept=".jpg,.png,.pdf">

    <!-- Multiple files -->
    <input type="file" name="photos" multiple accept="image/*">

    <button type="submit">Upload</button>
</form>
```

**Without `enctype="multipart/form-data"`, file uploads WON'T WORK!**

### Complete form example

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
        <input type="number" id="age" name="age" min="13">

        <fieldset>
            <legend>Interests:</legend>
            <input type="checkbox" id="tech" name="interests" value="tech">
            <label for="tech">Technology</label>

            <input type="checkbox" id="sports" name="interests" value="sports">
            <label for="sports">Sports</label>
        </fieldset>

        <input type="checkbox" id="terms" name="terms" required>
        <label for="terms">I agree to the terms and conditions</label>

        <button type="submit">Register</button>
        <button type="reset">Clear Form</button>
    </fieldset>
</form>
```

### Form limitations: What HTML forms CAN'T do

HTML forms are awesome for getting data from users. But they're not magic. Here's where they hit a wall - and where you'll eventually need JavaScript to pick up the slack:

**The page-reload problem:**
```html
<!-- Every time someone clicks Submit, the ENTIRE page reloads -->
<form action="/submit" method="POST">
    <button type="submit">Submit</button>
</form>
<!-- Want smooth, no-reload submission? You need JavaScript (fetch/AJAX) -->
```

**Validation only goes so far:**
- Can't check if two password fields match (confirm password? nope)
- Can't verify a username is available (that needs a server round-trip)
- Can't do "if you checked X, field Y is required" logic
- `pattern` gives you regex, but no friendly custom error messages

**Styling? Good luck.**
- `<select>`, `<input type="file">`, and `<input type="date">` look different on every browser and OS
- You can't fully restyle native controls with CSS alone
- Most custom-looking form elements are actually rebuilt from scratch with JavaScript

**No multi-step wizards:**
- HTML alone can't show step 1, then step 2, then step 3
- No way to save progress between steps

**No data transformation:**
- Can't format a phone number as the user types
- Can't conditionally show/hide fields based on another field's value
- Can't encrypt data before sending

### Brain Power
🧠 Given these limitations, why do you think HTML forms still matter? Why not just build everything in JavaScript from the start? (Hint: think about accessibility, progressive enhancement, and what happens when JavaScript fails to load...)

### Watch It!
⚠️ **Never rely on HTML validation alone!** Users can open DevTools, delete the `required` attribute, and submit garbage. Or they can skip the browser entirely and send requests directly to your server. *Always* validate on the server too.

### There are NO Dumb Questions

**Q: What's the difference between `<button>` and `<input type="submit">`?**
**A:** `<button>` is more flexible (you can put HTML inside, like images). Both work for submitting forms.

**Q: Why use `<fieldset>` and `<legend>`?**
**A:** They group related form fields and add a label. Great for accessibility and organization.

**Q: Can I style form elements?**
**A:** Yes, but some elements (like file inputs and select dropdowns) are tricky to style. CSS frameworks help.

**Q: So do I need JavaScript for forms?**
**A:** For basic forms (contact, simple signup), HTML alone works fine! For anything dynamic (live validation, AJAX submit, conditional fields), yes, you'll need JavaScript.

---

## 9. Semantic HTML: Meaning Matters

### Why semantic HTML?

Think about this: You could build an entire website using only `<div>` and `<span>`. But should you?

**No!** Here's why semantic HTML matters:
1. **Accessibility** - Screen readers rely on semantic tags
2. **SEO** - Search engines understand your content better
3. **Maintainability** - Other developers understand your code
4. **Default styling** - Browsers style semantic tags appropriately

### The layout tags: Structuring your page

```html
<body>
    <header>
        <h1>Site Title</h1>
        <nav>Navigation menu</nav>
    </header>

    <main>
        <article>
            <h2>Article Title</h2>
            <p>Article content...</p>
        </article>

        <aside>Sidebar content</aside>
    </main>

    <footer>
        <p>&copy; 2026 My Website</p>
    </footer>
</body>
```

### Let's meet the semantic tags

**`<header>`** - Introductory content or navigation
- Not just at the top of the page!
- Can have multiple headers (one per article/section)

**`<nav>`** - Navigation links
- Main site navigation
- Breadcrumbs
- Table of contents

**`<main>`** - Main content (only ONE per page!)
- The primary content
- Excludes sidebars, navigation, footers

**`<article>`** - Self-contained content
- Blog posts
- News articles
- Forum posts
- Can stand alone and still make sense

**`<section>`** - Thematic grouping
- Chapters
- Tabs in a tabbed interface
- Different sections of a page

**`<aside>`** - Tangentially related content
- Sidebars
- Pull quotes
- Advertisements
- Related links

**`<footer>`** - Footer for page or section
- Copyright info
- Contact info
- Related links

### Brain Power
🧠 What's the difference between `<article>` and `<section>`? Could an article contain sections? Could a section contain articles?

### A complete semantic page structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>My Blog</title>
</head>
<body>
    <header>
        <h1>My Awesome Blog</h1>
        <nav>
            <ul>
                <li><a href="/">Home</a></li>
                <li><a href="/about">About</a></li>
                <li><a href="/contact">Contact</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <article>
            <header>
                <h2>Understanding Semantic HTML</h2>
                <p>Published on <time datetime="2026-01-13">January 13, 2026</time></p>
            </header>

            <section>
                <h3>Introduction</h3>
                <p>Semantic HTML is important because...</p>
            </section>

            <section>
                <h3>Benefits</h3>
                <p>Here are the benefits...</p>
            </section>

            <footer>
                <p>Tags: HTML, Semantic, Web Development</p>
            </footer>
        </article>

        <aside>
            <h3>Related Posts</h3>
            <ul>
                <li><a href="/post1">Post 1</a></li>
                <li><a href="/post2">Post 2</a></li>
            </ul>
        </aside>
    </main>

    <footer>
        <p>&copy; 2026 My Blog. All rights reserved.</p>
    </footer>
</body>
</html>
```

### Watch It!
⚠️ **Don't use semantic tags just for styling!** If you need a container for CSS, use `<div>`. Only use semantic tags when they add meaning.

### More semantic tags for text

**`<mark>`** - Highlighted text (like a highlighter pen)
```html
<p>The <mark>important part</mark> is highlighted.</p>
```

**`<time>`** - Dates and times
```html
<time datetime="2026-01-13">January 13, 2026</time>
```

**`<code>`** - Code snippets
```html
<p>Use the <code>console.log()</code> function to debug.</p>
```

**`<pre>`** - Preformatted text (preserves whitespace)
```html
<pre>
function hello() {
    console.log("Hello!");
}
</pre>
```

**`<kbd>`** - Keyboard input
```html
<p>Press <kbd>Ctrl</kbd> + <kbd>C</kbd> to copy.</p>
```

**`<samp>`** - Sample output
```html
<samp>Error: File not found</samp>
```

**`<var>`** - Variable in math or programming
```html
<p>The formula is <var>E</var> = <var>mc</var><sup>2</sup></p>
```

### Quotations and citations

**`<blockquote>`** - Long quotations (block-level)
```html
<blockquote cite="https://source.com">
    <p>This is a long quotation that deserves its own paragraph.</p>
</blockquote>
```

**`<q>`** - Short inline quotations
```html
<p>As Einstein said, <q>Imagination is more important than knowledge.</q></p>
```

**`<cite>`** - Title of a work
```html
<p>My favorite book is <cite>The Great Gatsby</cite>.</p>
```

**`<abbr>`** - Abbreviations
```html
<p><abbr title="HyperText Markup Language">HTML</abbr> is awesome!</p>
```

**`<dfn>`** - Defining instance of a term
```html
<p><dfn>HTML</dfn> is a markup language for creating web pages.</p>
```

**`<address>`** - Contact information
```html
<address>
    Written by <a href="mailto:john@example.com">John Doe</a>.<br>
    Visit us at: 123 Main St, City, Country
</address>
```

### Highlighting changes

**`<del>`** - Deleted text
```html
<p>Price: <del>$50</del> $30</p>
```

**`<ins>`** - Inserted text
```html
<p>My favorite color is <del>blue</del> <ins>red</ins>.</p>
```

**`<s>`** - No longer accurate
```html
<s>Out of stock</s>
```

### Exercise: Semantify this HTML

Convert this div soup into semantic HTML:

```html
<div class="header">
    <div class="title">My Blog</div>
    <div class="menu">
        <div><a href="/">Home</a></div>
        <div><a href="/about">About</a></div>
    </div>
</div>

<div class="content">
    <div class="post">
        <div class="post-title">My First Post</div>
        <div class="post-content">This is my first blog post...</div>
    </div>
</div>

<div class="sidebar">Related links</div>

<div class="footer">Copyright 2026</div>
```

**Your answer:**
```html
<!-- Try it yourself first! -->
```

**Answer:**
```html
<header>
    <h1>My Blog</h1>
    <nav>
        <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/about">About</a></li>
        </ul>
    </nav>
</header>

<main>
    <article>
        <h2>My First Post</h2>
        <p>This is my first blog post...</p>
    </article>

    <aside>Related links</aside>
</main>

<footer>
    <p>&copy; 2026</p>
</footer>
```

### There are NO Dumb Questions

**Q: Does semantic HTML actually affect how the page looks?**
**A:** Barely! Most semantic elements have little or no default styling. The value is in meaning - accessibility, SEO, and code readability. You still use CSS for visual design.

**Q: When should I use `<section>` vs `<div>`?**
**A:** `<section>` is for a thematic grouping of content (usually with its own heading). `<div>` is for styling or layout when no semantic element fits. If you can't think of a meaningful heading for it, it's probably a `<div>`.

**Q: Is it wrong to use `<div>` at all?**
**A:** Not at all! Divs are fine for layout containers and CSS hooks. The problem is using them *instead of* semantic elements. `<div class="nav">` should be `<nav>`, but a `<div class="card-grid">` wrapper is perfectly valid.

---

## 10. Styling: Making It Pretty

### Three ways to style HTML

1. **Inline CSS** - Style attribute on elements
2. **Internal CSS** - `<style>` tag in `<head>`
3. **External CSS** - Separate `.css` file

### Inline CSS: Quick but messy

```html
<p style="color: red; font-size: 18px; font-weight: bold;">
    This text is red, large, and bold.
</p>
```

**Pros:** Quick, overrides everything
**Cons:** Hard to maintain, repeating yourself, mixing content and presentation

### Watch It!
⚠️ **Avoid inline CSS!** It's okay for quick testing, but not for production. Use external CSS instead.

### Internal CSS: Better, but still limited

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #f4f4f4;
        }

        h1 {
            color: #333;
            border-bottom: 2px solid #007bff;
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
    <p class="highlight">This is highlighted.</p>
</body>
</html>
```

**Pros:** All in one file, easier to manage than inline
**Cons:** Can't reuse across pages, makes HTML file large

### External CSS: The right way

**index.html:**
```html
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1>Hello World</h1>
    <p class="highlight">Styled text</p>
</body>
</html>
```

**styles.css:**
```css
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 20px;
}

h1 {
    color: #333;
}

.highlight {
    background-color: yellow;
}
```

**Pros:** Reusable, cached by browser, separates content and presentation
**Cons:** Extra HTTP request (but worth it!)

### CSS Specificity: Who wins?

When multiple styles conflict, specificity determines the winner:

1. **Inline styles** (highest) - `style="..."`
2. **IDs** - `#header { }`
3. **Classes, attributes, pseudo-classes** - `.highlight { }`, `[type="text"]`, `:hover`
4. **Elements** (lowest) - `p { }`, `div { }`

```html
<style>
    p { color: black; }           /* Specificity: 1 */
    .highlight { color: yellow; }  /* Specificity: 10 */
    #intro { color: blue; }        /* Specificity: 100 */
</style>

<p style="color: red;">Red wins!</p>     <!-- Inline: 1000 -->
<p id="intro" class="highlight">Blue wins!</p>  <!-- ID beats class -->
<p class="highlight">Yellow wins!</p>    <!-- Class beats element -->
```

### Brain Power
🧠 What color will this text be?
```html
<style>
    p { color: black; }
    .red { color: red; }
    #blue { color: blue; }
</style>

<p id="blue" class="red" style="color: green;">What color am I?</p>
```

**Answer:** Green! Inline styles always win.

### There are NO Dumb Questions

**Q: Can I have multiple `<link>` tags?**
**A:** Yes! Load as many CSS files as you need. They're processed in order.

**Q: Where should I put the `<link>` tag?**
**A:** In the `<head>`. Browsers will load CSS before rendering the page.

**Q: What if my CSS file doesn't load?**
**A:** Check the file path, check your browser console for errors, and make sure the file exists!

---

## 11. JavaScript: Adding Behavior

### HTML structures, CSS styles, JavaScript DOES

HTML is the skeleton, CSS is the skin, JavaScript is the muscles and brain. It makes things interactive!

### Three ways to include JavaScript

1. **Inline JavaScript** - Event handlers
2. **Internal JavaScript** - `<script>` tag in HTML
3. **External JavaScript** - Separate `.js` file

### Inline JavaScript: Don't do this

```html
<button onclick="alert('Clicked!')">Click Me</button>
```

**Why not?** Mixing behavior with structure, hard to maintain, security issues.

### Internal JavaScript: Better

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
        console.log('Page loaded!');

        document.getElementById('btn').addEventListener('click', function() {
            document.getElementById('heading').textContent = 'Button Clicked!';
        });
    </script>
</body>
</html>
```

### External JavaScript: The best way

**index.html:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript Example</title>
</head>
<body>
    <h1 id="heading">Hello World</h1>
    <button id="btn">Click Me</button>

    <!-- Just before closing </body> -->
    <script src="script.js"></script>
</body>
</html>
```

**script.js:**
```javascript
console.log('Page loaded!');

document.getElementById('btn').addEventListener('click', function() {
    document.getElementById('heading').textContent = 'Button Clicked!';
});
```

### Script placement: Where matters!

```html
<!-- In <head>: Blocks rendering! -->
<head>
    <script src="script.js"></script>
</head>

<!-- Before </body>: Best for most scripts -->
<body>
    <!-- Content -->
    <script src="script.js"></script>
</body>

<!-- With defer: Loads async, executes after parsing -->
<head>
    <script src="script.js" defer></script>
</head>

<!-- With async: Loads and executes ASAP -->
<head>
    <script src="script.js" async></script>
</head>
```

### defer vs async: What's the difference?

| Attribute | Download | Execution | Order Preserved |
|-----------|----------|-----------|-----------------|
| Normal | Blocks HTML | Immediately | Yes |
| `defer` | Parallel (async) | After HTML parsing | Yes |
| `async` | Parallel (async) | ASAP (may block) | No |

**Rule of thumb:** Use `defer` for most scripts!

### Brain Power
🧠 Why would you put a script tag at the END of the body instead of the beginning? Think about DOM elements...

### Watch It!
⚠️ **Scripts run in order!** If `script1.js` depends on `script2.js`, load `script2.js` first.

```html
<!-- Wrong! jQuery not loaded yet -->
<script src="my-plugin.js"></script>
<script src="jquery.js"></script>

<!-- Right! jQuery loads first -->
<script src="jquery.js"></script>
<script src="my-plugin.js"></script>
```

### ES6 Modules: Modern JavaScript

```html
<!-- Modern modules -->
<script type="module" src="script.js"></script>
```

Modules are always deferred, have their own scope, and support `import`/`export`.

### There are NO Dumb Questions

**Q: What's `document.getElementById()`?**
**A:** JavaScript function that finds an HTML element by its `id` attribute. Then you can manipulate it!

**Q: Can I have multiple `<script>` tags?**
**A:** Yes! They execute in order. Common to have multiple external scripts.

**Q: What's the `console.log()` thing?**
**A:** Prints to browser console (F12 → Console tab). Great for debugging!

---

## 12. Accessibility: Building for Everyone

### What is web accessibility?

**Web accessibility** means people with disabilities can use your website. This includes:
- Visual impairments (blindness, low vision, color blindness)
- Hearing impairments (deafness, hard of hearing)
- Motor impairments (can't use a mouse)
- Cognitive impairments (dyslexia, memory issues)

### Why should you care?

1. **It's the right thing to do** - 15% of the world has a disability
2. **It's often the law** - ADA, Section 508, WCAG compliance
3. **Better SEO** - Accessible sites rank higher
4. **Better UX for everyone** - Curb-cut effect

### The four principles of accessibility (WCAG)

1. **Perceivable** - Information must be presentable to users
2. **Operable** - UI must be operable (keyboard navigation!)
3. **Understandable** - Information must be understandable
4. **Robust** - Content must work with assistive technologies

### Use semantic HTML

```html
<!-- Good: Semantic button -->
<button>Click Me</button>

<!-- Bad: Div pretending to be a button -->
<div onclick="doSomething()">Click Me</div>
```

Screen readers know what a `<button>` is. A `<div>` with `onclick`? Not so much.

### Always use alt text on images

```html
<!-- Informative image: Describe it -->
<img src="chart.png" alt="Bar chart showing 50% increase in Q4 sales">

<!-- Decorative image: Empty alt -->
<img src="decorative-border.png" alt="">

<!-- Don't skip alt! Screen readers will read the filename! -->
<img src="IMG_20240113_0834.jpg">  <!-- Bad! -->
```

### Watch It!
⚠️ **Empty alt (`alt=""`) is NOT the same as missing alt!** Empty alt tells screen readers "this is decorative, skip it". Missing alt makes screen readers announce the filename.

### Labels for ALL form inputs

```html
<!-- Good: Label associated with input -->
<label for="email">Email:</label>
<input type="email" id="email" name="email">

<!-- Bad: No label -->
<input type="email" name="email" placeholder="Email">
```

Placeholders are NOT labels! They disappear when you type.

### Keyboard navigation: Not everyone uses a mouse

**Test your site with keyboard only:**
- Tab = Next element
- Shift+Tab = Previous element
- Enter = Activate button/link
- Space = Activate checkbox/button
- Arrow keys = Radio buttons, select dropdowns

```html
<!-- Make custom elements keyboard-accessible -->
<div tabindex="0" role="button" onclick="doSomething()">
    Custom Button
</div>
```

### Skip links: Let keyboard users skip navigation

```html
<body>
    <a href="#main-content" class="skip-link">Skip to main content</a>

    <nav>
        <!-- Long navigation menu -->
    </nav>

    <main id="main-content">
        <!-- Main content -->
    </main>
</body>
```

```css
.skip-link {
    position: absolute;
    top: -40px;
}

.skip-link:focus {
    top: 0;
}
```

### Color contrast: Make text readable

**WCAG Requirements:**
- **Level AA:** 4.5:1 contrast for normal text, 3:1 for large text
- **Level AAA:** 7:1 contrast for normal text, 4.5:1 for large text

```html
<!-- Good contrast -->
<p style="color: #000; background: #fff;">Black on white (21:1)</p>

<!-- Bad contrast -->
<p style="color: #ccc; background: #fff;">Light gray on white (1.6:1) - FAIL!</p>
```

Use tools like WebAIM Contrast Checker to test.

### ARIA: When HTML isn't enough

ARIA (Accessible Rich Internet Applications) fills gaps when semantic HTML isn't available.

```html
<!-- Button with no text (icon only) -->
<button aria-label="Close dialog">
    <span class="icon-close"></span>
</button>

<!-- Expandable section -->
<button aria-expanded="false" aria-controls="menu">
    Menu
</button>
<div id="menu" hidden>Menu items...</div>

<!-- Live region for dynamic content -->
<div role="alert" aria-live="polite">
    Your changes have been saved!
</div>

<!-- Form field with error -->
<label for="email">Email:</label>
<input type="email" id="email" aria-invalid="true" aria-describedby="email-error">
<span id="email-error" role="alert">Please enter a valid email</span>
```

### Common ARIA attributes

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `role` | Define element's purpose | `role="navigation"` |
| `aria-label` | Label for screen readers | `aria-label="Close"` |
| `aria-labelledby` | Reference to label element | `aria-labelledby="title"` |
| `aria-describedby` | Additional description | `aria-describedby="help"` |
| `aria-expanded` | Is it expanded? | `aria-expanded="false"` |
| `aria-hidden` | Hide from screen readers | `aria-hidden="true"` |
| `aria-live` | Announce dynamic changes | `aria-live="polite"` |

### Watch It!
⚠️ **Don't use ARIA when HTML will do!** `<button>` is better than `<div role="button">`. Native HTML has better keyboard support and browser compatibility.

### Heading structure: It's a table of contents

```html
<!-- Good: Logical hierarchy -->
<h1>Main Page Title</h1>
  <h2>Section 1</h2>
    <h3>Subsection 1.1</h3>
    <h3>Subsection 1.2</h3>
  <h2>Section 2</h2>

<!-- Bad: Skipping levels -->
<h1>Main Page Title</h1>
  <h4>Section 1</h4>  <!-- Skipped h2 and h3! -->
```

Screen readers let users jump between headings. Don't use headings for font size - use CSS!

### Language declaration

```html
<html lang="en">

<!-- Mixed language content -->
<p>The French word <span lang="fr">bonjour</span> means hello.</p>
```

Helps screen readers pronounce words correctly.

### Brain Power
🧠 Why is accessibility good for SEO? Think about how search engine bots "see" your website...

### Quick accessibility checklist

- [ ] All images have alt text
- [ ] All form inputs have labels
- [ ] Color contrast meets WCAG AA (4.5:1)
- [ ] Site is keyboard-navigable
- [ ] Heading hierarchy is logical
- [ ] Links have descriptive text (not "click here")
- [ ] Videos have captions
- [ ] HTML language is declared
- [ ] Semantic HTML used appropriately
- [ ] Forms have clear error messages

### There are NO Dumb Questions

**Q: Do I really need to worry about accessibility?**
**A:** Yes! About 15-20% of the population has some form of disability. Plus, accessibility helps everyone - captions help in noisy environments, keyboard navigation helps power users, good contrast helps in bright sunlight.

**Q: What's the minimum I should do for accessibility?**
**A:** Start with the checklist above. Alt text on images, labels on form inputs, logical heading hierarchy, and keyboard navigation cover the most common issues.

**Q: How do I test accessibility?**
**A:** Use your keyboard to navigate (Tab, Enter, Escape). Try a screen reader (VoiceOver on Mac, NVDA on Windows). Run Lighthouse in Chrome DevTools. These catch most problems.

---

## 13. SEO: Getting Found

### What is SEO?

**Search Engine Optimization** = Making your website rank higher in search results. More traffic = more visitors = more customers/readers/whatever your goal is.

### The `<title>` tag: The most important SEO element

```html
<title>Best Pizza in New York | Joe's Pizza</title>
```

**Best practices:**
- 50-60 characters (longer gets truncated)
- Include main keyword
- Include brand name
- Unique for every page
- Descriptive and compelling

### Meta description: Your sales pitch

```html
<meta name="description" content="Joe's Pizza serves authentic New York-style pizza since 1975. Order online for delivery or pickup in Manhattan.">
```

**Best practices:**
- 150-160 characters
- Include main keyword naturally
- Call to action
- Unique for every page
- Accurate (Google penalizes misleading descriptions)

### Meta keywords: Mostly useless now

```html
<meta name="keywords" content="pizza, new york pizza, manhattan pizza">
```

Google ignores meta keywords (too much spam). Focus on content instead.

### Viewport: Mobile-first is required

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

Google's mobile-first indexing means mobile-friendliness affects your ranking. This tag is REQUIRED.

### Canonical URL: Prevent duplicate content

```html
<link rel="canonical" href="https://example.com/page">
```

Use when the same content is available at multiple URLs:
```
example.com/page
example.com/page/
example.com/page?utm_source=email
```

### Robots meta tag: Control indexing

```html
<!-- Allow indexing and following links (default) -->
<meta name="robots" content="index, follow">

<!-- Don't index this page -->
<meta name="robots" content="noindex, follow">

<!-- Don't follow links on this page -->
<meta name="robots" content="index, nofollow">

<!-- Don't index or follow -->
<meta name="robots" content="noindex, nofollow">
```

### Open Graph: Look good on social media

```html
<meta property="og:title" content="Page Title">
<meta property="og:description" content="Page description">
<meta property="og:image" content="https://example.com/image.jpg">
<meta property="og:url" content="https://example.com/page">
<meta property="og:type" content="website">
<meta property="og:site_name" content="Site Name">
```

When someone shares your link on Facebook/LinkedIn, this is what shows up.

### Twitter Card: Twitter has its own tags

```html
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:site" content="@username">
<meta name="twitter:title" content="Page Title">
<meta name="twitter:description" content="Page description">
<meta name="twitter:image" content="https://example.com/image.jpg">
```

### Semantic HTML for SEO

Search engines love semantic HTML! It helps them understand your content.

```html
<!-- Good: Semantic structure -->
<article>
    <h1>Article Title</h1>
    <p>Content...</p>
</article>

<!-- Bad: Div soup -->
<div class="article">
    <div class="title">Article Title</div>
    <div class="content">Content...</div>
</div>
```

### Heading hierarchy: Your table of contents

```html
<h1>Main Page Topic (one per page!)</h1>
  <h2>Section 1</h2>
    <h3>Subsection 1.1</h3>
  <h2>Section 2</h2>
```

Search engines use headings to understand page structure. One `<h1>` per page!

### Image SEO: Don't ignore images

```html
<img src="red-running-shoes-nike.jpg"
     alt="Red Nike running shoes with white swoosh"
     width="800"
     height="600"
     loading="lazy">
```

**Image SEO tips:**
- Descriptive file names (not `IMG_1234.jpg`)
- Descriptive alt text with keywords (naturally!)
- Specify dimensions (prevents layout shift)
- Compress images (faster = better ranking)
- Use modern formats (WebP)
- Lazy load below-the-fold images

### Internal linking: Connect your content

```html
<!-- Good: Descriptive anchor text -->
<a href="/seo-guide">Learn more about SEO best practices</a>

<!-- Bad: Generic anchor text -->
<a href="/seo-guide">Click here</a>
```

Internal links help:
1. Search engines discover new pages
2. Distribute page authority
3. Users navigate your site
4. Establish content relationships

### Clean URLs: Readable is rankable

```html
<!-- Good: Descriptive URLs -->
https://example.com/blog/seo-tips-2026
https://example.com/products/red-shoes

<!-- Bad: Non-descriptive URLs -->
https://example.com/page?id=123&cat=45
https://example.com/product/item.php?id=789
```

### Page speed: Fast sites rank higher

```html
<!-- Preload critical resources -->
<link rel="preload" href="critical.css" as="style">
<link rel="preload" href="font.woff2" as="font" type="font/woff2" crossorigin>

<!-- Preconnect to external domains -->
<link rel="preconnect" href="https://fonts.googleapis.com">

<!-- DNS prefetch -->
<link rel="dns-prefetch" href="https://cdn.example.com">

<!-- Defer non-critical JavaScript -->
<script src="analytics.js" defer></script>

<!-- Lazy load images -->
<img src="image.jpg" loading="lazy" alt="Description">
```

### Structured data: Help search engines understand

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "SEO Best Practices for 2026",
  "description": "Comprehensive guide to SEO",
  "image": "https://example.com/seo-guide.jpg",
  "author": {
    "@type": "Person",
    "name": "John Doe"
  },
  "datePublished": "2026-01-13",
  "dateModified": "2026-01-13"
}
</script>
```

**Common structured data types:**
- Article
- Product
- Recipe
- Event
- Organization
- Person
- FAQ
- BreadcrumbList

### Watch It!
⚠️ **SEO takes time!** Changes won't show up overnight. Google can take weeks or months to re-index and re-rank your page.

### Brain Power
🧠 Why do you think page speed affects SEO? Think about user experience...

### SEO Best Practices Checklist

- [ ] Unique, descriptive `<title>` for each page
- [ ] Unique meta description for each page
- [ ] Mobile-friendly (responsive design)
- [ ] Fast loading (under 3 seconds)
- [ ] Semantic HTML structure
- [ ] One `<h1>` per page with logical heading hierarchy
- [ ] Descriptive URLs
- [ ] Internal linking with descriptive anchor text
- [ ] Image optimization (alt text, file names, compression)
- [ ] HTTPS (secure connection)
- [ ] XML sitemap
- [ ] Robots.txt file
- [ ] Structured data where appropriate
- [ ] Fresh, quality content
- [ ] Mobile-first design

### There are NO Dumb Questions

**Q: Is SEO the same as accessibility?**
**A:** They overlap! Both benefit from semantic HTML, alt text, good structure. But accessibility is about people with disabilities, SEO is about search engines.

**Q: Can I guarantee #1 ranking?**
**A:** No! Anyone who promises #1 ranking is lying. SEO is about improving your chances, not guarantees.

**Q: How long does SEO take?**
**A:** Typically 3-6 months to see significant results. SEO is a long-term strategy, not a quick fix.

**Q: Should I hire an SEO expert?**
**A:** For complex sites or competitive industries, yes. But learn the basics first so you can evaluate their work!

---

## Congratulations!

You've made it through the HTML cheatsheet! But this isn't the end - it's just the beginning.

### What's next?

1. **Practice, practice, practice** - Build real projects
2. **Learn CSS** - Make your HTML look amazing
3. **Learn JavaScript** - Add interactivity
4. **Study responsive design** - Mobile-first approach
5. **Explore frameworks** - React, Vue, Angular
6. **Keep learning** - The web evolves constantly

### Brain Power (Final Challenge)
🧠 Build a complete personal portfolio page using everything you learned. Include:
- Semantic HTML structure
- Multiple sections (about, projects, contact)
- A form for contact
- Images with proper alt text
- Accessible navigation
- SEO meta tags
- Internal links

### Additional Resources

- **MDN Web Docs:** https://developer.mozilla.org/en-US/docs/Web/HTML
- **W3Schools:** https://www.w3schools.com/html/
- **HTML Living Standard:** https://html.spec.whatwg.org/
- **WCAG Guidelines:** https://www.w3.org/WAI/WCAG21/quickref/
- **Frontend Roadmap:** https://roadmap.sh/frontend
- **Can I Use:** https://caniuse.com/

---

## Quick Reference Card

**Document Structure:**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page Title</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- Content -->
    <script src="script.js"></script>
</body>
</html>
```

**Common Tags:**
- `<h1>` to `<h6>` - Headings
- `<p>` - Paragraph
- `<a href="">` - Link
- `<img src="" alt="">` - Image
- `<div>` - Block container
- `<span>` - Inline container
- `<ul>/<ol>/<li>` - Lists
- `<table>/<tr>/<td>` - Tables
- `<form>/<input>` - Forms

**Semantic Tags:**
- `<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<aside>`, `<footer>`

**Form Inputs:**
- `text`, `email`, `password`, `number`, `date`, `checkbox`, `radio`, `file`, `submit`

**Attributes:**
- `id` - Unique identifier
- `class` - CSS class
- `style` - Inline CSS
- `data-*` - Custom data
- `alt` - Image alternative text
- `href` - Link URL
- `src` - Resource URL

---

**Created in the style of Head First books**

*Now go build something awesome!* 🚀