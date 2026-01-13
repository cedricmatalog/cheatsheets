# Head First Next.js Cheatsheet

> Your brain on Next.js. Here you'll learn to build production-ready React apps the way your brain likes to learn - with conversational style, practical examples, and concepts that stick.

---

## How to Use This Cheatsheet

**We think of Next.js as powerful, not perplexing.** You'll find Q&A sections, "Watch It!" warnings, "Brain Power" exercises, and lots of conversation. Next.js has many features, but we'll make them make sense.

**The activities are NOT optional.** The exercises and challenges are part of the learning experience. Create a Next.js app and try the code!

**The redundancy is intentional.** Next.js concepts build on React. You'll see routing, data fetching, and rendering patterns repeatedly - that's how mastery happens.

---

## Prerequisites

**Important:** You MUST know React before learning Next.js:
- Components (functional)
- JSX
- Props and State
- Hooks (useState, useEffect)
- React fundamentals

If you need a refresher, check out the React cheatsheet first!

---

## Table of Contents

1. [Introduction: Why Next.js?](#1-introduction-why-nextjs)
2. [Getting Started: Your First App](#2-getting-started-your-first-app)
3. [Routing: File-Based Routes](#3-routing-file-based-routes)
4. [App Router vs Pages Router](#4-app-router-vs-pages-router)
5. [Advanced Routing Patterns](#5-advanced-routing-patterns)
6. [Rendering: Server and Client](#6-rendering-server-and-client)
7. [Advanced Data Fetching](#7-advanced-data-fetching)
8. [Server Actions: Mutations](#8-server-actions-mutations)
9. [Runtimes: Node.js vs Edge](#9-runtimes-nodejs-vs-edge)
10. [Layouts and Templates](#10-layouts-and-templates)
11. [Styling: Writing CSS](#11-styling-writing-css)
12. [Optimizations: Images, Fonts, Scripts](#12-optimizations-images-fonts-scripts)
13. [API Routes: Building APIs](#13-api-routes-building-apis)
14. [Middleware: Request Processing](#14-middleware-request-processing)
15. [Caching: Performance](#15-caching-performance)
16. [Configuration: Setting Up Your App](#16-configuration-setting-up-your-app)
17. [Testing Your Next.js App](#17-testing-your-nextjs-app)
18. [Deployment: Going Live](#18-deployment-going-live)

---

## 1. Introduction: Why Next.js?

### What is Next.js?

Next.js is a **React framework** for building production-ready web applications. It adds crucial features that React doesn't have out of the box:

- **File-based routing** (no React Router!)
- **Server-side rendering** (SSR)
- **Static site generation** (SSG)
- **API routes** (backend in your React app!)
- **Image optimization**
- **Automatic code splitting**
- **Built-in performance optimizations**

**React = Library (UI only)**
**Next.js = Framework (Full-stack)**

### Why use Next.js?

```
React alone:
- Need to configure routing
- Client-side only (slower initial load)
- No SEO without extra work
- Manual optimization
- Separate backend needed

Next.js:
- Routing built-in ✅
- Server-side rendering ✅
- Great SEO ✅
- Automatic optimization ✅
- Backend features included ✅
```

### SPA vs SSR: What's the difference?

**SPA (Single Page Application) - Traditional React:**
```
1. Browser requests page
2. Server sends empty HTML + large JS bundle
3. Browser downloads and executes JS
4. React renders the page
Result: Slow first load, blank screen while loading
```

**SSR (Server-Side Rendering) - Next.js:**
```
1. Browser requests page
2. Server runs React, generates HTML
3. Server sends ready-to-view HTML
4. Browser shows page immediately
5. React "hydrates" (makes interactive)
Result: Fast first load, content immediately visible
```

### Brain Power
🧠 Why is SSR better for SEO than SPA?

**Answer:** Search engine crawlers see the fully rendered HTML immediately! With SPA, they might see an empty page because they don't always execute JavaScript. SSR = content is already there.

### Rendering Strategies in Next.js

Next.js supports multiple rendering strategies:

- **SSR (Server-Side Rendering):** Render on every request
- **SSG (Static Site Generation):** Render at build time
- **ISR (Incremental Static Regeneration):** Rebuild pages on-demand
- **CSR (Client-Side Rendering):** Render in browser (like traditional React)

### Watch It!
⚠️ **Next.js is NOT a replacement for React!** It's built ON TOP of React. You're still writing React components. Next.js just adds framework features around them.

### There are NO Dumb Questions

**Q: Do I need to learn Next.js if I know React?**
**A:** For production apps, YES! Next.js handles routing, SEO, performance, and deployment much better than vanilla React. Most React jobs use Next.js or similar frameworks.

**Q: What about Remix, Gatsby, or other React frameworks?**
**A:** They're alternatives! Next.js is most popular, but Remix is gaining traction. Learn one deeply, concepts transfer.

**Q: Can I still use React libraries with Next.js?**
**A:** Yes! Any React library works. Next.js is just React with extras.

---

## 2. Getting Started: Your First App

### Creating a Next.js App

```bash
# Create new Next.js app with create-next-app
npx create-next-app@latest my-app

# You'll be asked:
# - TypeScript? → Yes (recommended)
# - ESLint? → Yes
# - Tailwind CSS? → Yes (popular choice)
# - App Router? → Yes (new, recommended)
# - src/ directory? → No (optional)
# - Import alias? → Yes (default @/*)

cd my-app
npm run dev
```

Visit `http://localhost:3000` - your app is running!

### Project Structure: App Router

```
my-app/
├── app/
│   ├── layout.tsx      # Root layout (wraps all pages)
│   ├── page.tsx        # Home page (/)
│   ├── about/
│   │   └── page.tsx    # About page (/about)
│   └── blog/
│       └── page.tsx    # Blog page (/blog)
├── public/
│   └── images/         # Static files (images, etc.)
├── node_modules/
├── package.json
├── next.config.js      # Next.js configuration
└── tsconfig.json       # TypeScript config
```

### Your First Page

```tsx
// app/page.tsx
export default function Home() {
    return (
        <main>
            <h1>Welcome to Next.js!</h1>
            <p>This is your home page</p>
        </main>
    );
}
```

That's it! File in `app/page.tsx` = route at `/`

### Adding Another Page

```tsx
// app/about/page.tsx
export default function About() {
    return (
        <main>
            <h1>About Us</h1>
            <p>Learn more about our company</p>
        </main>
    );
}
```

File in `app/about/page.tsx` = route at `/about`

### Brain Power
🧠 How does Next.js know what route a page should be? What's the pattern?

**Answer:** The folder structure IS the routing! `app/about/page.tsx` → `/about`. `app/blog/post/page.tsx` → `/blog/post`. No configuration needed!

### Watch It!
⚠️ **File must be named `page.tsx` (or `page.jsx`)!** Other filenames won't create routes. `about.tsx` won't work, `about/page.tsx` will.

---

## 3. Routing: File-Based Routes

### How Routing Works

```
app/
├── page.tsx                  → /
├── about/
│   └── page.tsx             → /about
├── blog/
│   ├── page.tsx             → /blog
│   └── [slug]/
│       └── page.tsx         → /blog/:slug (dynamic)
└── dashboard/
    ├── page.tsx             → /dashboard
    └── settings/
        └── page.tsx         → /dashboard/settings
```

### Dynamic Routes: With Parameters

```tsx
// app/blog/[slug]/page.tsx
export default function BlogPost({ params }: { params: { slug: string } }) {
    return (
        <article>
            <h1>Blog Post: {params.slug}</h1>
            <p>This is the blog post for {params.slug}</p>
        </article>
    );
}
```

Visiting `/blog/hello-world` → `params.slug = 'hello-world'`

### Multiple Dynamic Segments

```tsx
// app/shop/[category]/[product]/page.tsx
export default function Product({
    params
}: {
    params: { category: string; product: string }
}) {
    return (
        <div>
            <h1>{params.product}</h1>
            <p>Category: {params.category}</p>
        </div>
    );
}
```

`/shop/electronics/laptop` → `{ category: 'electronics', product: 'laptop' }`

### Catch-All Routes: Multiple Segments

```tsx
// app/docs/[...slug]/page.tsx
export default function Docs({ params }: { params: { slug: string[] } }) {
    return (
        <div>
            <h1>Documentation</h1>
            <p>Path: {params.slug.join('/')}</p>
        </div>
    );
}
```

- `/docs/intro` → `slug = ['intro']`
- `/docs/api/auth` → `slug = ['api', 'auth']`
- `/docs/a/b/c/d` → `slug = ['a', 'b', 'c', 'd']`

### Navigation: Linking Between Pages

```tsx
import Link from 'next/link';

export default function Nav() {
    return (
        <nav>
            <Link href="/">Home</Link>
            <Link href="/about">About</Link>
            <Link href="/blog">Blog</Link>
            <Link href="/blog/hello-world">First Post</Link>
        </nav>
    );
}
```

**Use `<Link>` instead of `<a>`!** Link enables client-side navigation (faster, no full page reload).

### Programmatic Navigation

```tsx
'use client';

import { useRouter } from 'next/navigation';

export default function Button() {
    const router = useRouter();

    const handleClick = () => {
        router.push('/dashboard');
    };

    return <button onClick={handleClick}>Go to Dashboard</button>;
}
```

### Watch It!
⚠️ **App Router uses `'next/navigation'`, Pages Router uses `'next/router'`!** Different imports for different router types. Check which router you're using.

### Route Groups: Organization Without URLs

```tsx
// app/(marketing)/about/page.tsx      → /about
// app/(marketing)/contact/page.tsx    → /contact
// app/(shop)/products/page.tsx        → /products
// app/(shop)/cart/page.tsx            → /cart

// Parentheses are ignored in URLs!
```

Use route groups to organize files without affecting URLs.

### Private Folders: Not Routes

```tsx
// app/_components/Button.tsx   → Not a route
// app/_lib/utils.ts             → Not a route

// Underscore prefix = private, not a route
```

### Complete Routing Example

```
app/
├── page.tsx                              → /
├── about/
│   └── page.tsx                         → /about
├── blog/
│   ├── page.tsx                         → /blog
│   └── [slug]/
│       └── page.tsx                     → /blog/hello-world
├── shop/
│   ├── page.tsx                         → /shop
│   └── [category]/
│       └── [product]/
│           └── page.tsx                 → /shop/electronics/laptop
└── docs/
    └── [...slug]/
        └── page.tsx                     → /docs/any/number/of/segments
```

### There are NO Dumb Questions

**Q: What's the difference between `[slug]` and `[...slug]`?**
**A:** `[slug]` matches ONE segment. `[...slug]` matches ANY NUMBER of segments (catch-all).

**Q: Can I have both `/blog` and `/blog/[slug]`?**
**A:** Yes! `/blog` matches exactly `/blog`. `/blog/[slug]` matches `/blog/anything-else`.

**Q: What about query parameters like `/search?q=hello`?**
**A:** Use `useSearchParams()` hook:
```tsx
'use client';
import { useSearchParams } from 'next/navigation';

const searchParams = useSearchParams();
const query = searchParams.get('q'); // 'hello'
```

---

## 4. App Router vs Pages Router

### Two Routing Systems

Next.js has TWO routing systems:

1. **Pages Router** (Old, stable)
2. **App Router** (New, recommended since Next.js 13)

### Pages Router: The Old Way

```
pages/
├── index.tsx        → /
├── about.tsx        → /about
└── blog/
    └── [slug].tsx   → /blog/:slug
```

**Features:**
- File in `pages/` = route
- `getServerSideProps`, `getStaticProps` for data
- Simpler (less features)

### App Router: The New Way

```
app/
├── page.tsx         → /
├── about/
│   └── page.tsx     → /about
└── blog/
    └── [slug]/
        └── page.tsx → /blog/:slug
```

**Features:**
- Folder with `page.tsx` = route
- React Server Components
- Layouts, loading states, error boundaries
- Server Actions
- More powerful, modern

### Watch It!
⚠️ **Use App Router for new projects!** Pages Router still works (and many projects use it), but App Router is the future. This cheatsheet focuses on App Router.

### Brain Power
🧠 Why do you think Next.js created a new router instead of updating the old one?

**Answer:** React Server Components needed fundamental changes that couldn't be added to Pages Router without breaking changes. App Router was built from scratch for the new React features.

---

## 5. Advanced Routing Patterns

### Parallel Routes: Multiple Pages at Once

Parallel routes let you render multiple pages in the same layout simultaneously. Great for dashboards!

```
app/
└── dashboard/
    ├── @analytics/
    │   └── page.tsx
    ├── @team/
    │   └── page.tsx
    ├── layout.tsx
    └── page.tsx
```

```tsx
// app/dashboard/layout.tsx
export default function DashboardLayout({
    children,
    analytics,
    team
}: {
    children: React.ReactNode;
    analytics: React.ReactNode;
    team: React.ReactNode;
}) {
    return (
        <div className="dashboard">
            <div>{children}</div>
            <div className="sidebar">
                {analytics}
                {team}
            </div>
        </div>
    );
}
```

**The `@` prefix creates a slot!** Each slot is passed to the layout as a prop.

### Intercepting Routes: Modals Without Navigation

Show content in a modal without changing the URL!

```
app/
├── photo/
│   └── [id]/
│       └── page.tsx        → Full page /photo/123
└── feed/
    ├── (..)photo/
    │   └── [id]/
    │       └── page.tsx    → Modal when navigating from /feed
    └── page.tsx
```

```tsx
// app/feed/(..)photo/[id]/page.tsx
import Modal from '@/components/Modal';

export default function PhotoModal({ params }) {
    return (
        <Modal>
            <Image src={`/photos/${params.id}.jpg`} />
        </Modal>
    );
}
```

**Convention:**
- `(.)` = same level
- `(..)` = one level up
- `(..)(..)` = two levels up
- `(...)` = from root

### Redirects: Sending Users Elsewhere

```tsx
import { redirect } from 'next/navigation';

export default async function Page() {
    const user = await getUser();

    if (!user) {
        redirect('/login');
    }

    return <Dashboard user={user} />;
}
```

**Permanent redirects:**
```tsx
import { permanentRedirect } from 'next/navigation';

export default function OldPage() {
    permanentRedirect('/new-page'); // 308 status
}
```

**Client-side redirects:**
```tsx
'use client';

import { useRouter } from 'next/navigation';

export default function Button() {
    const router = useRouter();

    return (
        <button onClick={() => router.push('/dashboard')}>
            Go to Dashboard
        </button>
    );
}
```

### Static vs Dynamic Routes

**Static Routes (Default):**
Generated at build time, served from CDN (fast!)

```tsx
// app/about/page.tsx - Static by default
export default function About() {
    return <h1>About Us</h1>;
}
```

**Dynamic Routes:**
Generated on each request (when you need fresh data)

```tsx
// app/posts/page.tsx - Dynamic (uses no-store)
export default async function Posts() {
    const posts = await fetch('https://api.example.com/posts', {
        cache: 'no-store' // Makes it dynamic
    });

    return <PostsList posts={posts} />;
}
```

**Force dynamic rendering:**
```tsx
export const dynamic = 'force-dynamic';

export default function Page() {
    return <div>Always rendered on request</div>;
}
```

**Force static rendering:**
```tsx
export const dynamic = 'force-static';

export default function Page() {
    return <div>Always static</div>;
}
```

### Route Segment Config Options

```tsx
// app/posts/page.tsx

// Rendering behavior
export const dynamic = 'auto' | 'force-dynamic' | 'error' | 'force-static';

// Revalidation
export const revalidate = false | 0 | number; // seconds

// Runtime
export const runtime = 'nodejs' | 'edge';

// Fetch caching
export const fetchCache = 'auto' | 'default-cache' | 'only-cache' | 'force-cache' | 'force-no-store' | 'default-no-store' | 'only-no-store';
```

### Streaming with Suspense

Stream parts of your page as they load!

```tsx
// app/dashboard/page.tsx
import { Suspense } from 'react';
import SlowComponent from './SlowComponent';

export default function Dashboard() {
    return (
        <div>
            <h1>Dashboard</h1>

            {/* Fast content shows immediately */}
            <QuickStats />

            {/* Slow content streams in */}
            <Suspense fallback={<p>Loading analytics...</p>}>
                <SlowComponent />
            </Suspense>
        </div>
    );
}
```

**Multiple Suspense boundaries:**
```tsx
export default function Page() {
    return (
        <div>
            <Suspense fallback={<Skeleton />}>
                <UserProfile />
            </Suspense>

            <Suspense fallback={<Skeleton />}>
                <RecentPosts />
            </Suspense>

            <Suspense fallback={<Skeleton />}>
                <Analytics />
            </Suspense>
        </div>
    );
}
```

Each section loads independently!

### Watch It!
⚠️ **Parallel routes and intercepting routes are advanced!** Start with basic routing. Use these when you need complex UI patterns like dashboards with multiple views or modals that preserve URLs.

### Brain Power
🧠 Why would you use intercepting routes instead of just showing a modal with state?

**Answer:** Intercepting routes give you a shareable URL! Users can bookmark or share the modal state. Direct navigation shows the full page, but navigation from elsewhere shows the modal.

### There are NO Dumb Questions

**Q: When should I use static vs dynamic routes?**
**A:** Use static (default) for content that doesn't change often - landing pages, blogs, docs. Use dynamic for personalized content, real-time data, or user-specific pages.

**Q: What's the difference between redirect() and router.push()?**
**A:** `redirect()` works in Server Components and causes a hard navigation. `router.push()` is client-side only and does soft navigation. Use redirect() for auth checks on the server.

**Q: Can I mix static and dynamic in the same app?**
**A:** Absolutely! That's the power of Next.js. Your marketing pages can be static, dashboard dynamic, and blog posts static with ISR.

---

## 6. Rendering: Server and Client

### Server Components: The Default

In App Router, **all components are Server Components by default!**

```tsx
// app/page.tsx - This is a Server Component!
export default function Home() {
    return <h1>Hello from the server!</h1>;
}
```

**Server Components:**
- Run on the server
- Can access database directly
- Can't use hooks (useState, useEffect)
- Can't use browser APIs
- Smaller bundle (code stays on server)

### Client Components: Add Interactivity

Add `'use client'` directive to make it a Client Component:

```tsx
'use client';

import { useState } from 'react';

export default function Counter() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>+</button>
        </div>
    );
}
```

**Client Components:**
- Run in the browser
- Can use hooks
- Can use browser APIs
- Needed for interactivity

### When to Use Which?

**Server Components (default):**
- Fetching data
- Accessing backend resources
- Keeping sensitive info on server
- Large dependencies on server

**Client Components (`'use client'`):**
- User interactions (onClick, onChange)
- State (useState, useReducer)
- Effects (useEffect)
- Browser APIs (localStorage, window)
- Custom hooks

### Composition: Mixing Server and Client

```tsx
// app/page.tsx (Server Component)
import Counter from '@/components/Counter';

export default function Home() {
    // Server-side code
    const posts = await fetchPosts();

    return (
        <div>
            <h1>Welcome</h1>
            {/* Server-rendered list */}
            <ul>
                {posts.map(post => <li key={post.id}>{post.title}</li>)}
            </ul>
            {/* Client component for interactivity */}
            <Counter />
        </div>
    );
}

// components/Counter.tsx (Client Component)
'use client';
import { useState } from 'react';

export default function Counter() {
    const [count, setCount] = useState(0);
    return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

### Watch It!
⚠️ **Once you use `'use client'`, all imported components become client components too!** Keep `'use client'` as far down the component tree as possible.

```tsx
// Bad: Everything becomes client
'use client';
import ServerComponent from './Server'; // Now client!

// Good: Only interactive parts are client
import ClientComponent from './Client'; // Has 'use client'
import ServerComponent from './Server'; // Stays server
```

### Brain Power
🧠 Why do Server Components make your app faster?

**Answer:** Their code never goes to the browser! Less JavaScript to download and execute. Server Components render to HTML on the server, so the browser just displays it - no React runtime needed for those parts.

---

## 6. Data Fetching: Getting Data

### Fetching in Server Components

Server Components can `await` data directly:

```tsx
// app/posts/page.tsx (Server Component)
async function getPosts() {
    const res = await fetch('https://api.example.com/posts');
    return res.json();
}

export default async function PostsPage() {
    const posts = await getPosts();

    return (
        <div>
            <h1>Blog Posts</h1>
            <ul>
                {posts.map(post => (
                    <li key={post.id}>{post.title}</li>
                ))}
            </ul>
        </div>
    );
}
```

**No useEffect needed!** Just `async/await` in the component.

### Fetching in Client Components

Client Components use traditional React patterns:

```tsx
'use client';

import { useEffect, useState } from 'react';

export default function Posts() {
    const [posts, setPosts] = useState([]);
    const [loading, setLoading] = useState(true);

    useEffect(() => {
        fetch('https://api.example.com/posts')
            .then(res => res.json())
            .then(data => {
                setPosts(data);
                setLoading(false);
            });
    }, []);

    if (loading) return <p>Loading...</p>;

    return (
        <ul>
            {posts.map(post => <li key={post.id}>{post.title}</li>)}
        </ul>
    );
}
```

### Parallel Data Fetching

```tsx
// Fetch in parallel (faster!)
async function PostPage({ params }) {
    const postPromise = fetch(`/api/posts/${params.id}`);
    const commentsPromise = fetch(`/api/posts/${params.id}/comments`);

    // Wait for both to complete
    const [post, comments] = await Promise.all([
        postPromise.then(r => r.json()),
        commentsPromise.then(r => r.json())
    ]);

    return (
        <article>
            <h1>{post.title}</h1>
            <p>{post.content}</p>
            <h2>Comments ({comments.length})</h2>
            {/* ... */}
        </article>
    );
}
```

### Sequential Data Fetching

```tsx
// Fetch sequentially (when dependent)
async function PostPage({ params }) {
    // Fetch post first
    const post = await fetch(`/api/posts/${params.id}`).then(r => r.json());

    // Then fetch author (depends on post data)
    const author = await fetch(`/api/users/${post.authorId}`).then(r => r.json());

    return (
        <article>
            <h1>{post.title}</h1>
            <p>By {author.name}</p>
        </article>
    );
}
```

### Caching: Automatic Performance

```tsx
// Cached by default (revalidate every hour)
fetch('https://api.example.com/posts', {
    next: { revalidate: 3600 }
});

// Never cache (always fresh)
fetch('https://api.example.com/posts', {
    cache: 'no-store'
});

// Force cache (until manually revalidated)
fetch('https://api.example.com/posts', {
    cache: 'force-cache'
});
```

### Watch It!
⚠️ **Next.js extends fetch() with caching!** Regular `fetch()` doesn't cache. Next.js adds caching and revalidation options automatically.

### Loading States

```tsx
// app/posts/loading.tsx (automatically shown while loading)
export default function Loading() {
    return <p>Loading posts...</p>;
}

// app/posts/page.tsx
export default async function PostsPage() {
    const posts = await fetch('https://api.example.com/posts').then(r => r.json());
    return <PostsList posts={posts} />;
}
```

Create `loading.tsx` file - Next.js shows it automatically while page loads!

### Error Handling

```tsx
// app/posts/error.tsx (shown when error occurs)
'use client';

export default function Error({
    error,
    reset
}: {
    error: Error;
    reset: () => void;
}) {
    return (
        <div>
            <h2>Something went wrong!</h2>
            <p>{error.message}</p>
            <button onClick={reset}>Try again</button>
        </div>
    );
}
```

### Complete Data Fetching Example

```tsx
// app/products/page.tsx
async function getProducts() {
    const res = await fetch('https://api.example.com/products', {
        next: { revalidate: 60 } // Revalidate every minute
    });

    if (!res.ok) {
        throw new Error('Failed to fetch products');
    }

    return res.json();
}

export default async function ProductsPage() {
    const products = await getProducts();

    return (
        <div>
            <h1>Our Products</h1>
            <div className="grid">
                {products.map(product => (
                    <ProductCard key={product.id} product={product} />
                ))}
            </div>
        </div>
    );
}

// app/products/loading.tsx
export default function Loading() {
    return <div>Loading products...</div>;
}

// app/products/error.tsx
'use client';

export default function Error({ error, reset }) {
    return (
        <div>
            <h2>Error loading products</h2>
            <p>{error.message}</p>
            <button onClick={reset}>Try again</button>
        </div>
    );
}
```

### There are NO Dumb Questions

**Q: Do I always need loading.tsx and error.tsx?**
**A:** No, they're optional! But they improve UX. Without them, Next.js shows default loading and error states.

**Q: Can I use libraries like SWR or React Query?**
**A:** Yes, in Client Components! Server Components can fetch directly. Choose based on your needs.

**Q: What's the difference between `revalidate` and `no-store`?**
**A:** `revalidate: 60` caches for 60 seconds, then refreshes. `no-store` never caches, always fetches fresh.

---

## 7. Advanced Data Fetching

### Preloading Data

Preload data before it's needed to improve performance:

```tsx
// app/posts/[id]/page.tsx
import { preload } from 'react-dom';

async function getPost(id: string) {
    const res = await fetch(`https://api.example.com/posts/${id}`);
    return res.json();
}

export default async function Post({ params }: { params: { id: string } }) {
    // Preload before awaiting
    preload(getPost(params.id));

    // Await later
    const post = await getPost(params.id);

    return (
        <article>
            <h1>{post.title}</h1>
            <p>{post.content}</p>
        </article>
    );
}
```

### React Cache: Deduplication

The `cache` function deduplicates requests across your app:

```tsx
// lib/data.ts
import { cache } from 'react';

export const getUser = cache(async (id: string) => {
    console.log('Fetching user:', id); // Only logs once per request!
    const res = await fetch(`https://api.example.com/users/${id}`);
    return res.json();
});
```

```tsx
// Multiple components can call getUser(1) - only fetches once!
// app/page.tsx
import { getUser } from '@/lib/data';

export default async function Page() {
    const user = await getUser('1');
    return <UserProfile user={user} />;
}

// components/UserProfile.tsx
import { getUser } from '@/lib/data';

export default async function UserProfile() {
    const user = await getUser('1'); // Same ID = uses cached result!
    return <div>{user.name}</div>;
}
```

### Memoization in Fetch

Next.js automatically memoizes fetch requests:

```tsx
// These three fetches only make ONE request!
export default async function Page() {
    const data1 = await fetch('https://api.example.com/data');
    const data2 = await fetch('https://api.example.com/data');
    const data3 = await fetch('https://api.example.com/data');

    // All three get the same result from one network call
}
```

**Automatic deduplication happens when:**
- Same URL
- Same options
- Within the same render pass

### Handling Sensitive Data

Keep secrets on the server!

```tsx
// ✅ GOOD: Server Component with secret
export default async function Dashboard() {
    const apiKey = process.env.API_SECRET; // Safe on server!
    const data = await fetch('https://api.example.com/data', {
        headers: {
            'Authorization': `Bearer ${apiKey}`
        }
    });

    return <DashboardUI data={data} />;
}
```

```tsx
// ❌ BAD: Exposing secret to client
'use client';

export default function Dashboard() {
    const apiKey = process.env.API_SECRET; // ❌ undefined!
    // Even if it worked, the bundle would contain your secret!
}
```

**Best practice:** Use Server Actions or API routes to handle sensitive operations:

```tsx
// app/actions.ts
'use server';

export async function fetchPrivateData() {
    const apiKey = process.env.API_SECRET; // Safe!
    const res = await fetch('https://api.example.com/private', {
        headers: { 'Authorization': `Bearer ${apiKey}` }
    });
    return res.json();
}
```

```tsx
// Client Component can call Server Action
'use client';

import { fetchPrivateData } from './actions';

export default function Component() {
    const handleClick = async () => {
        const data = await fetchPrivateData(); // Secure!
        console.log(data);
    };

    return <button onClick={handleClick}>Fetch Data</button>;
}
```

### Revalidation Errors

Handle cache revalidation failures gracefully:

```tsx
'use server';

import { revalidatePath } from 'next/cache';

export async function updatePost(id: string, data: any) {
    try {
        await db.posts.update({ where: { id }, data });

        // Revalidate the cache
        revalidatePath(`/posts/${id}`);
        revalidatePath('/posts');

        return { success: true };
    } catch (error) {
        console.error('Failed to update post:', error);
        return { success: false, error: error.message };
    }
}
```

**On-demand revalidation with tags:**

```tsx
// Tag your fetches
fetch('https://api.example.com/posts', {
    next: { tags: ['posts'] }
});

// Revalidate all fetches with this tag
import { revalidateTag } from 'next/cache';
revalidateTag('posts');
```

### Request Waterfall: The Problem

```tsx
// ❌ BAD: Sequential (slow!)
export default async function Page() {
    const user = await fetch('/api/user');
    const posts = await fetch(`/api/posts?userId=${user.id}`);
    const comments = await fetch(`/api/comments?userId=${user.id}`);

    // Total time: user + posts + comments
}
```

```tsx
// ✅ GOOD: Parallel (fast!)
export default async function Page() {
    const userPromise = fetch('/api/user');
    const postsPromise = fetch('/api/posts');
    const commentsPromise = fetch('/api/comments');

    const [user, posts, comments] = await Promise.all([
        userPromise.then(r => r.json()),
        postsPromise.then(r => r.json()),
        commentsPromise.then(r => r.json())
    ]);

    // Total time: max(user, posts, comments)
}
```

### Brain Power
🧠 Why does React cache() only work during a single request, not across requests?

**Answer:** Each request should be fresh! Caching across requests could show stale data to users. cache() deduplicates within one request to avoid redundant work, but each new page request starts fresh.

### Watch It!
⚠️ **Never store API secrets in client components or NEXT_PUBLIC_ variables!** Use Server Components, Server Actions, or API routes to keep secrets server-side.

### There are NO Dumb Questions

**Q: What's the difference between cache() and fetch caching?**
**A:** fetch caching is for HTTP requests and persists across requests. cache() is for any function and only deduplicates within one request (render pass).

**Q: Should I always parallelize data fetching?**
**A:** Only if requests are independent! If one request needs data from another (waterfall by necessity), keep them sequential.

**Q: How do I debug cache issues?**
**A:** Check the Network tab in DevTools. Next.js adds `x-nextjs-cache` headers showing HIT/MISS/STALE status.

---

## 8. Server Actions: Mutations

### What are Server Actions?

Server Actions are **async functions that run on the server**. They're great for form submissions, mutations, and any server-side operation.

```tsx
// app/actions.ts
'use server';

export async function createPost(formData: FormData) {
    const title = formData.get('title');
    const content = formData.get('content');

    // Server-side code (can access database)
    await db.posts.create({
        data: { title, content }
    });
}
```

### Using Server Actions in Forms

```tsx
// app/new-post/page.tsx
import { createPost } from '../actions';

export default function NewPost() {
    return (
        <form action={createPost}>
            <input name="title" placeholder="Title" required />
            <textarea name="content" placeholder="Content" required />
            <button type="submit">Create Post</button>
        </form>
    );
}
```

**No API route needed!** Form submits directly to server function.

### Server Actions with useTransition

```tsx
'use client';

import { useTransition } from 'react';
import { deletePost } from '../actions';

export default function DeleteButton({ postId }) {
    const [isPending, startTransition] = useTransition();

    return (
        <button
            onClick={() => startTransition(() => deletePost(postId))}
            disabled={isPending}
        >
            {isPending ? 'Deleting...' : 'Delete'}
        </button>
    );
}
```

### Revalidating After Mutations

```tsx
'use server';

import { revalidatePath } from 'next/cache';

export async function createPost(formData: FormData) {
    // Create post in database
    await db.posts.create({
        data: {
            title: formData.get('title'),
            content: formData.get('content')
        }
    });

    // Refresh the posts page
    revalidatePath('/posts');
}
```

### Form Validation in Server Actions

```tsx
'use server';

import { z } from 'zod';
import { redirect } from 'next/navigation';

const postSchema = z.object({
    title: z.string().min(1, 'Title is required').max(100),
    content: z.string().min(10, 'Content must be at least 10 characters'),
    published: z.boolean().optional()
});

export async function createPost(formData: FormData) {
    // Parse and validate
    const rawData = {
        title: formData.get('title'),
        content: formData.get('content'),
        published: formData.get('published') === 'on'
    };

    const result = postSchema.safeParse(rawData);

    if (!result.success) {
        return {
            errors: result.error.flatten().fieldErrors,
            message: 'Validation failed'
        };
    }

    // Create post
    const post = await db.posts.create({
        data: result.data
    });

    revalidatePath('/posts');
    redirect(`/posts/${post.id}`);
}
```

### Using Server Actions with useFormState

```tsx
'use client';

import { useFormState } from 'react-dom';
import { createPost } from './actions';

const initialState = {
    errors: {},
    message: ''
};

export default function CreatePostForm() {
    const [state, formAction] = useFormState(createPost, initialState);

    return (
        <form action={formAction}>
            <div>
                <input name="title" required />
                {state.errors?.title && (
                    <p className="error">{state.errors.title[0]}</p>
                )}
            </div>

            <div>
                <textarea name="content" required />
                {state.errors?.content && (
                    <p className="error">{state.errors.content[0]}</p>
                )}
            </div>

            {state.message && <p>{state.message}</p>}

            <button type="submit">Create Post</button>
        </form>
    );
}
```

### Optimistic Updates

```tsx
'use client';

import { useOptimistic } from 'react';
import { addTodo } from './actions';

export default function TodoList({ todos }) {
    const [optimisticTodos, addOptimisticTodo] = useOptimistic(
        todos,
        (state, newTodo) => [...state, { id: 'temp', text: newTodo, pending: true }]
    );

    async function formAction(formData) {
        const text = formData.get('text');
        addOptimisticTodo(text);
        await addTodo(text);
    }

    return (
        <div>
            <ul>
                {optimisticTodos.map(todo => (
                    <li key={todo.id} style={{ opacity: todo.pending ? 0.5 : 1 }}>
                        {todo.text}
                    </li>
                ))}
            </ul>

            <form action={formAction}>
                <input name="text" required />
                <button type="submit">Add</button>
            </form>
        </div>
    );
}
```

### Server Actions with useFormStatus

```tsx
'use client';

import { useFormStatus } from 'react-dom';

function SubmitButton() {
    const { pending } = useFormStatus();

    return (
        <button type="submit" disabled={pending}>
            {pending ? 'Creating...' : 'Create Post'}
        </button>
    );
}

export default function Form({ action }) {
    return (
        <form action={action}>
            <input name="title" required />
            <textarea name="content" required />
            <SubmitButton />
        </form>
    );
}
```

### Returning Data from Server Actions

```tsx
'use server';

export async function createPost(formData: FormData) {
    try {
        const post = await db.posts.create({
            data: {
                title: formData.get('title'),
                content: formData.get('content')
            }
        });

        revalidatePath('/posts');

        return {
            success: true,
            post: {
                id: post.id,
                title: post.title
            }
        };
    } catch (error) {
        return {
            success: false,
            error: 'Failed to create post'
        };
    }
}
```

```tsx
'use client';

import { createPost } from './actions';

export default function Form() {
    async function handleSubmit(formData: FormData) {
        const result = await createPost(formData);

        if (result.success) {
            alert(`Post created: ${result.post.title}`);
        } else {
            alert(result.error);
        }
    }

    return (
        <form action={handleSubmit}>
            {/* form fields */}
        </form>
    );
}
```

### Progressive Enhancement

Server Actions work without JavaScript!

```tsx
// app/posts/new/page.tsx
import { createPost } from '../actions';

export default function NewPost() {
    return (
        <form action={createPost}>
            <input name="title" required />
            <textarea name="content" required />
            {/* Works even if JavaScript is disabled! */}
            <button type="submit">Create Post</button>
        </form>
    );
}
```

### Brain Power
🧠 What's the advantage of Server Actions over traditional API routes for forms?

**Answer:** Simpler! No need to create API endpoints, handle CORS, or write fetch code. Server Actions work directly in forms, support progressive enhancement (work without JS), and integrate seamlessly with React hooks like useFormStatus and useOptimistic.

### Watch It!
⚠️ **Server Actions can only be used in Server Components or Client Components that import them!** They're marked with `'use server'` directive. Also, always validate input - never trust client data!

---

## 9. Runtimes: Node.js vs Edge

### What are Runtimes?

Runtimes determine WHERE your code runs. Next.js supports two:

1. **Node.js Runtime** (Default) - Full Node.js environment
2. **Edge Runtime** - Lightweight, runs at the edge (closer to users)

### Node.js Runtime (Default)

Full Node.js environment with all APIs:

```tsx
// app/api/data/route.ts
// Default: Node.js runtime

export async function GET() {
    const fs = require('fs'); // ✅ Works! Full Node.js APIs
    const data = fs.readFileSync('./data.json');

    return Response.json({ data });
}
```

**Features:**
- All Node.js APIs (fs, path, crypto, etc.)
- All npm packages work
- Runs on servers
- Slower cold starts
- More memory

### Edge Runtime

Lightweight runtime that runs globally at the edge:

```tsx
// app/api/fast/route.ts
export const runtime = 'edge'; // Opt into Edge

export async function GET() {
    // Only Web APIs available
    const data = await fetch('https://api.example.com/data');

    return Response.json({ data });
}
```

**Features:**
- Only Web APIs (fetch, Response, Request, etc.)
- No Node.js APIs (no fs, path, etc.)
- Runs at edge locations worldwide
- Faster cold starts (instant!)
- Less memory
- Lower latency (closer to users)

### When to Use Each

**Use Node.js Runtime (default) when you need:**
- File system access
- Node.js libraries
- Database connections
- Complex operations
- More memory

**Use Edge Runtime when you need:**
- Fastest response times
- Geo-location based responses
- A/B testing
- Personalization
- Authentication checks
- Simple data fetching

### Setting Runtime Per Route

```tsx
// app/page.tsx
export const runtime = 'nodejs'; // Default, can omit

export default function Page() {
    return <h1>Node.js page</h1>;
}
```

```tsx
// app/fast/page.tsx
export const runtime = 'edge'; // Opt into Edge

export default function FastPage() {
    return <h1>Edge-rendered page</h1>;
}
```

### Edge Runtime Limitations

```tsx
// ❌ These DON'T work in Edge Runtime
export const runtime = 'edge';

export default function Page() {
    const fs = require('fs'); // ❌ Error!
    const path = require('path'); // ❌ Error!

    // Heavy npm packages may not work
    // No native Node.js modules
}
```

```tsx
// ✅ These work in Edge Runtime
export const runtime = 'edge';

export default async function Page() {
    // Web APIs work!
    const data = await fetch('...'); // ✅
    const headers = new Headers(); // ✅
    const url = new URL('https://...'); // ✅

    return <div>{data}</div>;
}
```

### Edge Middleware

Middleware ALWAYS runs on Edge:

```tsx
// middleware.ts (automatically Edge runtime)
import { NextResponse } from 'next/server';

export function middleware(request) {
    // Runs at the edge!
    const country = request.geo?.country || 'US';

    // Redirect based on location
    if (country === 'GB') {
        return NextResponse.redirect(new URL('/uk', request.url));
    }

    return NextResponse.next();
}
```

### Edge API Routes

```tsx
// app/api/personalize/route.ts
export const runtime = 'edge';

export async function GET(request: Request) {
    // Access geo data (Edge only!)
    const { geo } = request;

    return Response.json({
        country: geo?.country,
        city: geo?.city,
        latitude: geo?.latitude,
        longitude: geo?.longitude
    });
}
```

### Dynamic Route Configuration

```tsx
// app/blog/[slug]/page.tsx

// Runtime configuration
export const runtime = 'edge'; // or 'nodejs'

// Other configs work together
export const dynamic = 'force-dynamic';
export const revalidate = 60;

export default function BlogPost({ params }) {
    return <article>Post: {params.slug}</article>;
}
```

### Brain Power
🧠 Why would you choose Edge Runtime over Node.js Runtime if it has fewer features?

**Answer:** Speed and global distribution! Edge Runtime runs in data centers closer to your users worldwide, giving instant response times. For simple tasks (auth checks, redirects, API proxying), the speed wins over extra features.

### Watch It!
⚠️ **Not all npm packages work in Edge Runtime!** Packages using Node.js APIs (fs, crypto, etc.) will fail. Check package compatibility before using Edge Runtime.

### There are NO Dumb Questions

**Q: Can I mix runtimes in the same app?**
**A:** Yes! Each route can have its own runtime. Use Edge for fast pages, Node.js for complex ones.

**Q: Is Edge Runtime like Cloudflare Workers?**
**A:** Similar concept! Edge Runtime is based on Web Standards (like Workers), runs globally at the edge with fast cold starts.

**Q: Does Edge cost more?**
**A:** On Vercel, Edge Functions are included. Check your hosting provider's pricing for edge compute.

---

## 10. Layouts and Templates

### Root Layout: Wraps Everything

```tsx
// app/layout.tsx (required!)
export default function RootLayout({ children }) {
    return (
        <html lang="en">
            <body>
                <nav>
                    <Link href="/">Home</Link>
                    <Link href="/about">About</Link>
                </nav>
                <main>{children}</main>
                <footer>&copy; 2024</footer>
            </body>
        </html>
    );
}
```

**Root layout wraps ALL pages!** Must include `<html>` and `<body>`.

### Nested Layouts

```tsx
// app/dashboard/layout.tsx
export default function DashboardLayout({ children }) {
    return (
        <div className="dashboard">
            <aside>
                <Link href="/dashboard">Overview</Link>
                <Link href="/dashboard/settings">Settings</Link>
            </aside>
            <main>{children}</main>
        </div>
    );
}

// This layout wraps all /dashboard/* pages
```

### Templates: Re-render on Navigation

```tsx
// app/template.tsx
export default function Template({ children }) {
    return <div className="animate-in">{children}</div>;
}
```

**Difference:** Layouts persist, templates re-mount on navigation.

---

## 9. Styling: Writing CSS

### Global CSS

```tsx
// app/globals.css
@tailwind base;
@tailwind components;
@tailwind utilities;

body {
    margin: 0;
    font-family: system-ui;
}

// app/layout.tsx
import './globals.css';

export default function RootLayout({ children }) {
    return <html><body>{children}</body></html>;
}
```

### CSS Modules

```css
/* components/Button.module.css */
.button {
    background: blue;
    color: white;
    padding: 10px 20px;
}

.primary {
    background: green;
}
```

```tsx
// components/Button.tsx
import styles from './Button.module.css';

export default function Button() {
    return <button className={styles.button}>Click me</button>;
}
```

### Tailwind CSS (Most Popular)

```tsx
export default function Card() {
    return (
        <div className="bg-white rounded-lg shadow-md p-6">
            <h2 className="text-2xl font-bold mb-4">Title</h2>
            <p className="text-gray-600">Content here</p>
        </div>
    );
}
```

### Sass/SCSS

```scss
// styles.module.scss
.card {
    background: white;
    padding: 1rem;

    h2 {
        font-size: 2rem;
        margin-bottom: 1rem;
    }
}
```

### CSS-in-JS

**Styled-Components:**
```bash
npm install styled-components
```

```tsx
// app/page.tsx
'use client';

import styled from 'styled-components';

const Button = styled.button`
    background: blue;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;

    &:hover {
        background: darkblue;
    }
`;

export default function Page() {
    return <Button>Click me</Button>;
}
```

**Important:** Add styled-components registry for App Router:

```tsx
// app/lib/registry.tsx
'use client';

import React, { useState } from 'react';
import { useServerInsertedHTML } from 'next/navigation';
import { ServerStyleSheet, StyleSheetManager } from 'styled-components';

export default function StyledComponentsRegistry({
    children,
}: {
    children: React.ReactNode;
}) {
    const [styledComponentsStyleSheet] = useState(() => new ServerStyleSheet());

    useServerInsertedHTML(() => {
        const styles = styledComponentsStyleSheet.getStyleElement();
        styledComponentsStyleSheet.instance.clearTag();
        return <>{styles}</>;
    });

    if (typeof window !== 'undefined') return <>{children}</>;

    return (
        <StyleSheetManager sheet={styledComponentsStyleSheet.instance}>
            {children}
        </StyleSheetManager>
    );
}
```

```tsx
// app/layout.tsx
import StyledComponentsRegistry from './lib/registry';

export default function RootLayout({ children }) {
    return (
        <html>
            <body>
                <StyledComponentsRegistry>
                    {children}
                </StyledComponentsRegistry>
            </body>
        </html>
    );
}
```

**Emotion:**
```bash
npm install @emotion/react @emotion/styled
```

```tsx
'use client';

import styled from '@emotion/styled';
import { css } from '@emotion/react';

const Button = styled.button`
    background: green;
    color: white;
    padding: 10px 20px;
`;

export default function Page() {
    return (
        <div
            css={css`
                display: flex;
                justify-content: center;
            `}
        >
            <Button>Emotion Button</Button>
        </div>
    );
}
```

---

## 16. Testing Your Next.js App

### Unit Testing with Vitest

```bash
npm install -D vitest @vitejs/plugin-react jsdom @testing-library/react @testing-library/jest-dom
```

```ts
// vitest.config.ts
import { defineConfig } from 'vitest/config';
import react from '@vitejs/plugin-react';

export default defineConfig({
    plugins: [react()],
    test: {
        environment: 'jsdom',
    },
});
```

```tsx
// components/Button.test.tsx
import { render, screen } from '@testing-library/react';
import { expect, test } from 'vitest';
import Button from './Button';

test('renders button with text', () => {
    render(<Button>Click me</Button>);
    expect(screen.getByText('Click me')).toBeDefined();
});
```

```json
// package.json
{
    "scripts": {
        "test": "vitest"
    }
}
```

### Unit Testing with Jest

```bash
npm install -D jest jest-environment-jsdom @testing-library/react @testing-library/jest-dom
```

```js
// jest.config.js
const nextJest = require('next/jest');

const createJestConfig = nextJest({
    dir: './', // Path to Next.js app
});

const customJestConfig = {
    setupFilesAfterEnv: ['<rootDir>/jest.setup.js'],
    testEnvironment: 'jest-environment-jsdom',
};

module.exports = createJestConfig(customJestConfig);
```

```js
// jest.setup.js
import '@testing-library/jest-dom';
```

```tsx
// __tests__/page.test.tsx
import { render, screen } from '@testing-library/react';
import Home from '@/app/page';

describe('Home', () => {
    it('renders a heading', () => {
        render(<Home />);

        const heading = screen.getByRole('heading', {
            name: /welcome/i,
        });

        expect(heading).toBeInTheDocument();
    });
});
```

### E2E Testing with Playwright

```bash
npm install -D @playwright/test
npx playwright install
```

```ts
// playwright.config.ts
import { defineConfig, devices } from '@playwright/test';

export default defineConfig({
    testDir: './e2e',
    fullyParallel: true,
    forbidOnly: !!process.env.CI,
    retries: process.env.CI ? 2 : 0,
    workers: process.env.CI ? 1 : undefined,
    use: {
        baseURL: 'http://localhost:3000',
        trace: 'on-first-retry',
    },
    projects: [
        {
            name: 'chromium',
            use: { ...devices['Desktop Chrome'] },
        },
    ],
    webServer: {
        command: 'npm run dev',
        url: 'http://localhost:3000',
        reuseExistingServer: !process.env.CI,
    },
});
```

```ts
// e2e/home.spec.ts
import { test, expect } from '@playwright/test';

test('homepage has title and links to blog', async ({ page }) => {
    await page.goto('/');

    // Check title
    await expect(page).toHaveTitle(/Home/);

    // Click link
    await page.click('text=Blog');

    // Check URL
    await expect(page).toHaveURL('/blog');
});
```

```json
// package.json
{
    "scripts": {
        "test:e2e": "playwright test"
    }
}
```

### E2E Testing with Cypress

```bash
npm install -D cypress
npx cypress open
```

```js
// cypress.config.js
const { defineConfig } = require('cypress');

module.exports = defineConfig({
    e2e: {
        baseUrl: 'http://localhost:3000',
        setupNodeEvents(on, config) {
            // implement node event listeners here
        },
    },
});
```

```js
// cypress/e2e/home.cy.js
describe('Home Page', () => {
    it('should navigate to blog', () => {
        cy.visit('/');

        cy.contains('Blog').click();

        cy.url().should('include', '/blog');

        cy.contains('Blog Posts');
    });
});
```

```json
// package.json
{
    "scripts": {
        "cypress": "cypress open",
        "cypress:headless": "cypress run"
    }
}
```

### Testing Server Components

```tsx
// __tests__/server-component.test.tsx
import { render, screen } from '@testing-library/react';
import Page from '@/app/page';

// Mock fetch for server components
global.fetch = jest.fn(() =>
    Promise.resolve({
        json: () => Promise.resolve({ data: 'test' }),
    })
) as jest.Mock;

describe('Server Component', () => {
    it('fetches and displays data', async () => {
        const Component = await Page(); // Server components return promises
        render(Component);

        expect(screen.getByText(/test/i)).toBeInTheDocument();
    });
});
```

### Testing Server Actions

```tsx
// __tests__/actions.test.ts
import { createPost } from '@/app/actions';

describe('Server Actions', () => {
    it('creates a post', async () => {
        const formData = new FormData();
        formData.append('title', 'Test Post');
        formData.append('content', 'Test Content');

        const result = await createPost(formData);

        expect(result.success).toBe(true);
    });
});
```

### Testing API Routes

```tsx
// __tests__/api.test.ts
import { GET } from '@/app/api/hello/route';

describe('/api/hello', () => {
    it('returns hello message', async () => {
        const response = await GET();
        const data = await response.json();

        expect(data).toEqual({ message: 'Hello!' });
    });
});
```

### Brain Power
🧠 Why would you use both unit tests (Vitest/Jest) AND E2E tests (Playwright)?

**Answer:** Different testing levels! Unit tests verify individual components work (fast, isolated). E2E tests verify the entire app works together as users experience it (slower, but catches integration issues). Use both for comprehensive coverage!

### Watch It!
⚠️ **Don't forget to mock external APIs in tests!** Your tests shouldn't make real API calls. Mock fetch, database calls, and third-party services to keep tests fast and reliable.

### There are NO Dumb Questions

**Q: Which testing framework should I choose?**
**A:** For unit tests: Vitest is faster and modern, Jest is more established. For E2E: Playwright is modern and powerful, Cypress has great DX. Pick based on your team's preference.

**Q: Do I need to test Server Components differently?**
**A:** Yes! Server Components are async and run on the server. Await them in tests and mock server-side APIs (database, file system).

**Q: How much should I test?**
**A:** Focus on business logic and critical paths. Don't test framework features (Next.js routing works). Test: forms, data mutations, authentication, complex logic.

---

## 10. Optimizations: Images, Fonts, Scripts

### Image Optimization

```tsx
import Image from 'next/image';

export default function Profile() {
    return (
        <Image
            src="/profile.jpg"
            alt="Profile picture"
            width={500}
            height={500}
            priority // Load immediately
        />
    );
}
```

**Automatic optimizations:**
- Lazy loading
- Responsive images
- WebP format
- Size optimization

### Font Optimization

```tsx
// app/layout.tsx
import { Inter } from 'next/font/google';

const inter = Inter({ subsets: ['latin'] });

export default function RootLayout({ children }) {
    return (
        <html className={inter.className}>
            <body>{children}</body>
        </html>
    );
}
```

### Scripts: Third-Party JavaScript

Optimize third-party scripts with next/script:

```tsx
import Script from 'next/script';

export default function Page() {
    return (
        <>
            {/* Load after page is interactive */}
            <Script src="https://example.com/script.js" />

            {/* Strategies */}
            <Script
                src="https://www.google-analytics.com/analytics.js"
                strategy="afterInteractive" // Default: loads after page is interactive
            />

            <Script
                src="https://connect.facebook.net/en_US/sdk.js"
                strategy="lazyOnload" // Loads during idle time
            />

            <Script
                src="https://cdn.example.com/critical.js"
                strategy="beforeInteractive" // Loads before page is interactive (use sparingly!)
            />

            {/* Inline scripts */}
            <Script id="show-banner">
                {`console.log('Hello from inline script!')`}
            </Script>

            {/* With callbacks */}
            <Script
                src="https://example.com/script.js"
                onLoad={() => {
                    console.log('Script loaded!');
                }}
                onError={(e) => {
                    console.error('Script failed to load', e);
                }}
            />
        </>
    );
}
```

### Videos: Optimization

Optimize video delivery:

```tsx
// app/page.tsx
export default function Page() {
    return (
        <video
            width="750"
            height="500"
            controls
            preload="none" // Don't preload until user clicks play
            poster="/thumbnail.jpg" // Show thumbnail
        >
            <source src="/video.webm" type="video/webm" />
            <source src="/video.mp4" type="video/mp4" />
            Your browser does not support the video tag.
        </video>
    );
}
```

**Best practices:**
- Use `preload="none"` or `preload="metadata"` to save bandwidth
- Provide multiple formats (WebM, MP4)
- Use poster images
- Consider streaming services (YouTube, Vimeo) for large files
- Use CDN for video hosting

### Lazy Loading: Code Splitting

Load components only when needed:

```tsx
// Dynamic imports
import dynamic from 'next/dynamic';

// Lazy load component
const HeavyComponent = dynamic(() => import('@/components/HeavyComponent'), {
    loading: () => <p>Loading...</p>,
    ssr: false // Don't render on server
});

export default function Page() {
    return (
        <div>
            <h1>My Page</h1>
            <HeavyComponent />
        </div>
    );
}
```

**Conditional loading:**
```tsx
'use client';

import { useState } from 'react';
import dynamic from 'next/dynamic';

const Chart = dynamic(() => import('@/components/Chart'), {
    ssr: false
});

export default function Dashboard() {
    const [showChart, setShowChart] = useState(false);

    return (
        <div>
            <button onClick={() => setShowChart(true)}>
                Show Chart
            </button>
            {showChart && <Chart />}
        </div>
    );
}
```

**Named exports:**
```tsx
// components/Charts.tsx
export const BarChart = () => <div>Bar Chart</div>;
export const LineChart = () => <div>Line Chart</div>;

// app/page.tsx
import dynamic from 'next/dynamic';

const BarChart = dynamic(() =>
    import('@/components/Charts').then((mod) => mod.BarChart)
);
```

### Analytics: Tracking

Add analytics to your Next.js app:

**Vercel Analytics:**
```bash
npm install @vercel/analytics
```

```tsx
// app/layout.tsx
import { Analytics } from '@vercel/analytics/react';

export default function RootLayout({ children }) {
    return (
        <html>
            <body>
                {children}
                <Analytics />
            </body>
        </html>
    );
}
```

**Google Analytics (gtag):**
```tsx
// app/layout.tsx
import Script from 'next/script';

export default function RootLayout({ children }) {
    return (
        <html>
            <body>
                {children}
                <Script
                    src={`https://www.googletagmanager.com/gtag/js?id=${process.env.NEXT_PUBLIC_GA_ID}`}
                    strategy="afterInteractive"
                />
                <Script id="google-analytics" strategy="afterInteractive">
                    {`
                        window.dataLayer = window.dataLayer || [];
                        function gtag(){dataLayer.push(arguments);}
                        gtag('js', new Date());
                        gtag('config', '${process.env.NEXT_PUBLIC_GA_ID}');
                    `}
                </Script>
            </body>
        </html>
    );
}
```

**Custom events:**
```tsx
'use client';

export default function Button() {
    const handleClick = () => {
        // Track custom event
        if (window.gtag) {
            window.gtag('event', 'button_click', {
                button_name: 'cta_button'
            });
        }
    };

    return <button onClick={handleClick}>Click me</button>;
}
```

### Third Party Libraries

Optimize third-party library loading:

**Use next/third-parties:**
```bash
npm install @next/third-parties
```

```tsx
// app/layout.tsx
import { GoogleAnalytics } from '@next/third-parties/google';

export default function RootLayout({ children }) {
    return (
        <html>
            <body>
                {children}
                <GoogleAnalytics gaId="G-XXXXXXXXXX" />
            </body>
        </html>
    );
}
```

**Google Maps:**
```tsx
import { GoogleMapsEmbed } from '@next/third-parties/google';

export default function Page() {
    return (
        <GoogleMapsEmbed
            apiKey="YOUR_API_KEY"
            height={400}
            width="100%"
            mode="place"
            q="Brooklyn+Bridge,New+York,NY"
        />
    );
}
```

### Package Bundling

Optimize your bundle size:

**Analyze bundle:**
```bash
npm install @next/bundle-analyzer
```

```js
// next.config.js
const withBundleAnalyzer = require('@next/bundle-analyzer')({
    enabled: process.env.ANALYZE === 'true'
});

module.exports = withBundleAnalyzer({
    // Your Next.js config
});
```

```bash
ANALYZE=true npm run build
```

**Tree shaking:**
```tsx
// ✅ GOOD: Import only what you need
import { useState } from 'react';
import { format } from 'date-fns/format';

// ❌ BAD: Imports entire library
import _ from 'lodash';
import * as dateFns from 'date-fns';
```

### Metadata (SEO)

```tsx
// app/page.tsx
export const metadata = {
    title: 'Home | My Site',
    description: 'Welcome to my amazing site',
};

export default function Home() {
    return <h1>Home</h1>;
}
```

**Dynamic metadata:**
```tsx
// app/blog/[slug]/page.tsx
export async function generateMetadata({ params }) {
    const post = await getPost(params.slug);

    return {
        title: post.title,
        description: post.excerpt,
        openGraph: {
            title: post.title,
            description: post.excerpt,
            images: [post.image],
        },
        twitter: {
            card: 'summary_large_image',
            title: post.title,
            description: post.excerpt,
            images: [post.image],
        }
    };
}
```

**All metadata options:**
```tsx
export const metadata = {
    title: 'My Page',
    description: 'Page description',
    keywords: ['nextjs', 'react', 'javascript'],
    authors: [{ name: 'John Doe' }],
    creator: 'John Doe',
    publisher: 'My Company',
    formatDetection: {
        email: false,
        address: false,
        telephone: false,
    },
    openGraph: {
        title: 'My Page',
        description: 'Page description',
        url: 'https://example.com',
        siteName: 'My Site',
        images: [
            {
                url: 'https://example.com/og.jpg',
                width: 1200,
                height: 630,
            },
        ],
        locale: 'en_US',
        type: 'website',
    },
    robots: {
        index: true,
        follow: true,
        googleBot: {
            index: true,
            follow: true,
            'max-video-preview': -1,
            'max-image-preview': 'large',
            'max-snippet': -1,
        },
    },
    icons: {
        icon: '/favicon.ico',
        shortcut: '/shortcut-icon.png',
        apple: '/apple-icon.png',
    },
    manifest: '/manifest.json',
};
```

### Memory Usage

Monitor and optimize memory:

**Monitoring:**
```tsx
// app/api/memory/route.ts
export async function GET() {
    const used = process.memoryUsage();

    return Response.json({
        rss: `${Math.round(used.rss / 1024 / 1024)} MB`,
        heapTotal: `${Math.round(used.heapTotal / 1024 / 1024)} MB`,
        heapUsed: `${Math.round(used.heapUsed / 1024 / 1024)} MB`,
        external: `${Math.round(used.external / 1024 / 1024)} MB`,
    });
}
```

**Best practices:**
- Avoid large in-memory caches
- Use streaming for large data
- Clean up event listeners
- Use pagination for large lists
- Implement proper garbage collection

### Brain Power
🧠 Why would you lazy load a component instead of importing it normally?

**Answer:** Reduce initial bundle size! Heavy components (charts, editors, maps) make your first page load slow. Lazy loading splits them into separate chunks that only load when needed, making the initial page fast.

### Watch It!
⚠️ **Don't lazy load everything!** Only lazy load heavy components that aren't immediately needed. Lazy loading adds complexity and a small delay. Use it strategically for components like modals, charts, or below-the-fold content.

---

## 11. API Routes: Building APIs

### Creating API Routes

```tsx
// app/api/hello/route.ts
export async function GET() {
    return Response.json({ message: 'Hello!' });
}

export async function POST(request: Request) {
    const data = await request.json();
    return Response.json({ received: data });
}

export async function PATCH(request: Request) {
    const data = await request.json();
    // Update logic
    return Response.json({ updated: true });
}

export async function DELETE(request: Request) {
    // Delete logic
    return Response.json({ deleted: true });
}
```

Visit `/api/hello` → JSON response

### Dynamic API Routes

```tsx
// app/api/posts/[id]/route.ts
export async function GET(
    request: Request,
    { params }: { params: { id: string } }
) {
    const post = await db.posts.findUnique({
        where: { id: params.id }
    });

    if (!post) {
        return Response.json(
            { error: 'Post not found' },
            { status: 404 }
        );
    }

    return Response.json(post);
}

export async function PATCH(
    request: Request,
    { params }: { params: { id: string } }
) {
    const body = await request.json();

    const updated = await db.posts.update({
        where: { id: params.id },
        data: body
    });

    return Response.json(updated);
}

export async function DELETE(
    request: Request,
    { params }: { params: { id: string } }
) {
    await db.posts.delete({
        where: { id: params.id }
    });

    return Response.json({ success: true });
}
```

### Reading Request Data

```tsx
// app/api/posts/route.ts
export async function POST(request: Request) {
    // JSON body
    const body = await request.json();

    // Query parameters
    const { searchParams } = new URL(request.url);
    const page = searchParams.get('page');

    // Headers
    const auth = request.headers.get('authorization');

    // Cookies
    const { cookies } = request;
    const token = cookies.get('token');

    return Response.json({
        body,
        page,
        hasAuth: !!auth,
        hasToken: !!token
    });
}
```

### Setting Response Headers

```tsx
// app/api/data/route.ts
export async function GET() {
    return Response.json(
        { data: 'value' },
        {
            status: 200,
            headers: {
                'Content-Type': 'application/json',
                'Cache-Control': 'public, max-age=3600',
                'X-Custom-Header': 'value'
            }
        }
    );
}
```

### Error Handling

```tsx
// app/api/posts/route.ts
export async function POST(request: Request) {
    try {
        const body = await request.json();

        // Validation
        if (!body.title) {
            return Response.json(
                { error: 'Title is required' },
                { status: 400 }
            );
        }

        const post = await db.posts.create({ data: body });

        return Response.json(post, { status: 201 });
    } catch (error) {
        console.error('API Error:', error);
        return Response.json(
            { error: 'Internal server error' },
            { status: 500 }
        );
    }
}
```

### CORS Headers

```tsx
// app/api/public/route.ts
export async function GET(request: Request) {
    return Response.json(
        { data: 'public' },
        {
            headers: {
                'Access-Control-Allow-Origin': '*',
                'Access-Control-Allow-Methods': 'GET, POST, PUT, DELETE, OPTIONS',
                'Access-Control-Allow-Headers': 'Content-Type, Authorization',
            },
        }
    );
}

export async function OPTIONS(request: Request) {
    return new Response(null, {
        status: 200,
        headers: {
            'Access-Control-Allow-Origin': '*',
            'Access-Control-Allow-Methods': 'GET, POST, PUT, DELETE, OPTIONS',
            'Access-Control-Allow-Headers': 'Content-Type, Authorization',
        },
    });
}
```

### Streaming Responses

```tsx
// app/api/stream/route.ts
export async function GET() {
    const encoder = new TextEncoder();

    const stream = new ReadableStream({
        async start(controller) {
            for (let i = 0; i < 5; i++) {
                controller.enqueue(encoder.encode(`data: ${i}\n\n`));
                await new Promise(resolve => setTimeout(resolve, 1000));
            }
            controller.close();
        }
    });

    return new Response(stream, {
        headers: {
            'Content-Type': 'text/event-stream',
            'Cache-Control': 'no-cache',
            'Connection': 'keep-alive'
        }
    });
}
```

### Brain Power
🧠 When should you use API Routes vs Server Actions?

**Answer:** Use Server Actions for form submissions and mutations (simpler, no API endpoint needed). Use API Routes when you need a public API, webhooks, or need to be called from external services. Server Actions are React-specific, API Routes are universal.

### Watch It!
⚠️ **API Routes run on the server!** You can access databases, file system, and secrets. But make sure to validate all input and handle errors properly.

---

## 12. Middleware: Request Processing

### Global Middleware

Middleware runs BEFORE requests are processed. Perfect for auth, redirects, and more!

```tsx
// middleware.ts (root)
import { NextResponse } from 'next/server';

export function middleware(request) {
    // Redirect if not authenticated
    if (!request.cookies.get('token')) {
        return NextResponse.redirect(new URL('/login', request.url));
    }

    return NextResponse.next();
}

export const config = {
    matcher: '/dashboard/:path*' // Apply to /dashboard/*
};
```

### Setting Headers

Add custom headers to responses:

```tsx
// middleware.ts
import { NextResponse } from 'next/server';

export function middleware(request) {
    // Clone the response
    const response = NextResponse.next();

    // Add custom headers
    response.headers.set('x-custom-header', 'my-value');
    response.headers.set('x-request-id', crypto.randomUUID());

    // Security headers
    response.headers.set('X-Frame-Options', 'DENY');
    response.headers.set('X-Content-Type-Options', 'nosniff');
    response.headers.set('Referrer-Policy', 'origin-when-cross-origin');

    return response;
}
```

### Using Cookies

Read and set cookies in middleware:

```tsx
// middleware.ts
import { NextRequest, NextResponse } from 'next/server';

export function middleware(request: NextRequest) {
    // Read cookies
    const token = request.cookies.get('token');
    const theme = request.cookies.get('theme');

    console.log('Token:', token?.value);

    const response = NextResponse.next();

    // Set cookies
    response.cookies.set('visited', 'true', {
        maxAge: 60 * 60 * 24 * 365, // 1 year
        httpOnly: true,
        secure: process.env.NODE_ENV === 'production',
        sameSite: 'lax'
    });

    // Delete cookies
    response.cookies.delete('old-cookie');

    return response;
}
```

### Conditional Redirects

```tsx
// middleware.ts
import { NextResponse } from 'next/server';

export function middleware(request) {
    const { pathname } = request.nextUrl;

    // Redirect old URLs
    if (pathname.startsWith('/old-blog')) {
        return NextResponse.redirect(
            new URL(pathname.replace('/old-blog', '/blog'), request.url)
        );
    }

    // Redirect based on auth
    const isAuthenticated = request.cookies.get('session');

    if (pathname.startsWith('/dashboard') && !isAuthenticated) {
        return NextResponse.redirect(new URL('/login', request.url));
    }

    if (pathname === '/login' && isAuthenticated) {
        return NextResponse.redirect(new URL('/dashboard', request.url));
    }

    return NextResponse.next();
}

export const config = {
    matcher: ['/dashboard/:path*', '/login', '/old-blog/:path*']
};
```

### Rewriting URLs

Serve different content without changing the URL:

```tsx
// middleware.ts
import { NextResponse } from 'next/server';

export function middleware(request) {
    const { pathname } = request.nextUrl;

    // Show /maintenance page for all routes during maintenance
    if (process.env.MAINTENANCE_MODE === 'true') {
        return NextResponse.rewrite(new URL('/maintenance', request.url));
    }

    // A/B testing
    const bucket = request.cookies.get('ab-test')?.value || 'A';

    if (pathname === '/') {
        if (bucket === 'B') {
            return NextResponse.rewrite(new URL('/home-variant-b', request.url));
        }
    }

    return NextResponse.next();
}
```

### Modifying Request Headers

Add headers to the request before it reaches your app:

```tsx
// middleware.ts
import { NextResponse } from 'next/server';

export function middleware(request) {
    // Clone request with modified headers
    const requestHeaders = new Headers(request.headers);
    requestHeaders.set('x-user-ip', request.ip || 'unknown');
    requestHeaders.set('x-pathname', request.nextUrl.pathname);

    // Pass modified headers to the page
    return NextResponse.next({
        request: {
            headers: requestHeaders
        }
    });
}
```

Then access in your page:

```tsx
// app/page.tsx
import { headers } from 'next/headers';

export default function Page() {
    const headersList = headers();
    const userIp = headersList.get('x-user-ip');
    const pathname = headersList.get('x-pathname');

    return (
        <div>
            <p>Your IP: {userIp}</p>
            <p>Path: {pathname}</p>
        </div>
    );
}
```

### Matcher Patterns

Control which routes run middleware:

```tsx
// middleware.ts
export const config = {
    // Single path
    matcher: '/dashboard',

    // Multiple paths
    matcher: ['/dashboard', '/admin', '/profile'],

    // Wildcards
    matcher: '/dashboard/:path*', // All /dashboard routes

    // Regex
    matcher: [
        '/((?!api|_next/static|_next/image|favicon.ico).*)', // Everything except these
    ],

    // Multiple patterns
    matcher: [
        '/dashboard/:path*',
        '/api/:path*',
        '/((?!_next/static|_next/image|favicon.ico).*)'
    ]
};
```

### Brain Power
🧠 Why does middleware run on the Edge Runtime instead of Node.js?

**Answer:** Speed! Middleware needs to run for EVERY request before the page loads. Edge Runtime starts instantly and runs globally, adding minimal latency. Node.js cold starts would slow down every request.

### Watch It!
⚠️ **Middleware runs on EVERY matched request!** Keep it fast. Avoid heavy operations, database calls, or complex logic. Use it for quick checks and redirects only.

### There are NO Dumb Questions

**Q: Can I access environment variables in middleware?**
**A:** Yes! But only NEXT_PUBLIC_ variables and server-side variables. Database credentials work, but be careful with timing.

**Q: Can I fetch data in middleware?**
**A:** Yes, but keep it fast! Middleware adds latency to every request. Only fetch if absolutely necessary (like checking a session with an external service).

**Q: What's the difference between redirect and rewrite?**
**A:** redirect() changes the URL (user sees new URL). rewrite() keeps the same URL but serves different content (internal routing).

---

## 13. Caching: Performance

### Automatic Caching

```tsx
// Cached for 1 hour
fetch('https://api.example.com/data', {
    next: { revalidate: 3600 }
});

// Never cache
fetch('https://api.example.com/data', {
    cache: 'no-store'
});
```

### Revalidating Cache

```tsx
import { revalidatePath, revalidateTag } from 'next/cache';

// Revalidate specific path
revalidatePath('/posts');

// Revalidate by tag
revalidateTag('posts');
```

---

## 14. Configuration: Setting Up Your App

### Environment Variables

Store secrets and config safely!

```bash
# .env.local (never commit this!)
DATABASE_URL=postgresql://localhost/mydb
API_SECRET=your-secret-key

# .env (can commit this - defaults)
NEXT_PUBLIC_API_URL=https://api.example.com
```

**Important prefix:** `NEXT_PUBLIC_` exposes variables to the browser!

```tsx
// Server Component - Access any env var
export default async function Page() {
    const secret = process.env.API_SECRET; // ✅ Server only
    const publicUrl = process.env.NEXT_PUBLIC_API_URL; // ✅ Works

    return <div>Connected to API</div>;
}
```

```tsx
// Client Component - Only NEXT_PUBLIC_*
'use client';

export default function Component() {
    const url = process.env.NEXT_PUBLIC_API_URL; // ✅ Works
    const secret = process.env.API_SECRET; // ❌ undefined!

    return <div>API URL: {url}</div>;
}
```

**Environment files priority:**
```
.env.local          # Loaded first (all environments)
.env.production     # Production only
.env.development    # Development only
.env                # Defaults
```

### Watch It!
⚠️ **NEVER put secrets in NEXT_PUBLIC_ variables!** They're exposed to the browser. API keys, database credentials, and secrets should NEVER have the NEXT_PUBLIC_ prefix.

### TypeScript Configuration

```json
// tsconfig.json
{
  "compilerOptions": {
    "target": "ES2017",
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": true,
    "skipLibCheck": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "noEmit": true,
    "esModuleInterop": true,
    "module": "esnext",
    "moduleResolution": "bundler",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve",
    "incremental": true,
    "plugins": [
      {
        "name": "next"
      }
    ],
    "paths": {
      "@/*": ["./*"]
    }
  },
  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx", ".next/types/**/*.ts"],
  "exclude": ["node_modules"]
}
```

**Type-safe routes:**
```tsx
import { Route } from 'next';
import Link from 'next/link';

// TypeScript knows valid routes!
<Link<Route> href="/blog/hello" /> // ✅
<Link<Route> href="/invalid-route" /> // ❌ Error
```

### Internationalization (i18n)

Support multiple languages!

```tsx
// app/[lang]/page.tsx
const dictionaries = {
    en: () => import('./dictionaries/en.json').then((module) => module.default),
    es: () => import('./dictionaries/es.json').then((module) => module.default),
};

export default async function Page({ params: { lang } }) {
    const dict = await dictionaries[lang]();

    return (
        <div>
            <h1>{dict.welcome}</h1>
            <p>{dict.description}</p>
        </div>
    );
}
```

```json
// dictionaries/en.json
{
    "welcome": "Welcome",
    "description": "This is my website"
}
```

```json
// dictionaries/es.json
{
    "welcome": "Bienvenido",
    "description": "Este es mi sitio web"
}
```

**Language detection middleware:**
```tsx
// middleware.ts
import { NextResponse } from 'next/server';

const locales = ['en', 'es', 'fr'];
const defaultLocale = 'en';

export function middleware(request) {
    // Check if locale is in pathname
    const pathname = request.nextUrl.pathname;
    const pathnameHasLocale = locales.some(
        (locale) => pathname.startsWith(`/${locale}/`) || pathname === `/${locale}`
    );

    if (pathnameHasLocale) return;

    // Redirect to locale
    const locale = defaultLocale;
    request.nextUrl.pathname = `/${locale}${pathname}`;
    return NextResponse.redirect(request.nextUrl);
}

export const config = {
    matcher: ['/((?!_next|api|favicon.ico).*)'],
};
```

### Markdown and MDX

Write content-driven pages with MDX!

```bash
npm install @next/mdx @mdx-js/loader @mdx-js/react
```

```js
// next.config.js
const withMDX = require('@next/mdx')({
    extension: /\.mdx?$/,
});

module.exports = withMDX({
    pageExtensions: ['js', 'jsx', 'ts', 'tsx', 'md', 'mdx'],
});
```

```mdx
// app/blog/hello-world.mdx
---
title: "Hello World"
date: "2024-01-01"
---

# Hello World

This is my first **MDX** post!

<CustomComponent />

export const metadata = {
    title: 'Hello World - My Blog'
}
```

**MDX Components:**
```tsx
// mdx-components.tsx
export function useMDXComponents(components) {
    return {
        h1: ({ children }) => <h1 className="text-4xl font-bold">{children}</h1>,
        code: ({ children }) => <code className="bg-gray-100">{children}</code>,
        ...components,
    };
}
```

### Custom Server (Advanced)

Run Next.js with a custom Node.js server:

```js
// server.js
const { createServer } = require('http');
const { parse } = require('url');
const next = require('next');

const dev = process.env.NODE_ENV !== 'production';
const app = next({ dev });
const handle = app.getRequestHandler();

app.prepare().then(() => {
    createServer((req, res) => {
        const parsedUrl = parse(req.url, true);

        // Custom route handling
        if (parsedUrl.pathname === '/custom') {
            res.writeHead(200);
            res.end('Custom route!');
            return;
        }

        // Let Next.js handle everything else
        handle(req, res, parsedUrl);
    }).listen(3000, (err) => {
        if (err) throw err;
        console.log('> Ready on http://localhost:3000');
    });
});
```

```json
// package.json
{
    "scripts": {
        "dev": "node server.js",
        "build": "next build",
        "start": "NODE_ENV=production node server.js"
    }
}
```

### Brain Power
🧠 Why would you need a custom server if Next.js already handles routing?

**Answer:** Custom servers let you add WebSocket support, custom middleware, integration with existing Node.js apps, or special authentication flows. Most apps don't need this!

### There are NO Dumb Questions

**Q: Should I use .env.local or .env for secrets?**
**A:** Use .env.local! It's automatically ignored by Git. .env is for defaults you CAN commit (like API URLs, not secrets).

**Q: Can I use libraries like react-i18next for i18n?**
**A:** Yes! Next.js doesn't force a specific i18n solution. The example shown is simple. Use libraries for complex translations.

**Q: When should I use MDX vs a CMS?**
**A:** MDX is great for developer blogs and documentation (content in your repo). CMSs are better for non-technical editors and larger content teams.

---

## 15. Deployment: Going Live

### Deploy to Vercel (Easiest)

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel
```

**Automatic:**
- HTTPS
- CDN
- Serverless functions
- Preview deployments

### Build for Production

```bash
npm run build
npm run start
```

### Docker Container

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build
EXPOSE 3000
CMD ["npm", "start"]
```

### Static Export

```js
// next.config.js
module.exports = {
    output: 'export'
};
```

```bash
npm run build
# Generates static HTML in out/
```

---

## Congratulations!

You've learned Next.js fundamentals! But there's so much more.

### What's next?

1. **Build projects** - Blog, e-commerce, dashboard
2. **Learn TypeScript** - Type-safe Next.js
3. **Master data fetching** - Server Actions, caching
4. **Authentication** - NextAuth.js, Auth0
5. **Database** - Prisma, Drizzle
6. **Testing** - Playwright, Vitest
7. **Advanced patterns** - Parallel routes, intercepting routes

### Additional Resources

- **Next.js Docs:** https://nextjs.org/docs
- **Learn Next.js:** https://nextjs.org/learn
- **Frontend Roadmap:** https://roadmap.sh/frontend
- **React Roadmap:** https://roadmap.sh/react
- **Vercel:** https://vercel.com

---

## Quick Reference Card

**Create App:**
```bash
npx create-next-app@latest
npm run dev  # Start development server
```

**Routing:**
```
app/page.tsx                     → /
app/about/page.tsx               → /about
app/blog/[slug]/page.tsx         → /blog/:slug
app/docs/[...slug]/page.tsx      → /docs/any/path
app/(marketing)/about/page.tsx   → /about (route group)
```

**Advanced Routing:**
```tsx
// Parallel Routes
app/dashboard/@analytics/page.tsx

// Intercepting Routes
app/feed/(..)photo/[id]/page.tsx

// Redirects
import { redirect } from 'next/navigation';
redirect('/login');

// Static vs Dynamic
export const dynamic = 'force-dynamic';
export const revalidate = 3600;
```

**Server Component:**
```tsx
// Default: async, server-side
export default async function Page() {
    const data = await fetch('https://...');
    return <div>{data}</div>;
}
```

**Client Component:**
```tsx
'use client';
import { useState } from 'react';

export default function Counter() {
    const [count, setCount] = useState(0);
    return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

**Data Fetching:**
```tsx
// With caching
fetch('https://...', {
    next: { revalidate: 3600 }
});

// Without caching
fetch('https://...', {
    cache: 'no-store'
});

// React cache
import { cache } from 'react';
const getData = cache(async (id) => {
    return await fetch(`https://.../${id}`);
});
```

**Server Actions:**
```tsx
// app/actions.ts
'use server';

export async function createPost(formData: FormData) {
    const title = formData.get('title');
    await db.posts.create({ data: { title } });
    revalidatePath('/posts');
}

// app/page.tsx
<form action={createPost}>
    <input name="title" />
    <button type="submit">Create</button>
</form>
```

**Navigation:**
```tsx
import Link from 'next/link';
<Link href="/about">About</Link>

// Programmatic
import { useRouter } from 'next/navigation';
const router = useRouter();
router.push('/dashboard');
```

**Image:**
```tsx
import Image from 'next/image';
<Image
    src="/pic.jpg"
    width={500}
    height={500}
    alt="..."
    priority
/>
```

**Metadata:**
```tsx
// Static
export const metadata = {
    title: 'Page Title',
    description: 'Page description',
    openGraph: {
        title: 'Page Title',
        images: ['/og-image.jpg'],
    }
};

// Dynamic
export async function generateMetadata({ params }) {
    const post = await getPost(params.id);
    return { title: post.title };
}
```

**API Routes:**
```tsx
// app/api/posts/route.ts
export async function GET(request: Request) {
    return Response.json({ posts: [] });
}

export async function POST(request: Request) {
    const body = await request.json();
    return Response.json({ created: true }, { status: 201 });
}

// app/api/posts/[id]/route.ts
export async function GET(req, { params }) {
    return Response.json({ id: params.id });
}
```

**Middleware:**
```tsx
// middleware.ts
import { NextResponse } from 'next/server';

export function middleware(request) {
    // Auth check
    if (!request.cookies.get('token')) {
        return NextResponse.redirect(new URL('/login', request.url));
    }

    // Add headers
    const response = NextResponse.next();
    response.headers.set('x-custom', 'value');
    return response;
}

export const config = {
    matcher: '/dashboard/:path*'
};
```

**Environment Variables:**
```bash
# .env.local
DATABASE_URL=...           # Server only
NEXT_PUBLIC_API_URL=...    # Available in browser
```

**Runtimes:**
```tsx
export const runtime = 'edge';  // or 'nodejs' (default)
```

**Loading & Error States:**
```tsx
// app/loading.tsx - Auto-shown while loading
export default function Loading() {
    return <div>Loading...</div>;
}

// app/error.tsx - Auto-shown on error
'use client';
export default function Error({ error, reset }) {
    return <div>Error: {error.message}</div>;
}
```

**Lazy Loading:**
```tsx
import dynamic from 'next/dynamic';

const Chart = dynamic(() => import('./Chart'), {
    loading: () => <p>Loading...</p>,
    ssr: false
});
```

**Testing:**
```bash
# Vitest
npm run test

# Playwright
npx playwright test

# Cypress
npx cypress run
```

---

**Created in the style of Head First books**

*Now go build the next big thing with Next.js!* 🚀