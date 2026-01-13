# Head First CSS Cheatsheet

> Your brain on CSS. Here you'll learn how to make websites beautiful the way your brain likes to learn - with conversational style, visual examples, and practical exercises that stick.

---

## How to Use This Cheatsheet

**We think of CSS as fun, not frustrating.** You'll find Q&A sections, "Watch It!" warnings, "Brain Power" exercises, and lots of conversation. CSS can seem magical (or maddening), but we'll make it click.

**The activities are NOT optional.** The exercises and challenges are part of the learning experience. Type the code, see what happens, break it, fix it.

**The redundancy is intentional.** CSS concepts build on each other. You'll see selectors, specificity, and the box model pop up again and again - that's how learning works.

---

## Table of Contents

1. [Introduction: What is CSS?](#1-introduction-what-is-css)
2. [CSS Basics: Syntax and Rules](#2-css-basics-syntax-and-rules)
3. [Selectors: Targeting Elements](#3-selectors-targeting-elements)
4. [Colors: Making Things Colorful](#4-colors-making-things-colorful)
5. [Text Styling: Typography Matters](#5-text-styling-typography-matters)
6. [The Box Model: Everything is a Box](#6-the-box-model-everything-is-a-box)
7. [Units: Sizing Things Right](#7-units-sizing-things-right)
8. [Background: More Than Just Color](#8-background-more-than-just-color)
9. [Display: Block, Inline, and Friends](#9-display-block-inline-and-friends)
10. [Position: Moving Things Around](#10-position-moving-things-around)
11. [Layouts: Flexbox and Grid](#11-layouts-flexbox-and-grid)
12. [Transforms and Animations](#12-transforms-and-animations)
13. [Responsive Design: One Size Fits All](#13-responsive-design-one-size-fits-all)
14. [CSS Variables and Functions](#14-css-variables-and-functions)
15. [Best Practices and Methodologies](#15-best-practices-and-methodologies)

---

## 1. Introduction: What is CSS?

### CSS = Cascading Style Sheets

Remember HTML? It's the skeleton. **CSS is the skin, clothes, makeup, and style.** It's what makes websites go from boring black text on white background to... well, everything you see on the web.

**Cascading** = Styles "cascade" down (more on this later - it's important!)
**Style** = Colors, fonts, spacing, layout
**Sheets** = Files (usually) containing all your style rules

### The Three Ways to Add CSS

Think of it like getting dressed:

1. **Inline CSS** = Getting dressed while still in bed (messy, not recommended)
2. **Internal CSS** = Having a closet in your bedroom (okay for small projects)
3. **External CSS** = Having a walk-in closet in a separate room (professional, best practice)

### Inline CSS: Quick and dirty

```html
<p style="color: red; font-size: 20px;">Red text</p>
```

**Pros:** Fast for testing
**Cons:** Nightmare to maintain, mixes content with presentation, no reusability

### Internal CSS: Better, but limited

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        p {
            color: blue;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <p>Blue text</p>
</body>
</html>
```

**Pros:** All in one file, styles are separated from HTML
**Cons:** Can't reuse across multiple pages, makes HTML files bloated

### External CSS: The right way

**index.html:**
```html
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <p>Styled text</p>
</body>
</html>
```

**styles.css:**
```css
p {
    color: green;
    font-size: 16px;
}
```

**Pros:** Reusable, cached by browsers, clean separation, easier to maintain
**Cons:** Extra HTTP request (but browsers cache it!)

### Cascading Order: Who wins?

When multiple styles conflict, CSS has a priority system:

1. **Inline styles** (highest priority) - `style="..."`
2. **Internal & External styles** (same priority, last one wins)
3. **Browser defaults** (lowest priority)

### Brain Power
🧠 If you have an external stylesheet that makes paragraphs blue, an internal style that makes them red, and an inline style that makes them green - what color will the paragraph be?

**Answer:** Green! Inline styles always win.

### Watch It!
⚠️ **The cascade can bite you!** Understanding cascading order and specificity (we'll cover this soon) is crucial to not pulling your hair out wondering why your styles aren't working.

### There are NO Dumb Questions

**Q: Why is it called "cascading"?**
**A:** Because styles "cascade" from top to bottom, and more specific styles override general ones. Like water cascading down a waterfall, picking up things along the way.

**Q: Can I have multiple external stylesheets?**
**A:** Yes! Load as many as you need. They're processed in order.

**Q: Which method should I use?**
**A:** External CSS for real projects, internal CSS for single-page demos, inline CSS for quick testing only.

---

## 2. CSS Basics: Syntax and Rules

### The anatomy of a CSS rule

```css
selector {
    property: value;
    property: value;
}
```

Every CSS rule has three parts:

1. **Selector** - What element(s) to style
2. **Property** - What aspect to change (color, size, etc.)
3. **Value** - What to change it to

### A real example

```css
p {
    color: blue;
    font-size: 16px;
    margin: 10px;
}
```

- **Selector:** `p` (all paragraph elements)
- **Declaration block:** Everything inside `{ }`
- **Declaration:** Each `property: value;` pair
- **Semicolon:** Separates declarations (last one is optional but recommended)

### Multiple selectors, same style

```css
h1, h2, h3 {
    color: navy;
    font-family: Arial;
}
```

Comma = "and" (style ALL of these)

### Comments: Leave notes for yourself

```css
/* This is a single-line comment */

/*
    This is a
    multi-line comment
    Use it to explain complex CSS
*/

p {
    color: red; /* You can also comment inline */
}
```

### Watch It!
⚠️ **CSS comments are different from HTML comments!** CSS uses `/* */`, HTML uses `<!-- -->`. Don't mix them up.

### Brain Power
🧠 What's wrong with this CSS?

```css
p {
    color: blue
    font-size: 16px;
}
```

**Answer:** Missing semicolon after `blue`! While the last semicolon is optional, missing ones between declarations will break your CSS.

### The CSS Declaration

Let's break it down even further:

```css
color: blue;
  ↑     ↑   ↑
property: value;
      ↑
    colon separates
```

**Properties** are predefined by CSS (you can't make up your own)
**Values** depend on the property (colors for `color`, sizes for `font-size`, etc.)

### Sharpen your pencil

Match the CSS term to its definition:

1. Selector → _____
2. Property → _____
3. Value → _____
4. Declaration → _____

A. What aspect to change
B. What element to style
C. What to change it to
D. A property-value pair

**Answers:** 1-B, 2-A, 3-C, 4-D

---

## 3. Selectors: Targeting Elements

### Why selectors matter

Selectors are like addresses. If CSS is mail, selectors tell the browser which houses (elements) to deliver the style to.

### Simple Selectors

#### Element Selector (Type Selector)

```css
p {
    color: blue;
}

h1 {
    font-size: 32px;
}
```

Selects ALL elements of that type.

#### Class Selector

```css
.highlight {
    background-color: yellow;
}

.error {
    color: red;
}
```

```html
<p class="highlight">Highlighted paragraph</p>
<span class="error">Error message</span>
```

- Starts with a dot (`.`)
- Reusable - use on multiple elements
- Multiple classes on one element: `class="highlight error"`

#### ID Selector

```css
#header {
    background-color: navy;
}

#main-content {
    padding: 20px;
}
```

```html
<div id="header">Site Header</div>
<main id="main-content">Content here</main>
```

- Starts with a hash (`#`)
- Should be unique per page
- Higher specificity than classes

#### Universal Selector

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```

Selects EVERYTHING. Use sparingly (performance impact).

#### Grouping Selector

```css
h1, h2, h3, h4, h5, h6 {
    font-family: Arial, sans-serif;
    color: #333;
}
```

Comma-separated = apply same styles to multiple selectors.

### Brain Power
🧠 When would you use a class vs an ID? What's the practical difference?

**Answer:** Classes are for styling multiple elements (reusable). IDs are for unique elements (navigation targets, JavaScript). In CSS, use classes for styling 99% of the time.

### Combinator Selectors: Getting specific

#### Descendant Selector (space)

```css
article p {
    line-height: 1.6;
}
```

Selects ALL `<p>` elements inside `<article>`, at any depth.

```html
<article>
    <p>Styled</p>
    <div>
        <p>Also styled</p>
    </div>
</article>
```

#### Child Selector (>)

```css
article > p {
    line-height: 1.6;
}
```

Selects ONLY direct children (one level deep).

```html
<article>
    <p>Styled</p>
    <div>
        <p>NOT styled (not a direct child)</p>
    </div>
</article>
```

#### Next Sibling Selector (+)

```css
h2 + p {
    margin-top: 0;
}
```

Selects the FIRST `<p>` immediately after an `<h2>`.

```html
<h2>Heading</h2>
<p>This paragraph is styled</p>
<p>This one is NOT</p>
```

#### Subsequent Sibling Selector (~)

```css
h2 ~ p {
    color: gray;
}
```

Selects ALL `<p>` elements that come after an `<h2>` (at the same level).

```html
<h2>Heading</h2>
<p>Styled</p>
<p>Also styled</p>
<div>
    <p>NOT styled (different level)</p>
</div>
```

### Watch It!
⚠️ **Descendant selectors can be expensive!** The browser has to check every nested element. `article p` is slower than `.article-paragraph`.

### Attribute Selectors: Super specific

```css
/* Has attribute */
input[required] {
    border: 2px solid red;
}

/* Exact value */
input[type="text"] {
    padding: 5px;
}

/* Contains value */
a[href*="example.com"] {
    color: green;
}

/* Starts with */
a[href^="https"] {
    padding-left: 20px;
}

/* Ends with */
a[href$=".pdf"] {
    background: url(pdf-icon.png);
}
```

### Pseudo-Classes: State-based styling

```css
/* Link states */
a:link { color: blue; }
a:visited { color: purple; }
a:hover { color: red; }
a:active { color: orange; }

/* Form states */
input:focus {
    border-color: blue;
    outline: 2px solid lightblue;
}

input:disabled {
    background-color: #ccc;
}

/* Structural pseudo-classes */
li:first-child {
    font-weight: bold;
}

li:last-child {
    border-bottom: none;
}

li:nth-child(odd) {
    background-color: #f0f0f0;
}

li:nth-child(even) {
    background-color: white;
}

/* Not selector */
p:not(.highlight) {
    color: gray;
}
```

### Pseudo-Elements: Style parts of elements

```css
/* First letter */
p::first-letter {
    font-size: 2em;
    font-weight: bold;
    float: left;
}

/* First line */
p::first-line {
    font-variant: small-caps;
}

/* Before and after (content generation) */
.quote::before {
    content: """;
    font-size: 2em;
    color: gray;
}

.quote::after {
    content: """;
    font-size: 2em;
    color: gray;
}

/* Selection (when user highlights text) */
::selection {
    background-color: yellow;
    color: black;
}
```

### Watch It!
⚠️ **Pseudo-elements use double colons (::), pseudo-classes use single (:)**. Modern browsers accept single colons for pseudo-elements for backwards compatibility, but use double colons for clarity.

### Exercise: Selector Challenge

What will these selectors match?

```css
1. div p { }
2. div > p { }
3. div + p { }
4. div ~ p { }
5. p.highlight { }
6. p .highlight { }
```

**Answers:**
1. All `<p>` inside `<div>` at any depth
2. Only `<p>` that are direct children of `<div>`
3. The first `<p>` immediately after a `<div>`
4. All `<p>` elements that come after a `<div>` (same level)
5. `<p>` elements with class "highlight"
6. Elements with class "highlight" inside a `<p>`

### There are NO Dumb Questions

**Q: Why do we need so many selectors?**
**A:** Specificity and control! Different selectors give you different levels of precision for targeting exactly what you want to style.

**Q: Should I use IDs or classes for styling?**
**A:** Classes! IDs have very high specificity which makes them hard to override. Save IDs for JavaScript and page anchors.

**Q: What's the difference between `::before` and `:before`?**
**A:** No functional difference in modern browsers, but `::before` (double colon) is the correct CSS3 syntax for pseudo-elements. Use double colons.

---

## 4. Colors: Making Things Colorful

### Ways to specify colors in CSS

CSS gives you SIX ways to define colors. Why so many? Flexibility!

### Named Colors: The easy way

```css
p {
    color: red;
}

div {
    background-color: blue;
}

span {
    color: cornflowerblue; /* Yep, that's a real color name */
}
```

147 named colors available. Easy to remember, but limited.

### Hex Colors: The classic way

```css
h1 {
    color: #FF0000; /* Red */
}

p {
    color: #00FF00; /* Green */
}

div {
    background-color: #0000FF; /* Blue */
}

/* Shorthand (when digits repeat) */
.box {
    color: #F00; /* Same as #FF0000 */
    background: #FFF; /* Same as #FFFFFF (white) */
}
```

**Format:** `#RRGGBB` (Red, Green, Blue)
- Each pair is hexadecimal (0-9, A-F)
- 00 = no color, FF = full color
- Shorthand when pairs match: `#336699` → `#369`

### RGB: The numerical way

```css
p {
    color: rgb(255, 0, 0); /* Red */
}

div {
    background-color: rgb(0, 128, 255); /* Blue */
}
```

**Format:** `rgb(red, green, blue)`
- Each value: 0-255
- More intuitive than hex for some people

### RGBA: RGB with transparency

```css
.overlay {
    background-color: rgba(0, 0, 0, 0.5); /* 50% transparent black */
}

.button {
    background-color: rgba(255, 0, 0, 0.8); /* 80% opaque red */
}
```

**Format:** `rgba(red, green, blue, alpha)`
- Alpha: 0 (fully transparent) to 1 (fully opaque)
- Great for overlays, shadows, glass effects

### HSL: The designer's way

```css
h1 {
    color: hsl(0, 100%, 50%); /* Red */
}

p {
    color: hsl(120, 100%, 50%); /* Green */
}

div {
    background-color: hsl(240, 100%, 50%); /* Blue */
}
```

**Format:** `hsl(hue, saturation, lightness)`
- **Hue:** 0-360 (color wheel degrees) - 0=red, 120=green, 240=blue
- **Saturation:** 0-100% (0%=gray, 100%=full color)
- **Lightness:** 0-100% (0%=black, 50%=normal, 100%=white)

### HSLA: HSL with transparency

```css
.card {
    background-color: hsla(200, 50%, 50%, 0.7); /* Semi-transparent blue */
}
```

### Brain Power
🧠 Why would you use HSL instead of RGB or hex? Think about creating color variations...

**Answer:** HSL makes it easy to create color schemes! Want a lighter version? Increase lightness. Want less vibrant? Decrease saturation. With RGB/hex, you have to calculate all three channels.

### Interview: RGB vs HSL

**Head First: Welcome RGB and HSL! You're both ways to specify colors. What makes you different?**

**RGB:** I'm straightforward - three numbers for red, green, and blue light. Mix them like paint.

**HSL:** I think like a designer - hue (what color), saturation (how vibrant), lightness (how bright).

**HF: When should developers use each of you?**

**RGB:** When they know the exact RGB values, or when they're working with tools that output RGB.

**HSL:** When they're creating color schemes! It's way easier to make variations. Same hue, different lightness = instant color palette.

**HF: What about hex?**

**RGB:** That's just me in disguise! Hex is RGB in hexadecimal notation.

**HSL:** And I'm the new kid, but designers love me.

### Color Properties

```css
/* Text color */
p {
    color: #333;
}

/* Background color */
div {
    background-color: lightblue;
}

/* Border color */
.box {
    border: 2px solid red;
    border-color: blue; /* Override just the color */
}

/* Outline color */
button:focus {
    outline-color: orange;
}
```

### Watch It!
⚠️ **Use `color` for text, `background-color` for backgrounds!** Don't confuse them. `color` by itself always means text color.

### Exercise: Color Conversion

Convert these colors:

1. `rgb(255, 0, 0)` to hex: _____
2. `#00FF00` to RGB: _____
3. Red at 50% opacity in RGBA: _____

**Answers:**
1. `#FF0000`
2. `rgb(0, 255, 0)`
3. `rgba(255, 0, 0, 0.5)`

### There are NO Dumb Questions

**Q: Which color format should I use?**
**A:** Preference! Hex is most common (short, clean). RGBA/HSLA when you need transparency. HSL when creating color schemes.

**Q: What's the difference between `opacity` and `rgba`?**
**A:** `opacity` affects the entire element including children. `rgba` only affects that specific color. Use `rgba` for backgrounds, `opacity` for entire elements.

**Q: Can I use color names in production?**
**A:** Sure, but be consistent. "Red" can be ambiguous. Hex/RGB gives you exact shades.

---

## 5. Text Styling: Typography Matters

### Font Families: Choosing fonts

```css
/* Single font */
p {
    font-family: Arial;
}

/* Font stack (fallbacks) */
body {
    font-family: Arial, Helvetica, sans-serif;
}

/* Serif fonts */
h1 {
    font-family: Georgia, "Times New Roman", serif;
}

/* Monospace fonts */
code {
    font-family: "Courier New", Courier, monospace;
}
```

**Font stack:** Browser tries the first font. If not available, tries the next. Last should be a generic family (`serif`, `sans-serif`, `monospace`, `cursive`, `fantasy`).

**Quote fonts with spaces:** `"Times New Roman"`, not `Times New Roman`

### Font Size: How big?

```css
p {
    font-size: 16px;
}

h1 {
    font-size: 2em; /* 2x parent font size */
}

.small {
    font-size: 0.8rem; /* 0.8x root font size */
}

.responsive {
    font-size: clamp(14px, 2vw, 24px); /* Responsive size */
}
```

### Font Style: Italic and oblique

```css
em {
    font-style: italic;
}

.slanted {
    font-style: oblique;
}

.normal {
    font-style: normal; /* Override italic */
}
```

### Font Weight: How bold?

```css
p {
    font-weight: normal; /* 400 */
}

strong {
    font-weight: bold; /* 700 */
}

.light {
    font-weight: 300;
}

.extra-bold {
    font-weight: 900;
}
```

Values: `100`, `200`, `300`, `400` (normal), `500`, `600`, `700` (bold), `800`, `900`
Or: `normal`, `bold`, `bolder`, `lighter`

### Font Variant: Small caps

```css
.small-caps {
    font-variant: small-caps;
}
```

### Font Shorthand: All in one

```css
/* font: style variant weight size/line-height family */

p {
    font: italic small-caps bold 16px/1.5 Arial, sans-serif;
}

/* Minimum required: size and family */
p {
    font: 16px Arial;
}
```

**Order matters!** Size and family are required, others are optional.

### Google Fonts: Free custom fonts

**1. Add to HTML head:**
```html
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700&display=swap" rel="stylesheet">
```

**2. Use in CSS:**
```css
body {
    font-family: 'Roboto', sans-serif;
}
```

### Text Alignment

```css
.left {
    text-align: left; /* Default */
}

.center {
    text-align: center;
}

.right {
    text-align: right;
}

.justify {
    text-align: justify; /* Stretched to edges */
}
```

### Text Decoration

```css
a {
    text-decoration: underline;
}

.no-underline {
    text-decoration: none;
}

.strikethrough {
    text-decoration: line-through;
}

.fancy {
    text-decoration: underline wavy red;
}
```

### Text Transform

```css
.uppercase {
    text-transform: uppercase; /* HELLO */
}

.lowercase {
    text-transform: lowercase; /* hello */
}

.capitalize {
    text-transform: capitalize; /* Hello World */
}
```

### Text Spacing

```css
/* Letter spacing */
.spaced {
    letter-spacing: 2px;
}

.tight {
    letter-spacing: -1px;
}

/* Word spacing */
.word-spaced {
    word-spacing: 5px;
}

/* Text indent (first line) */
p {
    text-indent: 2em;
}
```

### Line Height: Breathing room

```css
p {
    line-height: 1.6; /* 1.6x font size - unitless recommended */
}

.tight {
    line-height: 1.2;
}

.loose {
    line-height: 2;
}

/* With units */
.fixed {
    line-height: 24px; /* Fixed height */
}
```

### Watch It!
⚠️ **Use unitless line-height!** `line-height: 1.5` is better than `line-height: 24px`. Unitless values scale with font size.

### Text Shadows

```css
h1 {
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
    /* x-offset y-offset blur color */
}

.multiple-shadows {
    text-shadow:
        2px 2px 4px red,
        -2px -2px 4px blue;
}
```

### Direction: For RTL languages

```css
.arabic {
    direction: rtl; /* Right to left */
}

.english {
    direction: ltr; /* Left to right */
}
```

### Brain Power
🧠 Why is line-height important? What happens if it's too small?

**Answer:** Line-height affects readability! Too small and lines crash into each other. Too large and text feels disconnected. Sweet spot: 1.4-1.8 for body text.

### Complete Typography Example

```css
body {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Arial, sans-serif;
    font-size: 16px;
    line-height: 1.6;
    color: #333;
}

h1 {
    font-size: 2.5em;
    font-weight: 700;
    line-height: 1.2;
    margin-bottom: 0.5em;
}

p {
    margin-bottom: 1em;
    text-align: justify;
}

a {
    color: #0066cc;
    text-decoration: none;
}

a:hover {
    text-decoration: underline;
}

code {
    font-family: "Courier New", monospace;
    background-color: #f4f4f4;
    padding: 2px 4px;
    border-radius: 3px;
}
```

### There are NO Dumb Questions

**Q: What's the difference between em and rem?**
**A:** `em` is relative to parent font size. `rem` is relative to root (`<html>`) font size. Use `rem` for consistency.

**Q: Should I use px or em for font sizes?**
**A:** Use relative units (`em`, `rem`, `%`) for accessibility. Users can adjust browser font size settings.

**Q: What's a good line-height for body text?**
**A:** 1.5-1.6 is the sweet spot for readability. Headings can be tighter (1.2-1.3).

---

## 6. The Box Model: Everything is a Box

### The fundamental truth of CSS

**Every element is a rectangular box.** Even if it looks round (border-radius), it's still a box underneath. Understanding the box model is THE key to mastering CSS layout.

### The Box Model: Four layers

```
┌─────────────────────────────┐
│         MARGIN              │  (transparent)
│  ┌─────────────────────┐   │
│  │      BORDER         │   │  (visible)
│  │  ┌───────────────┐  │   │
│  │  │   PADDING     │  │   │  (transparent)
│  │  │  ┌─────────┐  │  │   │
│  │  │  │ CONTENT │  │  │   │  (your content)
│  │  │  └─────────┘  │  │   │
│  │  └───────────────┘  │   │
│  └─────────────────────┘   │
└─────────────────────────────┘
```

### Content: The innermost box

```css
div {
    width: 200px;
    height: 100px;
}
```

This sets the content area size.

### Padding: Space inside the border

```css
/* All sides */
.box {
    padding: 20px;
}

/* Vertical | Horizontal */
.box {
    padding: 10px 20px;
}

/* Top | Horizontal | Bottom */
.box {
    padding: 10px 20px 30px;
}

/* Top | Right | Bottom | Left (clockwise) */
.box {
    padding: 10px 20px 30px 40px;
}

/* Individual sides */
.box {
    padding-top: 10px;
    padding-right: 20px;
    padding-bottom: 10px;
    padding-left: 20px;
}
```

**Mnemonic for 4 values:** TRouBLe (Top, Right, Bottom, Left)

### Border: The visible edge

```css
/* Shorthand: width style color */
.box {
    border: 2px solid black;
}

/* Individual properties */
.box {
    border-width: 2px;
    border-style: solid;
    border-color: black;
}

/* Individual sides */
.box {
    border-top: 1px solid red;
    border-right: 2px dashed blue;
    border-bottom: 3px dotted green;
    border-left: 4px double orange;
}

/* Border radius (rounded corners) */
.box {
    border-radius: 10px; /* All corners */
}

.box {
    border-radius: 10px 20px 30px 40px; /* TL TR BR BL */
}

/* Circle */
.circle {
    width: 100px;
    height: 100px;
    border-radius: 50%;
}
```

**Border styles:** `solid`, `dashed`, `dotted`, `double`, `groove`, `ridge`, `inset`, `outset`, `none`, `hidden`

### Margin: Space outside the border

```css
/* Same syntax as padding */
.box {
    margin: 20px;
}

/* Auto centering */
.centered {
    width: 800px;
    margin: 0 auto; /* Vertical 0, Horizontal auto */
}

/* Negative margins (pull elements) */
.overlap {
    margin-top: -20px;
}
```

### Watch It!
⚠️ **Margin collapse!** Vertical margins between elements collapse to the larger of the two. If one element has `margin-bottom: 20px` and the next has `margin-top: 30px`, the space between them is 30px, NOT 50px!

### Width and Height

```css
.box {
    width: 300px;
    height: 200px;
}

/* Min and max */
.responsive {
    width: 80%;
    max-width: 1200px; /* Won't grow beyond this */
    min-width: 320px;  /* Won't shrink below this */
}

.flexible-height {
    min-height: 200px; /* At least this tall */
}
```

### Box-sizing: The game changer

```css
/* Default (ugh) */
.box {
    box-sizing: content-box; /* width = content only */
    width: 200px;
    padding: 20px;
    border: 2px solid black;
    /* Total width = 200 + 40 + 4 = 244px */
}

/* Better! */
.box {
    box-sizing: border-box; /* width = content + padding + border */
    width: 200px;
    padding: 20px;
    border: 2px solid black;
    /* Total width = 200px (padding and border included!) */
}
```

### The CSS reset every project needs

```css
* {
    box-sizing: border-box;
}
```

This makes life so much easier. Width means TOTAL width, not just content.

### Brain Power
🧠 If you have a box with `width: 100px`, `padding: 10px`, `border: 5px`, and `margin: 20px`, what's the total space it takes up?

**Answer:**
- With `box-sizing: content-box`: 100 + 20 + 10 = 130px width (margin doesn't count in width)
- With `box-sizing: border-box`: 100px width (margin doesn't count)
- Space from other elements: Add 40px more (20px margin on each side)

### Outline: Like border, but different

```css
button:focus {
    outline: 2px solid blue;
    outline-offset: 2px; /* Space between element and outline */
}
```

**Outline vs Border:**
- Outline doesn't take up space (doesn't affect layout)
- Outline is always rectangular (no rounded corners)
- Outline goes outside the border
- Great for focus indicators

### Watch It!
⚠️ **Never remove focus outlines without replacing them!** `outline: none` without an alternative makes your site inaccessible to keyboard users.

### Box Shadows: Adding depth

```css
.card {
    box-shadow: 2px 4px 8px rgba(0, 0, 0, 0.2);
    /* x-offset y-offset blur spread color */
}

.elevated {
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

/* Multiple shadows */
.fancy {
    box-shadow:
        0 1px 3px rgba(0, 0, 0, 0.12),
        0 1px 2px rgba(0, 0, 0, 0.24);
}

/* Inset shadow (inside the box) */
.pressed {
    box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.2);
}
```

### Complete Box Model Example

```css
.card {
    /* Box sizing */
    box-sizing: border-box;

    /* Dimensions */
    width: 300px;
    min-height: 200px;

    /* Spacing */
    padding: 20px;
    margin: 20px auto;

    /* Border */
    border: 1px solid #ddd;
    border-radius: 8px;

    /* Shadow */
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);

    /* Background */
    background-color: white;
}
```

### There are NO Dumb Questions

**Q: Why does my width calculation seem wrong?**
**A:** Check your `box-sizing`! With `content-box` (default), padding and border ADD to width. With `border-box`, they're INCLUDED in width.

**Q: When should I use padding vs margin?**
**A:** Padding = space inside (part of clickable area, gets background color). Margin = space outside (separates elements).

**Q: What's the difference between `border` and `outline`?**
**A:** Border affects layout and takes space. Outline doesn't affect layout (overlays). Use outline for focus indicators.

---

## 7. Units: Sizing Things Right

### Absolute vs Relative units

**Absolute units:** Fixed size (same everywhere)
**Relative units:** Based on something else (parent, viewport, font size)

### Absolute Units

```css
/* Pixels (most common) */
.box {
    width: 300px;
    font-size: 16px;
}

/* Points (print) */
@media print {
    p {
        font-size: 12pt;
    }
}

/* Inches, centimeters (rare) */
.print-page {
    width: 8.5in;
    height: 11in;
}
```

**When to use:** Borders, shadows, small fixed sizes

### Relative Units: Font-based

```css
/* em - relative to parent font size */
.parent {
    font-size: 16px;
}

.child {
    font-size: 1.5em; /* 16px × 1.5 = 24px */
    padding: 1em;      /* 24px × 1 = 24px (uses own font size!) */
}

/* rem - relative to root (<html>) font size */
html {
    font-size: 16px;
}

.element {
    font-size: 1.5rem; /* 16px × 1.5 = 24px */
    padding: 2rem;     /* 16px × 2 = 32px (always based on root) */
}

/* Percentage - relative to parent */
.parent {
    width: 400px;
}

.child {
    width: 50%; /* 400px × 0.5 = 200px */
}
```

### Watch It!
⚠️ **em is tricky!** For font-size, it's relative to parent. For other properties, it's relative to the element's OWN font-size. Use `rem` for predictability.

### Relative Units: Viewport-based

```css
/* vw - viewport width (1vw = 1% of viewport width) */
.full-width {
    width: 100vw;
}

.half-width {
    width: 50vw;
}

/* vh - viewport height */
.full-height {
    height: 100vh;
}

.hero {
    height: 80vh;
}

/* vmin - smaller of vw or vh */
.square {
    width: 50vmin;
    height: 50vmin;
}

/* vmax - larger of vw or vh */
.large {
    font-size: 5vmax;
}
```

**Great for:** Full-screen sections, responsive typography

### Brain Power
🧠 If the viewport is 1000px wide and you set `width: 50vw`, how wide is the element? What if you set `font-size: 50vw`?

**Answer:** Both are 500px! (But 500px font size is huge - use vw for font-size carefully!)

### CSS Functions with Units

```css
/* calc() - do math */
.box {
    width: calc(100% - 40px); /* Full width minus 40px */
    height: calc(100vh - 60px); /* Full height minus header */
}

/* min() - smallest value */
.responsive {
    width: min(100%, 800px); /* Smaller of 100% or 800px */
    font-size: min(5vw, 24px);
}

/* max() - largest value */
.readable {
    width: max(50%, 300px); /* Larger of 50% or 300px */
}

/* clamp() - value between min and max */
.fluid {
    font-size: clamp(14px, 2vw, 24px);
    /* min: 14px, ideal: 2vw, max: 24px */
}

.container {
    width: clamp(320px, 80%, 1200px);
}
```

### Which unit should you use?

| Use Case | Recommended Unit | Why |
|----------|------------------|-----|
| Font size | `rem` | Respects user settings, predictable |
| Padding/Margin | `rem` or `em` | Scales with text |
| Width (containers) | `%` or `ch` | Responsive |
| Max-width | `px` or `rem` | Controlled limits |
| Borders | `px` | Consistency |
| Media queries | `em` or `rem` | Respects zoom |
| Viewport sections | `vh`/`vw` | Full-screen layouts |

### Special Units

```css
/* ch - width of "0" character */
p {
    max-width: 60ch; /* Readable line length */
}

/* ex - height of lowercase "x" */
.superscript {
    vertical-align: 1ex;
}

/* Percentage of parent */
.child {
    width: 80%; /* 80% of parent width */
    line-height: 150%; /* 1.5x font size */
}
```

### Watch It!
⚠️ **Viewport units ignore scrollbars!** `100vw` can cause horizontal scrolling if there's a vertical scrollbar. Use `100%` for full width instead.

### Complete Sizing Example

```css
/* Reset root font size */
html {
    font-size: 16px; /* Base for rem calculations */
}

/* Container with responsive width */
.container {
    width: min(90%, 1200px);
    margin: 0 auto;
    padding: 2rem;
}

/* Responsive typography */
h1 {
    font-size: clamp(2rem, 5vw, 4rem);
    line-height: 1.2;
    margin-bottom: 1rem;
}

p {
    font-size: 1rem;
    line-height: 1.6;
    max-width: 65ch; /* Readable line length */
    margin-bottom: 1em;
}

/* Full-height hero section */
.hero {
    height: 100vh;
    padding: 4rem 2rem;
}

/* Responsive card */
.card {
    width: clamp(280px, 100%, 400px);
    padding: 1.5rem;
    border: 1px solid #ddd;
    border-radius: 0.5rem;
}
```

### There are NO Dumb Questions

**Q: Should I use px or rem?**
**A:** Use `rem` for scalable, accessible designs. Use `px` for things that should stay fixed (borders, shadows).

**Q: What's the difference between % and vw?**
**A:** `%` is relative to parent element. `vw` is relative to viewport width (browser window).

**Q: When should I use calc()?**
**A:** When you need to mix units (`calc(100% - 40px)`) or do complex calculations.

**Q: What's a good max-width for readable text?**
**A:** 60-75 characters (use `max-width: 65ch`). Longer lines are hard to read.

---

## 8. Background: More Than Just Color

### Background Color

```css
div {
    background-color: lightblue;
}

.transparent {
    background-color: transparent;
}

.semi-transparent {
    background-color: rgba(0, 0, 0, 0.5);
}
```

### Background Image

```css
.hero {
    background-image: url('hero.jpg');
}

/* Multiple backgrounds (front to back) */
.layered {
    background-image:
        url('foreground.png'),
        url('background.jpg');
}

/* Linear gradient as image */
.gradient {
    background-image: linear-gradient(to right, red, blue);
}
```

### Background Repeat

```css
.tile {
    background-image: url('pattern.png');
    background-repeat: repeat; /* Default - tiles both directions */
}

.repeat-x {
    background-repeat: repeat-x; /* Only horizontal */
}

.repeat-y {
    background-repeat: repeat-y; /* Only vertical */
}

.no-repeat {
    background-repeat: no-repeat; /* Just once */
}
```

### Background Position

```css
.centered {
    background-image: url('logo.png');
    background-repeat: no-repeat;
    background-position: center; /* Center both axes */
}

.top-right {
    background-position: top right;
}

.precise {
    background-position: 50px 100px; /* X, Y offset */
}

.percentage {
    background-position: 50% 50%; /* Centered */
}
```

### Background Size

```css
/* Cover - fills container, may crop */
.cover {
    background-size: cover;
}

/* Contain - fits inside, may show empty space */
.contain {
    background-size: contain;
}

/* Exact size */
.sized {
    background-size: 200px 300px;
}

/* Width specified, height auto */
.auto-height {
    background-size: 100% auto;
}
```

### Background Attachment

```css
/* Scroll with page (default) */
.normal {
    background-attachment: scroll;
}

/* Fixed (parallax effect) */
.parallax {
    background-image: url('mountain.jpg');
    background-attachment: fixed;
    background-position: center;
    background-size: cover;
}
```

### Background Gradients: The fun stuff!

```css
/* Linear gradient */
.linear {
    background: linear-gradient(to right, red, blue);
}

.diagonal {
    background: linear-gradient(45deg, red, blue);
}

.multi-color {
    background: linear-gradient(
        to bottom,
        red 0%,
        yellow 50%,
        green 100%
    );
}

/* Radial gradient */
.radial {
    background: radial-gradient(circle, red, blue);
}

.radial-positioned {
    background: radial-gradient(circle at top left, red, blue);
}

/* Conic gradient (pie chart style) */
.conic {
    background: conic-gradient(red, yellow, green, blue, red);
}

/* Repeating gradients */
.stripes {
    background: repeating-linear-gradient(
        45deg,
        white 0px,
        white 10px,
        black 10px,
        black 20px
    );
}
```

### Background Shorthand

```css
.complete {
    background:
        url('image.jpg')     /* image */
        no-repeat            /* repeat */
        center               /* position */
        / cover              /* size (note the slash!) */
        fixed                /* attachment */
        lightblue;           /* color (behind image) */
}
```

### Watch It!
⚠️ **Background-size requires a slash!** In shorthand, separate position and size with `/`. Example: `center / cover`

### Brain Power
🧠 What's the difference between `background-size: cover` and `background-size: contain`?

**Answer:**
- `cover` scales the image to cover the ENTIRE container (may crop)
- `contain` scales the image to fit INSIDE the container (may leave empty space)

### Complete Background Example

```css
.hero {
    /* Gradient overlay + image */
    background:
        linear-gradient(
            rgba(0, 0, 0, 0.5),
            rgba(0, 0, 0, 0.5)
        ),
        url('hero.jpg') no-repeat center / cover;

    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
}

.pattern-bg {
    background-color: #f0f0f0;
    background-image: url('pattern.svg');
    background-repeat: repeat;
    background-size: 50px 50px;
}

.card {
    background-color: white;
    background-image:
        linear-gradient(135deg, transparent 10%, rgba(0, 0, 0, 0.05) 100%);
    border-radius: 8px;
    padding: 2rem;
}
```

### There are NO Dumb Questions

**Q: Can I use multiple background images?**
**A:** Yes! List them comma-separated. First one is on top.

**Q: What's the difference between `background` and `background-color`?**
**A:** `background` is shorthand for ALL background properties. `background-color` is just color. `background` will reset properties you don't specify!

**Q: Why use gradients instead of images?**
**A:** File size! Gradients are pure CSS (0 bytes to download). Images take bandwidth.

---

## 9. Display: Block, Inline, and Friends

### The Three Display Types You Need to Know

Every HTML element has a default display type. Understanding these is CRUCIAL for layout.

### Block: Stacks vertically

```css
div, p, h1, section, article {
    display: block;
}
```

**Characteristics:**
- Takes full width available
- Starts on new line
- Respects width, height, all margins/padding
- Examples: `<div>`, `<p>`, `<h1>`, `<section>`

```css
.block-element {
    display: block;
    width: 300px;
    height: 200px;
    margin: 20px;
    padding: 10px;
}
```

### Inline: Flows with text

```css
span, a, strong, em {
    display: inline;
}
```

**Characteristics:**
- Only takes needed width
- Stays in line with text
- IGNORES width, height, top/bottom margins
- Respects left/right margins and all padding
- Examples: `<span>`, `<a>`, `<strong>`, `<em>`

```css
.inline-element {
    display: inline;
    /* width and height ignored! */
    margin: 10px 20px; /* Only left/right work */
    padding: 5px; /* All sides work, but doesn't push elements down */
}
```

### Inline-block: Best of both worlds

```css
.button {
    display: inline-block;
}
```

**Characteristics:**
- Flows inline (stays in line)
- Respects width, height, ALL margins/padding (like block)
- Perfect for: navigation items, buttons, tags

```css
.nav-item {
    display: inline-block;
    width: 100px;
    padding: 10px 20px;
    margin: 5px;
    text-align: center;
}
```

### Brain Power
🧠 You want to create a horizontal navigation menu. Should you use `display: block`, `display: inline`, or `display: inline-block`? Why?

**Answer:** `inline-block`! You want items to flow horizontally (like inline) but also respect padding and width (like block).

### None: Hide completely

```css
.hidden {
    display: none; /* Removed from layout, takes no space */
}

.invisible {
    visibility: hidden; /* Invisible but still takes space */
}
```

### Watch It!
⚠️ **`display: none` vs `visibility: hidden`!**
- `display: none` = Element doesn't exist (no space)
- `visibility: hidden` = Element is invisible ghost (takes space)

### Flex: Modern layout

```css
.container {
    display: flex;
}

.inline-container {
    display: inline-flex;
}
```

More on this in the Layouts section!

### Grid: Modern layout 2

```css
.container {
    display: grid;
}

.inline-container {
    display: inline-grid;
}
```

### Table displays: For table layouts

```css
.table {
    display: table;
}

.table-row {
    display: table-row;
}

.table-cell {
    display: table-cell;
}
```

Rarely used (use actual `<table>` or Flexbox/Grid instead).

### Complete Display Example

```css
/* Horizontal navigation */
nav ul {
    list-style: none;
    padding: 0;
}

nav li {
    display: inline-block;
    margin: 0 10px;
}

nav a {
    display: block; /* Make entire area clickable */
    padding: 10px 20px;
    text-decoration: none;
}

/* Modal overlay */
.modal {
    display: none; /* Hidden by default */
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.8);
}

.modal.active {
    display: flex; /* Show as flex container */
    align-items: center;
    justify-content: center;
}

/* Cards in a row */
.card-container {
    display: flex;
}

.card {
    flex: 1;
    margin: 10px;
}
```

### There are NO Dumb Questions

**Q: Why can't I set width on inline elements?**
**A:** Because inline elements flow with text! They only take the space they need. Use `inline-block` instead.

**Q: When should I use inline-block vs flexbox?**
**A:** Inline-block for simple horizontal layouts (nav menus). Flexbox for complex layouts with alignment control.

**Q: What's the difference between `display: none` and `opacity: 0`?**
**A:** `display: none` removes from layout. `opacity: 0` is invisible but still takes space and can be clicked!

---

## 10. Position: Moving Things Around

### The Five Position Values

Position controls HOW an element is positioned in the document flow.

### Static: Default (don't use this)

```css
div {
    position: static; /* Default - normal flow */
}
```

Can't use top/right/bottom/left offsets. Rarely specified explicitly.

### Relative: Relative to self

```css
.nudge {
    position: relative;
    top: 10px;   /* Move down 10px from where it would be */
    left: 20px;  /* Move right 20px */
}
```

**Key points:**
- Element moves FROM its normal position
- Original space is STILL RESERVED (ghost element)
- Creates positioning context for absolute children

```css
.container {
    position: relative; /* Creates context */
}

.container .absolute-child {
    position: absolute; /* Positioned relative to container */
    top: 0;
    right: 0;
}
```

### Absolute: Relative to positioned ancestor

```css
.parent {
    position: relative; /* Positioning context */
}

.child {
    position: absolute;
    top: 20px;     /* 20px from parent's top */
    right: 10px;   /* 10px from parent's right */
}
```

**Key points:**
- Removed from normal flow (doesn't take space)
- Positioned relative to nearest positioned ancestor
- If no positioned ancestor, uses viewport
- Often used with `position: relative` parent

### Fixed: Relative to viewport

```css
.header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    background: white;
    z-index: 100;
}

.back-to-top {
    position: fixed;
    bottom: 20px;
    right: 20px;
}
```

**Key points:**
- Removed from normal flow
- Stays in place when scrolling
- Positioned relative to viewport
- Great for: headers, floating buttons, modals

### Sticky: Hybrid of relative and fixed

```css
.sticky-header {
    position: sticky;
    top: 0;
    background: white;
}
```

**Key points:**
- Acts relative until you scroll past threshold
- Then "sticks" (acts fixed) until parent ends
- MUST specify top/left/right/bottom
- Great for: table headers, navigation

### Watch It!
⚠️ **Absolute positioned elements need a positioned parent!** If the parent isn't `relative`, `absolute`, `fixed`, or `sticky`, the element will position relative to viewport.

### Brain Power
🧠 You want a close button in the top-right corner of a card. Which position values would you use for the card and button?

**Answer:** Card: `position: relative`, Button: `position: absolute` with `top: 10px; right: 10px;`

### Z-Index: Layering elements

```css
.bottom-layer {
    position: relative;
    z-index: 1;
}

.middle-layer {
    position: relative;
    z-index: 10;
}

.top-layer {
    position: relative;
    z-index: 100;
}
```

**Key points:**
- Higher z-index = on top
- Only works on positioned elements (not static!)
- Creates stacking contexts (can get complex)
- Common values: 1, 10, 100, 1000 (leave room!)

### Watch It!
⚠️ **Z-index doesn't work on static positioned elements!** Add `position: relative` at minimum.

### Common Position Patterns

```css
/* Full-screen overlay */
.overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    z-index: 1000;
}

/* Centered modal */
.modal {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: white;
    padding: 2rem;
    z-index: 1001;
}

/* Floating button */
.fab {
    position: fixed;
    bottom: 20px;
    right: 20px;
    z-index: 999;
}

/* Card with icon */
.card {
    position: relative;
    padding: 2rem;
}

.card .icon {
    position: absolute;
    top: 10px;
    right: 10px;
}

/* Sticky navigation */
.nav {
    position: sticky;
    top: 0;
    background: white;
    z-index: 100;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}
```

### Complete Position Example

```css
/* Page layout with fixed header */
.page-header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 60px;
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    z-index: 100;
}

.page-content {
    margin-top: 60px; /* Account for fixed header */
}

/* Card with badge */
.product-card {
    position: relative;
    padding: 1rem;
    border: 1px solid #ddd;
}

.product-card .sale-badge {
    position: absolute;
    top: -10px;
    right: -10px;
    background: red;
    color: white;
    padding: 5px 10px;
    border-radius: 20px;
}

/* Sticky sidebar */
.sidebar {
    position: sticky;
    top: 80px; /* Below fixed header */
    height: fit-content;
}

/* Back to top button */
.back-to-top {
    position: fixed;
    bottom: 30px;
    right: 30px;
    width: 50px;
    height: 50px;
    background: #333;
    color: white;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 999;
    cursor: pointer;
}
```

### There are NO Dumb Questions

**Q: What's the difference between fixed and sticky?**
**A:** Fixed stays in place always. Sticky scrolls normally until threshold, then sticks until its container ends.

**Q: Why isn't my absolute element positioning correctly?**
**A:** Check if its parent has `position: relative` (or absolute/fixed/sticky). Without it, the element positions relative to viewport!

**Q: Can I use negative values for top/left?**
**A:** Yes! Negative values move in opposite directions. `top: -10px` moves UP.

**Q: What are stacking contexts?**
**A:** Complex topic! Basically, elements with certain CSS properties (position + z-index, opacity, transform) create new "layers". Z-index only works within the same stacking context.

---

## 11. Layouts: Flexbox and Grid

### The Layout Revolution

Before Flexbox and Grid, layouts were HARD (floats, tables, positioning hacks). Now they're... actually pretty easy!

**When to use:**
- **Flexbox:** One-dimensional layouts (rows OR columns)
- **Grid:** Two-dimensional layouts (rows AND columns)
- **Float:** Almost never (legacy technique)

### Flexbox: One dimension at a time

```css
.container {
    display: flex;
}
```

### Flex Direction: Row or column

```css
.row {
    display: flex;
    flex-direction: row; /* Default - horizontal */
}

.column {
    display: flex;
    flex-direction: column; /* Vertical */
}

.row-reverse {
    display: flex;
    flex-direction: row-reverse; /* Right to left */
}

.column-reverse {
    display: flex;
    flex-direction: column-reverse; /* Bottom to top */
}
```

### Justify Content: Main axis alignment

```css
.container {
    display: flex;
    justify-content: flex-start; /* Default - left/top */
}

.center {
    justify-content: center; /* Center */
}

.end {
    justify-content: flex-end; /* Right/bottom */
}

.space-between {
    justify-content: space-between; /* Even space between items */
}

.space-around {
    justify-content: space-around; /* Space around items */
}

.space-evenly {
    justify-content: space-evenly; /* Even space everywhere */
}
```

### Align Items: Cross axis alignment

```css
.container {
    display: flex;
    height: 200px;
    align-items: stretch; /* Default - fill container */
}

.center {
    align-items: center; /* Vertical center */
}

.start {
    align-items: flex-start; /* Top */
}

.end {
    align-items: flex-end; /* Bottom */
}

.baseline {
    align-items: baseline; /* Align text baselines */
}
```

### The Perfect Centering

```css
.center-everything {
    display: flex;
    justify-content: center; /* Horizontal */
    align-items: center; /* Vertical */
    height: 100vh;
}
```

### Flex Wrap: Multiple lines

```css
.container {
    display: flex;
    flex-wrap: nowrap; /* Default - single line */
}

.wrap {
    display: flex;
    flex-wrap: wrap; /* Multiple lines */
}

.wrap-reverse {
    display: flex;
    flex-wrap: wrap-reverse; /* Wrap bottom to top */
}
```

### Gap: Spacing between items

```css
.container {
    display: flex;
    gap: 20px; /* Space between items */
}

.different-gaps {
    display: flex;
    gap: 10px 20px; /* row gap, column gap */
}
```

### Brain Power
🧠 How would you create a navigation bar with items evenly spaced and vertically centered?

**Answer:**
```css
nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
```

### Flex Items: Child properties

```css
/* Flex grow - how much to grow */
.grow {
    flex-grow: 1; /* Take available space */
}

.grow-more {
    flex-grow: 2; /* Take 2x more space */
}

/* Flex shrink - how much to shrink */
.no-shrink {
    flex-shrink: 0; /* Don't shrink */
}

/* Flex basis - initial size */
.item {
    flex-basis: 200px; /* Start at 200px */
}

/* Flex shorthand */
.item {
    flex: 1 1 200px; /* grow shrink basis */
}

.item {
    flex: 1; /* Common: grow, shrink, basis auto */
}

/* Align self - override align-items */
.special {
    align-self: flex-end; /* Different alignment */
}

/* Order - change visual order */
.first {
    order: -1; /* Appear first */
}

.last {
    order: 1; /* Appear last */
}
```

### Watch It!
⚠️ **`justify-content` and `align-items` flip with `flex-direction: column`!** In columns, `justify-content` controls vertical, `align-items` controls horizontal.

### Complete Flexbox Example

```css
/* Responsive card grid */
.card-container {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
}

.card {
    flex: 1 1 300px; /* Grow, shrink, min 300px */
    padding: 1.5rem;
    border: 1px solid #ddd;
    border-radius: 8px;
}

/* Header with logo and nav */
.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
}

.nav {
    display: flex;
    gap: 20px;
}

/* Perfect centering */
.hero {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
    text-align: center;
}
```

### Grid: Two dimensions

```css
.container {
    display: grid;
}
```

### Grid Template: Define columns and rows

```css
/* Three equal columns */
.grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
}

/* Shorthand with repeat */
.grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
}

/* Different sizes */
.grid {
    display: grid;
    grid-template-columns: 200px 1fr 2fr;
    /* Fixed, flexible, more flexible */
}

/* Rows */
.grid {
    display: grid;
    grid-template-rows: 100px auto 50px;
}

/* Auto-fill (responsive) */
.responsive-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
}
```

### Grid Gap

```css
.grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px; /* All gaps */
}

.different-gaps {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px 20px; /* row gap, column gap */
}
```

### Placing Items

```css
/* Span multiple columns */
.item-1 {
    grid-column: 1 / 3; /* Start line 1, end line 3 (2 columns) */
}

.item-2 {
    grid-column: span 2; /* Span 2 columns */
}

/* Span multiple rows */
.item-3 {
    grid-row: 1 / 3; /* Span 2 rows */
}

/* Place in specific cell */
.item-4 {
    grid-column: 2;
    grid-row: 2;
}

/* Shorthand */
.item-5 {
    grid-area: 1 / 2 / 3 / 4;
    /* row-start / col-start / row-end / col-end */
}
```

### Named Grid Areas

```css
.container {
    display: grid;
    grid-template-areas:
        "header header header"
        "sidebar content content"
        "footer footer footer";
    grid-template-columns: 200px 1fr 1fr;
    gap: 20px;
}

.header {
    grid-area: header;
}

.sidebar {
    grid-area: sidebar;
}

.content {
    grid-area: content;
}

.footer {
    grid-area: footer;
}
```

### Alignment in Grid

```css
.grid {
    display: grid;

    /* Align all items */
    justify-items: center; /* Horizontal */
    align-items: center; /* Vertical */

    /* Align grid itself */
    justify-content: center; /* Grid horizontal */
    align-content: center; /* Grid vertical */
}

/* Individual item */
.item {
    justify-self: end; /* This item only */
    align-self: start;
}
```

### Complete Grid Example

```css
/* Classic layout */
.page {
    display: grid;
    grid-template-areas:
        "header header"
        "sidebar main"
        "footer footer";
    grid-template-columns: 250px 1fr;
    grid-template-rows: 60px 1fr 40px;
    min-height: 100vh;
    gap: 0;
}

.header {
    grid-area: header;
    background: #333;
    color: white;
}

.sidebar {
    grid-area: sidebar;
    background: #f0f0f0;
    padding: 1rem;
}

.main {
    grid-area: main;
    padding: 2rem;
}

.footer {
    grid-area: footer;
    background: #333;
    color: white;
}

/* Responsive card grid */
.card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 20px;
}

/* Image gallery */
.gallery {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 10px;
}

.gallery img {
    width: 100%;
    height: 200px;
    object-fit: cover;
}
```

### Flexbox vs Grid: When to use each

| Use Flexbox | Use Grid |
|-------------|----------|
| One-dimensional (row OR column) | Two-dimensional (rows AND columns) |
| Content-first (size based on content) | Layout-first (define grid first) |
| Navigation bars | Page layouts |
| Centering things | Image galleries |
| Equal-height cards | Dashboard layouts |

### Watch It!
⚠️ **Grid `fr` unit is not the same as Flexbox `flex: 1`!** `fr` is a fraction of available space. `flex: 1` is a growth factor.

### There are NO Dumb Questions

**Q: Should I use Flexbox or Grid?**
**A:** Both! Use Grid for overall page layout, Flexbox for components. They complement each other.

**Q: What's the `fr` unit?**
**A:** Fraction of available space. `1fr 2fr` means second column is twice as wide as first.

**Q: What's `auto-fit` vs `auto-fill`?**
**A:** `auto-fit` collapses empty columns. `auto-fill` keeps them. Use `auto-fit` for most cases.

**Q: Can I nest Grid and Flexbox?**
**A:** Absolutely! Grid container children can be Flex containers and vice versa.

---

## 12. Transforms and Animations

### Transforms: Move, scale, rotate, skew

```css
/* Translate (move) */
.move {
    transform: translate(50px, 100px); /* X, Y */
}

.move-x {
    transform: translateX(50px);
}

.move-y {
    transform: translateY(100px);
}

/* Scale */
.bigger {
    transform: scale(1.5); /* 1.5x size */
}

.smaller {
    transform: scale(0.5); /* Half size */
}

.stretch {
    transform: scale(2, 0.5); /* Width, height */
}

/* Rotate */
.rotate {
    transform: rotate(45deg);
}

.spin {
    transform: rotate(180deg);
}

/* Skew */
.skew {
    transform: skew(10deg, 5deg); /* X, Y */
}

/* Multiple transforms */
.complex {
    transform: translate(50px, 0) rotate(45deg) scale(1.2);
}
```

### Transform Origin: Pivot point

```css
.box {
    transform: rotate(45deg);
    transform-origin: top left; /* Rotate from top-left */
}

.box {
    transform: rotate(45deg);
    transform-origin: 50% 50%; /* Center (default) */
}

.box {
    transform: rotate(45deg);
    transform-origin: 100% 100%; /* Bottom-right */
}
```

### 3D Transforms

```css
/* Rotate in 3D */
.rotate-3d {
    transform: rotateX(45deg) rotateY(45deg) rotateZ(45deg);
}

/* Perspective */
.parent {
    perspective: 1000px;
}

.child {
    transform: rotateY(45deg);
}
```

### Transitions: Smooth changes

```css
.box {
    background: blue;
    transition: background 0.3s ease;
}

.box:hover {
    background: red;
}

/* Multiple properties */
.box {
    transition:
        background 0.3s ease,
        transform 0.5s ease,
        opacity 0.2s linear;
}

/* All properties */
.box {
    transition: all 0.3s ease;
}
```

**Timing functions:**
- `ease` - Slow start, fast middle, slow end (default)
- `linear` - Constant speed
- `ease-in` - Slow start
- `ease-out` - Slow end
- `ease-in-out` - Slow start and end
- `cubic-bezier()` - Custom curve

### Watch It!
⚠️ **Not all properties can be transitioned!** You can't transition `display`, `font-family`, or `position`. Use opacity and transforms instead.

### Keyframe Animations: Complex motion

```css
/* Define animation */
@keyframes slide-in {
    from {
        transform: translateX(-100%);
        opacity: 0;
    }
    to {
        transform: translateX(0);
        opacity: 1;
    }
}

/* Use animation */
.element {
    animation: slide-in 0.5s ease-out;
}

/* Multiple keyframes */
@keyframes bounce {
    0% {
        transform: translateY(0);
    }
    50% {
        transform: translateY(-20px);
    }
    100% {
        transform: translateY(0);
    }
}

.bouncy {
    animation: bounce 1s ease-in-out infinite;
}
```

### Animation Properties

```css
.animated {
    animation-name: slide-in;
    animation-duration: 1s;
    animation-timing-function: ease-out;
    animation-delay: 0.5s;
    animation-iteration-count: 3; /* or infinite */
    animation-direction: alternate; /* normal, reverse, alternate, alternate-reverse */
    animation-fill-mode: forwards; /* Keep final state */
    animation-play-state: running; /* or paused */
}

/* Shorthand */
.animated {
    animation: slide-in 1s ease-out 0.5s 3 alternate forwards;
    /* name duration timing delay count direction fill-mode */
}
```

### Brain Power
🧠 How would you create a pulsing button that grows and shrinks continuously?

**Answer:**
```css
@keyframes pulse {
    0%, 100% {
        transform: scale(1);
    }
    50% {
        transform: scale(1.1);
    }
}

.pulse-button {
    animation: pulse 2s ease-in-out infinite;
}
```

### Common Animation Patterns

```css
/* Fade in */
@keyframes fade-in {
    from {
        opacity: 0;
    }
    to {
        opacity: 1;
    }
}

/* Slide in from left */
@keyframes slide-in-left {
    from {
        transform: translateX(-100%);
    }
    to {
        transform: translateX(0);
    }
}

/* Spin */
@keyframes spin {
    from {
        transform: rotate(0deg);
    }
    to {
        transform: rotate(360deg);
    }
}

/* Shake */
@keyframes shake {
    0%, 100% { transform: translateX(0); }
    25% { transform: translateX(-10px); }
    75% { transform: translateX(10px); }
}

/* Bounce */
@keyframes bounce {
    0%, 20%, 50%, 80%, 100% {
        transform: translateY(0);
    }
    40% {
        transform: translateY(-30px);
    }
    60% {
        transform: translateY(-15px);
    }
}
```

### Complete Animation Example

```css
/* Loading spinner */
.spinner {
    width: 40px;
    height: 40px;
    border: 4px solid rgba(0, 0, 0, 0.1);
    border-top-color: #333;
    border-radius: 50%;
    animation: spin 1s linear infinite;
}

@keyframes spin {
    to {
        transform: rotate(360deg);
    }
}

/* Animated button */
.button {
    background: blue;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: all 0.3s ease;
}

.button:hover {
    background: darkblue;
    transform: translateY(-2px);
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.button:active {
    transform: translateY(0);
}

/* Animated card on load */
.card {
    animation: slide-up 0.6s ease-out;
}

@keyframes slide-up {
    from {
        transform: translateY(50px);
        opacity: 0;
    }
    to {
        transform: translateY(0);
        opacity: 1;
    }
}

/* Notification animation */
.notification {
    animation: slide-in-right 0.3s ease-out;
}

.notification.closing {
    animation: slide-out-right 0.3s ease-in;
}

@keyframes slide-in-right {
    from {
        transform: translateX(100%);
    }
    to {
        transform: translateX(0);
    }
}

@keyframes slide-out-right {
    from {
        transform: translateX(0);
    }
    to {
        transform: translateX(100%);
    }
}
```

### Performance Tips

```css
/* Good - GPU accelerated */
.fast {
    transform: translateX(100px);
    opacity: 0.5;
}

/* Bad - triggers layout recalculation */
.slow {
    left: 100px;
    width: 50%;
}
```

### Watch It!
⚠️ **Animate transform and opacity for best performance!** Animating `width`, `height`, `top`, `left` forces browser to recalculate layout (slow). Use `transform` and `opacity` instead (GPU-accelerated).

### There are NO Dumb Questions

**Q: What's the difference between transitions and animations?**
**A:** Transitions are simple A-to-B changes (hover effects). Animations have multiple keyframes and more control.

**Q: Can I pause an animation?**
**A:** Yes! Set `animation-play-state: paused`. Great for pause buttons.

**Q: Why do some animations feel janky?**
**A:** Animating properties that trigger layout (width, height, top, left) is slow. Use transforms and opacity instead.

**Q: What's `will-change`?**
**A:** Tells browser to optimize for animation. Use sparingly: `will-change: transform, opacity`.

---

## 13. Responsive Design: One Size Fits All

### Mobile-first is best

Design for mobile first, then add complexity for larger screens.

### Media Queries: Conditional CSS

```css
/* Mobile styles (default) */
body {
    font-size: 14px;
}

/* Tablet and up */
@media (min-width: 768px) {
    body {
        font-size: 16px;
    }
}

/* Desktop and up */
@media (min-width: 1024px) {
    body {
        font-size: 18px;
    }
}

/* Large desktop */
@media (min-width: 1440px) {
    body {
        font-size: 20px;
    }
}
```

### Common Breakpoints

```css
/* Mobile: 0-767px (default) */

/* Tablet: 768px+ */
@media (min-width: 768px) { }

/* Desktop: 1024px+ */
@media (min-width: 1024px) { }

/* Large desktop: 1440px+ */
@media (min-width: 1440px) { }
```

### Media Query Features

```css
/* Width */
@media (min-width: 768px) { }
@media (max-width: 767px) { }
@media (min-width: 768px) and (max-width: 1023px) { }

/* Height */
@media (min-height: 600px) { }

/* Orientation */
@media (orientation: portrait) { }
@media (orientation: landscape) { }

/* Aspect ratio */
@media (aspect-ratio: 16/9) { }

/* Color scheme */
@media (prefers-color-scheme: dark) {
    body {
        background: #222;
        color: white;
    }
}

/* Reduced motion (accessibility!) */
@media (prefers-reduced-motion: reduce) {
    * {
        animation: none !important;
        transition: none !important;
    }
}

/* Print */
@media print {
    .no-print {
        display: none;
    }
}
```

### Watch It!
⚠️ **Always respect `prefers-reduced-motion`!** Some users get motion sickness from animations. Disable animations for them.

### Container Queries: Component-based responsive

```css
/* Define container */
.card-container {
    container-type: inline-size;
    container-name: card;
}

/* Query container, not viewport */
@container card (min-width: 400px) {
    .card {
        display: flex;
    }
}

@container card (min-width: 600px) {
    .card {
        display: grid;
        grid-template-columns: 1fr 1fr;
    }
}
```

### Responsive Typography

```css
/* Fluid typography */
h1 {
    font-size: clamp(2rem, 5vw, 4rem);
    /* min: 2rem, ideal: 5vw, max: 4rem */
}

p {
    font-size: clamp(1rem, 2vw, 1.25rem);
}

/* Responsive line length */
.content {
    max-width: min(90%, 65ch);
}
```

### Responsive Images

```css
/* Fluid images */
img {
    max-width: 100%;
    height: auto;
}

/* Art direction with picture */
```

```html
<picture>
    <source media="(min-width: 1024px)" srcset="large.jpg">
    <source media="(min-width: 768px)" srcset="medium.jpg">
    <img src="small.jpg" alt="Responsive image">
</picture>
```

### Brain Power
🧠 Why start with mobile-first instead of desktop-first?

**Answer:** It's easier to add complexity than remove it! Mobile forces you to prioritize content. Plus, mobile users often have slower connections - starting small means faster initial loads.

### Responsive Layout Patterns

```css
/* Stack on mobile, side-by-side on desktop */
.flex-container {
    display: flex;
    flex-direction: column;
    gap: 20px;
}

@media (min-width: 768px) {
    .flex-container {
        flex-direction: row;
    }
}

/* Responsive grid */
.grid {
    display: grid;
    grid-template-columns: 1fr; /* Mobile: 1 column */
    gap: 20px;
}

@media (min-width: 768px) {
    .grid {
        grid-template-columns: repeat(2, 1fr); /* Tablet: 2 columns */
    }
}

@media (min-width: 1024px) {
    .grid {
        grid-template-columns: repeat(3, 1fr); /* Desktop: 3 columns */
    }
}

/* Auto-responsive grid (no media queries!) */
.auto-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 20px;
}
```

### Hide/Show Elements

```css
/* Hide on mobile */
.desktop-only {
    display: none;
}

@media (min-width: 768px) {
    .desktop-only {
        display: block;
    }
}

/* Hide on desktop */
.mobile-only {
    display: block;
}

@media (min-width: 768px) {
    .mobile-only {
        display: none;
    }
}
```

### Complete Responsive Example

```css
/* Base (mobile) styles */
.container {
    width: 100%;
    padding: 1rem;
}

.header {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

.nav {
    display: flex;
    flex-direction: column;
}

.main {
    padding: 1rem;
}

.sidebar {
    display: none; /* Hidden on mobile */
}

.card-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 1rem;
}

/* Tablet */
@media (min-width: 768px) {
    .container {
        padding: 2rem;
    }

    .header {
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
    }

    .nav {
        flex-direction: row;
        gap: 2rem;
    }

    .card-grid {
        grid-template-columns: repeat(2, 1fr);
    }
}

/* Desktop */
@media (min-width: 1024px) {
    .container {
        max-width: 1200px;
        margin: 0 auto;
    }

    .page-layout {
        display: grid;
        grid-template-columns: 250px 1fr;
        gap: 2rem;
    }

    .sidebar {
        display: block;
    }

    .card-grid {
        grid-template-columns: repeat(3, 1fr);
    }
}

/* Large desktop */
@media (min-width: 1440px) {
    .card-grid {
        grid-template-columns: repeat(4, 1fr);
    }
}

/* Dark mode */
@media (prefers-color-scheme: dark) {
    body {
        background: #1a1a1a;
        color: #f0f0f0;
    }

    .card {
        background: #2a2a2a;
        border-color: #444;
    }
}

/* Reduced motion */
@media (prefers-reduced-motion: reduce) {
    *,
    *::before,
    *::after {
        animation-duration: 0.01ms !important;
        animation-iteration-count: 1 !important;
        transition-duration: 0.01ms !important;
    }
}
```

### There are NO Dumb Questions

**Q: What breakpoints should I use?**
**A:** Start with content-based breakpoints (where YOUR design breaks), not device-based. Common ones: 768px (tablet), 1024px (desktop).

**Q: Should I use `min-width` or `max-width`?**
**A:** Use `min-width` for mobile-first (add styles as screen grows). Use `max-width` for desktop-first (remove styles as screen shrinks).

**Q: What's the difference between media queries and container queries?**
**A:** Media queries check viewport size. Container queries check container size. Container queries are better for reusable components!

---

## 14. CSS Variables and Functions

### CSS Variables (Custom Properties)

```css
/* Define variables in :root */
:root {
    --primary-color: #007bff;
    --secondary-color: #6c757d;
    --font-size-base: 16px;
    --spacing-unit: 8px;
}

/* Use variables */
.button {
    background-color: var(--primary-color);
    font-size: var(--font-size-base);
    padding: calc(var(--spacing-unit) * 2);
}

/* Variables can reference other variables */
:root {
    --primary: blue;
    --primary-dark: darkblue;
    --button-bg: var(--primary);
}

/* Fallback values */
.element {
    color: var(--text-color, black); /* If --text-color not defined, use black */
}
```

### Scoped Variables

```css
:root {
    --color: blue;
}

.section {
    --color: red; /* Override for this section */
}

.section p {
    color: var(--color); /* Will be red */
}

p {
    color: var(--color); /* Will be blue */
}
```

### Dynamic Variables with JavaScript

```css
:root {
    --theme-color: blue;
}
```

```javascript
// Change variable value
document.documentElement.style.setProperty('--theme-color', 'red');

// Get variable value
const color = getComputedStyle(document.documentElement)
    .getPropertyValue('--theme-color');
```

### Brain Power
🧠 Why use CSS variables instead of SCSS/Sass variables?

**Answer:** CSS variables are LIVE! You can change them at runtime with JavaScript, use them in media queries, and they cascade/inherit. SCSS variables are compiled away.

### CSS Functions

#### calc() - Math operations

```css
/* Mix units */
.element {
    width: calc(100% - 40px);
    height: calc(100vh - 60px);
    padding: calc(1rem + 5px);
}

/* Use variables */
:root {
    --header-height: 60px;
}

.content {
    height: calc(100vh - var(--header-height));
}
```

#### min() - Smallest value

```css
/* Responsive without media queries */
.container {
    width: min(90%, 1200px);
    /* 90% on small screens, 1200px max on large */
}

.text {
    font-size: min(5vw, 24px);
}
```

#### max() - Largest value

```css
.element {
    width: max(50%, 300px);
    /* At least 300px, or 50% if larger */
}

.text {
    font-size: max(1rem, 14px);
}
```

#### clamp() - Between min and max

```css
/* Fluid typography */
h1 {
    font-size: clamp(2rem, 5vw, 4rem);
    /* min: 2rem, ideal: 5vw, max: 4rem */
}

/* Fluid spacing */
.section {
    padding: clamp(1rem, 5vw, 3rem);
}

/* Fluid width */
.container {
    width: clamp(320px, 80%, 1200px);
}
```

#### Other useful functions

```css
/* Gradients (covered earlier) */
.gradient {
    background: linear-gradient(45deg, red, blue);
}

/* Shapes */
.triangle {
    clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
}

/* Filters */
.image {
    filter: blur(5px) brightness(0.8);
}

/* Math functions */
.element {
    width: min(max(50%, 300px), 800px);
    /* Clamp without clamp()! */
}
```

### Complete Variables Example

```css
/* Theme variables */
:root {
    /* Colors */
    --color-primary: #007bff;
    --color-secondary: #6c757d;
    --color-success: #28a745;
    --color-danger: #dc3545;
    --color-warning: #ffc107;

    /* Grayscale */
    --color-black: #000;
    --color-white: #fff;
    --gray-100: #f8f9fa;
    --gray-200: #e9ecef;
    --gray-900: #212529;

    /* Spacing */
    --space-xs: 0.25rem;
    --space-sm: 0.5rem;
    --space-md: 1rem;
    --space-lg: 1.5rem;
    --space-xl: 2rem;

    /* Typography */
    --font-family-base: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Arial, sans-serif;
    --font-family-mono: "Courier New", monospace;
    --font-size-base: 16px;
    --font-size-sm: 0.875rem;
    --font-size-lg: 1.25rem;
    --line-height-base: 1.5;

    /* Borders */
    --border-width: 1px;
    --border-color: var(--gray-200);
    --border-radius: 0.25rem;
    --border-radius-lg: 0.5rem;

    /* Shadows */
    --shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.12);
    --shadow-md: 0 4px 6px rgba(0, 0, 0, 0.1);
    --shadow-lg: 0 10px 20px rgba(0, 0, 0, 0.15);

    /* Transitions */
    --transition-base: all 0.3s ease;
}

/* Dark theme */
@media (prefers-color-scheme: dark) {
    :root {
        --color-black: #fff;
        --color-white: #000;
        --gray-100: #212529;
        --gray-900: #f8f9fa;
        --border-color: #444;
    }
}

/* Using the variables */
.button {
    background: var(--color-primary);
    color: var(--color-white);
    padding: var(--space-sm) var(--space-lg);
    border-radius: var(--border-radius);
    font-size: var(--font-size-base);
    transition: var(--transition-base);
}

.card {
    background: var(--color-white);
    border: var(--border-width) solid var(--border-color);
    border-radius: var(--border-radius-lg);
    padding: var(--space-lg);
    box-shadow: var(--shadow-md);
}
```

### Watch It!
⚠️ **CSS variable names are case-sensitive!** `--Primary-Color` and `--primary-color` are different variables.

### There are NO Dumb Questions

**Q: Can I use CSS variables in media queries?**
**A:** No, variables can't be used in media query conditions. But you can CHANGE variable values inside media queries!

**Q: What's the browser support for CSS variables?**
**A:** Excellent! All modern browsers support them. IE11 doesn't, but it's dead.

**Q: Should I use CSS variables or SCSS variables?**
**A:** Both! Use SCSS for build-time values. Use CSS for runtime values and themes.

---

## 15. Best Practices and Methodologies

### CSS Specificity: Understanding the cascade

```css
/* Specificity score: 1 */
p {
    color: blue;
}

/* Specificity score: 10 */
.text {
    color: red;
}

/* Specificity score: 100 */
#main {
    color: green;
}

/* Specificity score: 11 */
p.text {
    color: orange;
}

/* Specificity score: 1000 (avoid!) */
p {
    color: purple !important;
}
```

**Specificity hierarchy:**
1. Inline styles (1000)
2. IDs (100)
3. Classes, attributes, pseudo-classes (10)
4. Elements, pseudo-elements (1)

### Watch It!
⚠️ **Avoid `!important` like the plague!** It breaks the cascade and makes debugging a nightmare. Only use for utility classes or overriding third-party CSS.

### BEM: Block Element Modifier

```css
/* Block */
.card { }

/* Element (part of block) */
.card__title { }
.card__image { }
.card__content { }

/* Modifier (variation) */
.card--featured { }
.card--large { }
.card__title--highlight { }
```

```html
<div class="card card--featured">
    <img class="card__image" src="...">
    <h2 class="card__title card__title--highlight">Title</h2>
    <p class="card__content">Content...</p>
</div>
```

**Benefits:**
- No nesting nightmares
- Clear component structure
- Easy to understand
- Prevents specificity wars

### Performance Best Practices

```css
/* Good - specific selector */
.nav-item { }

/* Bad - expensive */
div div div p { }

/* Good - single class */
.button-primary { }

/* Bad - over-specific */
div#main .sidebar ul li a.button { }
```

**Performance tips:**
- Avoid deep nesting
- Use classes, not complex selectors
- Minimize use of universal selector (`*`)
- Animate `transform` and `opacity` (GPU-accelerated)
- Use `will-change` sparingly

### Accessibility Best Practices

```css
/* Good - clear focus indicator */
a:focus {
    outline: 2px solid blue;
    outline-offset: 2px;
}

/* Bad - removes accessibility */
a:focus {
    outline: none;
}

/* Good - respects user preferences */
@media (prefers-reduced-motion: reduce) {
    * {
        animation-duration: 0.01ms !important;
        transition-duration: 0.01ms !important;
    }
}

/* Good - sufficient contrast */
.text {
    color: #333; /* On white: 12.6:1 ratio */
}

/* Bad - low contrast */
.text {
    color: #ccc; /* On white: 1.6:1 ratio - fails WCAG */
}

/* Good - keyboard navigation */
.skip-link:focus {
    position: static;
}
```

### Organization: File structure

```
styles/
├── base/
│   ├── reset.css
│   ├── typography.css
│   └── variables.css
├── components/
│   ├── buttons.css
│   ├── cards.css
│   └── forms.css
├── layouts/
│   ├── header.css
│   ├── footer.css
│   └── grid.css
├── pages/
│   ├── home.css
│   └── about.css
└── utils/
    └── utilities.css
```

### CSS Methodologies

#### CSS Modules

```css
/* Button.module.css */
.button {
    padding: 10px 20px;
}

.primary {
    background: blue;
}
```

```javascript
import styles from './Button.module.css';

<button className={styles.button + ' ' + styles.primary}>
    Click me
</button>
```

#### CSS-in-JS (Styled Components)

```javascript
import styled from 'styled-components';

const Button = styled.button`
    padding: 10px 20px;
    background: ${props => props.primary ? 'blue' : 'gray'};
`;

<Button primary>Click me</Button>
```

#### Utility-first (Tailwind)

```html
<button class="px-4 py-2 bg-blue-500 text-white rounded">
    Click me
</button>
```

### Modern CSS Reset

```css
/* Box sizing */
*,
*::before,
*::after {
    box-sizing: border-box;
}

/* Remove default margins */
* {
    margin: 0;
    padding: 0;
}

/* Body defaults */
body {
    min-height: 100vh;
    line-height: 1.5;
    -webkit-font-smoothing: antialiased;
}

/* Images */
img,
picture,
video,
canvas,
svg {
    display: block;
    max-width: 100%;
}

/* Form elements */
input,
button,
textarea,
select {
    font: inherit;
}

/* Remove animations for people who prefer not to see them */
@media (prefers-reduced-motion: reduce) {
    *,
    *::before,
    *::after {
        animation-duration: 0.01ms !important;
        animation-iteration-count: 1 !important;
        transition-duration: 0.01ms !important;
        scroll-behavior: auto !important;
    }
}
```

### Brain Power
🧠 You have a class `.button` and an ID `#submit`. If both style the same element with different colors, which wins? Why?

**Answer:** The ID wins! IDs have higher specificity (100) than classes (10). This is why you should avoid styling with IDs.

### Complete Best Practices Example

```css
/* Variables for theming */
:root {
    --primary: #007bff;
    --spacing: 1rem;
    --border-radius: 0.25rem;
}

/* Base styles */
body {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Arial, sans-serif;
    line-height: 1.6;
    color: #333;
}

/* BEM naming */
.card {
    background: white;
    border-radius: var(--border-radius);
    padding: var(--spacing);
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.card__title {
    font-size: 1.5rem;
    margin-bottom: 0.5rem;
}

.card__content {
    color: #666;
}

.card--featured {
    border: 2px solid var(--primary);
}

/* Utility classes */
.text-center {
    text-align: center;
}

.mt-2 {
    margin-top: calc(var(--spacing) * 2);
}

/* Accessibility */
.sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border-width: 0;
}

/* Focus indicators */
*:focus {
    outline: 2px solid var(--primary);
    outline-offset: 2px;
}

/* Reduced motion */
@media (prefers-reduced-motion: reduce) {
    * {
        animation-duration: 0.01ms !important;
        transition-duration: 0.01ms !important;
    }
}
```

### There are NO Dumb Questions

**Q: Should I use BEM, CSS Modules, or something else?**
**A:** Depends on your project! BEM for vanilla CSS, CSS Modules for React/Vue, Tailwind for rapid development. Pick what fits your workflow.

**Q: Is inline CSS ever acceptable?**
**A:** For dynamic styles set by JavaScript, yes. For static styles, no.

**Q: How can I improve CSS performance?**
**A:** Minimize file size, reduce specificity, avoid deep nesting, animate transform/opacity, use CSS variables for theming.

**Q: What's the difference between Sass and CSS?**
**A:** Sass is a preprocessor that adds features (variables, nesting, functions). It compiles to regular CSS.

---

## Congratulations!

You've made it through the CSS cheatsheet! Now you can make websites look amazing.

### What's next?

1. **Practice with real projects** - Build, build, build!
2. **Learn a CSS framework** - Bootstrap, Tailwind, Material UI
3. **Master CSS Grid and Flexbox** - They're powerful!
4. **Learn a preprocessor** - Sass or PostCSS
5. **Explore CSS-in-JS** - Styled Components, Emotion
6. **Study design principles** - Color theory, typography, spacing
7. **Keep learning** - CSS evolves constantly

### Brain Power (Final Challenge)
🧠 Build a responsive landing page with:
- Fixed navigation that becomes sticky
- Hero section with gradient overlay
- Card grid that's responsive (no media queries!)
- Smooth animations
- Dark mode support
- Full accessibility

### Additional Resources

- **MDN Web Docs:** https://developer.mozilla.org/en-US/docs/Web/CSS
- **CSS-Tricks:** https://css-tricks.com/
- **Can I Use:** https://caniuse.com/
- **Flexbox Froggy:** https://flexboxfroggy.com/ (game!)
- **Grid Garden:** https://cssgridgarden.com/ (game!)
- **Frontend Roadmap:** https://roadmap.sh/frontend

---

## Quick Reference Card

**Selectors:**
```css
element { }           /* Type */
.class { }           /* Class */
#id { }              /* ID */
* { }                /* Universal */
element1, element2   /* Grouping */
parent child { }     /* Descendant */
parent > child { }   /* Direct child */
element + next { }   /* Next sibling */
element ~ siblings   /* All siblings */
element:hover { }    /* Pseudo-class */
element::before { }  /* Pseudo-element */
[attribute] { }      /* Attribute */
```

**Box Model:**
```css
width, height
padding, margin
border, outline
box-sizing: border-box;
```

**Display:**
```css
display: block | inline | inline-block | flex | grid | none;
```

**Position:**
```css
position: static | relative | absolute | fixed | sticky;
top, right, bottom, left
z-index
```

**Flexbox:**
```css
display: flex;
flex-direction: row | column;
justify-content: center | space-between | ...
align-items: center | stretch | ...
gap: 20px;
```

**Grid:**
```css
display: grid;
grid-template-columns: repeat(3, 1fr);
grid-template-rows: auto;
gap: 20px;
```

**Colors:**
```css
color: red | #FF0000 | rgb(255,0,0) | hsl(0,100%,50%);
```

**Units:**
```css
px, em, rem, %, vw, vh, ch, fr
```

**Functions:**
```css
calc(100% - 40px)
min(90%, 1200px)
max(50%, 300px)
clamp(1rem, 2vw, 2rem)
```

---

**Created in the style of Head First books**

*Now go make the web beautiful!* 🎨