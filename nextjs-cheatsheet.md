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

### Part I: Fundamentals
1. [Introduction: Why Next.js?](#1-introduction-why-nextjs)
2. [Getting Started: Your First App](#2-getting-started-your-first-app)
3. [Routing: File-Based Routes](#3-routing-file-based-routes)
4. [App Router vs Pages Router](#4-app-router-vs-pages-router)
5. [Advanced Routing Patterns](#5-advanced-routing-patterns)

### Part II: Rendering & Data
6. [Rendering: Server and Client](#6-rendering-server-and-client)
7. [Data Fetching: Getting Data](#7-data-fetching-getting-data)
8. [Advanced Data Fetching](#8-advanced-data-fetching)
9. [Server Actions: Mutations](#9-server-actions-mutations)

### Part III: Architecture
10. [Runtimes: Node.js vs Edge](#10-runtimes-nodejs-vs-edge)
11. [Layouts and Templates](#11-layouts-and-templates)
12. [Styling: Writing CSS](#12-styling-writing-css)
13. [Testing Your Next.js App](#13-testing-your-nextjs-app)
14. [Optimizations: Images, Fonts, Scripts](#14-optimizations-images-fonts-scripts)

### Part IV: APIs & Middleware
15. [API Routes: Building APIs](#15-api-routes-building-apis)
16. [Middleware: Request Processing](#16-middleware-request-processing)
17. [Caching: Performance](#17-caching-performance)
18. [Configuration: Setting Up Your App](#18-configuration-setting-up-your-app)

### Part V: Production
19. [Authentication: Protecting Your App](#19-authentication-protecting-your-app)
20. [Navigation Hooks](#20-navigation-hooks-useparams-usepathname-usesearchparams)
21. [Special Files: File Conventions](#21-special-files-file-conventions)
22. [Security Best Practices](#22-security-best-practices)
23. [Turbopack: The New Bundler](#23-turbopack-the-new-bundler)
24. [Partial Prerendering (PPR)](#24-partial-prerendering-ppr)
25. [Deployment: Going Live](#25-deployment-going-live)

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
import Link from 'next/link';

export default function LandingPage() {
    return (
        <main className="flex flex-col items-center justify-center min-h-screen">
            <h1 className="text-5xl font-bold">Build Your Dream SaaS</h1>
            <p className="mt-4 text-xl">The best platform for managing your business.</p>
            <div className="mt-8 flex gap-4">
                <Link href="/signup" className="bg-blue-600 text-white px-6 py-3 rounded">
                    Get Started
                </Link>
                <Link href="/demo" className="border border-gray-300 px-6 py-3 rounded">
                    View Demo
                </Link>
            </div>
        </main>
    );
}
```

That's it! File in `app/page.tsx` = route at `/`

### Adding Another Page

```tsx
// app/pricing/page.tsx
export default function Pricing() {
    return (
        <main>
            <h1>Pricing Plans</h1>
            <div className="grid grid-cols-3 gap-4">
                {/* Pricing cards... */}
            </div>
        </main>
    );
}
```

File in `app/pricing/page.tsx` = route at `/pricing`

### Brain Power
🧠 How does Next.js know what route a page should be? What's the pattern?

**Answer:** The folder structure IS the routing! `app/about/page.tsx` → `/about`. `app/blog/post/page.tsx` → `/blog/post`. No configuration needed!

### Watch It!
⚠️ **File must be named `page.tsx` (or `page.jsx`)!** Other filenames won't create routes. `about.tsx` won't work, `about/page.tsx` will.

### There are NO Dumb Questions

**Q: Do I need to restart the server when I add a new page?**
**A:** No! Next.js detects new files automatically in development mode. Just create the file and navigate to the route.

**Q: What's the difference between `app/` and `src/app/`?**
**A:** Both work! `src/app/` keeps your project root cleaner by putting all source code in `src/`. Next.js supports both conventions.

**Q: Can I use JavaScript instead of TypeScript?**
**A:** Yes! Use `.jsx` instead of `.tsx`. But TypeScript is strongly recommended for the better developer experience and error catching.

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
// app/shop/[sku]/page.tsx
export default function ProductPage({ params }: { params: { sku: string } }) {
    return (
        <article>
            <h1>Product SKU: {params.sku}</h1>
            <p>Details for product {params.sku}...</p>
            <AddToCart sku={params.sku} />
        </article>
    );
}
```

Visiting `/shop/123-abc` → `params.sku = '123-abc'`

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

### Brain Power
🧠 How does file-based routing compare to React Router? What are the trade-offs?

**Answer:** File-based routing means the file structure IS the URL structure. Pros: no route config files, easier to understand, automatic code splitting. Cons: less flexible than programmatic routing, folder structure must match URL design.

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

### There are NO Dumb Questions

**Q: Can I use both routers in the same app?**
**A:** Yes! Pages in `/pages` use Pages Router, pages in `/app` use App Router. They can coexist during migration. Just don't have the same route in both.

**Q: Should I migrate my existing Pages Router app?**
**A:** Only if you need App Router features (Server Components, streaming, parallel routes). Pages Router is stable and will be maintained. Migrate incrementally, route by route.

**Q: Do I lose anything by using App Router?**
**A:** App Router has a steeper learning curve and more complex caching behavior. Some libraries haven't fully adapted yet. But the performance and developer experience benefits outweigh these for new projects.

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

export default function LikeButton({ initialLikes }: { initialLikes: number }) {
    const [likes, setLikes] = useState(initialLikes);
    const [isLiked, setIsLiked] = useState(false);

    const handleLike = () => {
        if (isLiked) {
            setLikes(likes - 1);
        } else {
            setLikes(likes + 1);
        }
        setIsLiked(!isLiked);
    };

    return (
        <button 
            onClick={handleLike}
            className={isLiked ? 'text-red-500' : 'text-gray-500'}
        >
            ♥ {likes}
        </button>
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
import LikeButton from '@/components/LikeButton';

export default async function Feed() {
    // Server-side code
    const posts = await fetchPosts();

    return (
        <div>
            <h1>Your Feed</h1>
            {/* Server-rendered list */}
            <ul>
                {posts.map(post => (
                    <li key={post.id}>
                        <h2>{post.title}</h2>
                        {/* Client component for interactivity */}
                        <LikeButton initialLikes={post.likes} />
                    </li>
                ))}
            </ul>
        </div>
    );
}

// components/LikeButton.tsx (Client Component)
'use client';
import { useState } from 'react';

export default function LikeButton({ initialLikes }) {
    const [likes, setLikes] = useState(initialLikes);
    return <button onClick={() => setLikes(likes + 1)}>♥ {likes}</button>;
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

### There are NO Dumb Questions

**Q: Can a Server Component render a Client Component?**
**A:** Yes! Server Components can import and render Client Components. But Client Components cannot import Server Components - pass them as `children` instead.

**Q: How do I know if my component is a Server or Client Component?**
**A:** If it has `'use client'` at the top, it's a Client Component. Otherwise, it's a Server Component by default in the App Router.

**Q: Can I use server-only code (like database queries) in a Client Component?**
**A:** No! Client Components run in the browser. Fetch data in a Server Component parent and pass it as props, or use Server Actions for mutations.

---

## 7. Data Fetching: Getting Data

### Fetching in Server Components

Server Components can `await` data directly:

```tsx
// app/dashboard/page.tsx (Server Component)
async function getDashboardMetrics() {
    // Simulate database call
    const revenue = await db.orders.aggregate({ _sum: { total: true } });
    const users = await db.users.count();
    
    return { revenue, users };
}

export default async function DashboardPage() {
    const metrics = await getDashboardMetrics();

    return (
        <div className="grid grid-cols-2 gap-4">
            <Card title="Total Revenue" value={`$${metrics.revenue}`} />
            <Card title="Total Users" value={metrics.users} />
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

export default function LiveStockTicker() {
    const [price, setPrice] = useState(null);
    const [loading, setLoading] = useState(true);

    useEffect(() => {
        const interval = setInterval(() => {
            fetch('https://api.finance.com/stock/AAPL')
                .then(res => res.json())
                .then(data => {
                    setPrice(data.price);
                    setLoading(false);
                });
        }, 1000);

        return () => clearInterval(interval);
    }, []);

    if (loading) return <p>Loading market data...</p>;

    return <div>AAPL: ${price}</div>;
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

### Brain Power
🧠 In Next.js, you can fetch data in Server Components OR Client Components. When would you choose each?

**Answer:**
- **Server Components:** For initial data (SEO, no waterfall, direct DB access, no loading spinners)
- **Client Components (React Query/SWR):** For interactive data (polling, optimistic updates, user-triggered refetches, real-time)

### There are NO Dumb Questions

**Q: Do I always need loading.tsx and error.tsx?**
**A:** No, they're optional! But they improve UX. Without them, Next.js shows default loading and error states.

**Q: Can I use libraries like SWR or React Query?**
**A:** Yes, in Client Components! Server Components can fetch directly. Choose based on your needs.

**Q: What's the difference between `revalidate` and `no-store`?**
**A:** `revalidate: 60` caches for 60 seconds, then refreshes. `no-store` never caches, always fetches fresh.

---

## 8. Advanced Data Fetching

### Preloading Data

Start fetching data early so it's ready when needed. Combine `cache()` with a preload pattern:

```tsx
// lib/data.ts
import { cache } from 'react';

// cache() deduplicates: calling getPost('1') twice only fetches once
export const getPost = cache(async (id: string) => {
    const res = await fetch(`https://api.example.com/posts/${id}`);
    if (!res.ok) throw new Error('Failed to fetch post');
    return res.json();
});

// Preload function: kicks off fetch without awaiting
export function preloadPost(id: string) {
    void getPost(id);  // Start fetching, don't block
}
```

```tsx
// app/posts/[id]/page.tsx
import { getPost, preloadPost } from '@/lib/data';

export default async function Post({ params }: { params: { id: string } }) {
    // Start fetching immediately (runs in parallel with other work)
    preloadPost(params.id);

    // By the time we await, data may already be cached
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

## 9. Server Actions: Mutations

### What are Server Actions?

Server Actions are **async functions that run on the server**. They're great for form submissions, mutations, and any server-side operation.

```tsx
// app/actions.ts
'use server';

import { revalidatePath } from 'next/cache';

export async function updateUserProfile(formData: FormData) {
    const userId = formData.get('userId');
    const name = formData.get('name');
    const bio = formData.get('bio');

    // Server-side code (can access database)
    await db.users.update({
        where: { id: userId },
        data: { name, bio }
    });

    revalidatePath('/profile');
}
```

### Using Server Actions in Forms

```tsx
// app/profile/page.tsx
import { updateUserProfile } from '../actions';

export default function ProfilePage({ user }) {
    return (
        <form action={updateUserProfile}>
            <input type="hidden" name="userId" value={user.id} />
            
            <label>Name</label>
            <input name="name" defaultValue={user.name} required />
            
            <label>Bio</label>
            <textarea name="bio" defaultValue={user.bio} />
            
            <button type="submit">Save Changes</button>
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

### There are NO Dumb Questions

**Q: Can I call a Server Action from a Client Component?**
**A:** Yes! Import the action and use it in `form action={...}` or call it directly in event handlers. The action still runs on the server.

**Q: How do I show loading state during a Server Action?**
**A:** Use `useFormStatus()` in a child component of the form, or `useActionState()` which provides an `isPending` state.

**Q: Can Server Actions return data?**
**A:** Yes! Return values from Server Actions are passed to the client. Use `useActionState` to capture the return value and display success/error messages.

---

## 10. Runtimes: Node.js vs Edge

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

## 11. Layouts and Templates

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
                <footer>&copy; {new Date().getFullYear()}</footer>
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

### Layout Hierarchy

```
app/
├── layout.tsx          ← Root Layout (wraps everything)
├── page.tsx            ← Home page
├── dashboard/
│   ├── layout.tsx      ← Dashboard Layout (persists across dashboard pages)
│   ├── page.tsx        ← /dashboard
│   ├── settings/
│   │   └── page.tsx    ← /dashboard/settings (uses BOTH layouts)
│   └── analytics/
│       └── page.tsx    ← /dashboard/analytics (uses BOTH layouts)
└── auth/
    ├── layout.tsx      ← Auth Layout (different from dashboard)
    └── login/
        └── page.tsx    ← /auth/login
```

Navigating between `/dashboard/settings` and `/dashboard/analytics` keeps the Dashboard Layout mounted (sidebar stays, no re-render).

### Layout with Data Fetching

```tsx
// app/dashboard/layout.tsx
import { getUser } from '@/lib/data';

export default async function DashboardLayout({ children }: { children: React.ReactNode }) {
    // Layouts can be async Server Components!
    const user = await getUser();

    return (
        <div className="dashboard">
            <aside>
                <p>Welcome, {user.name}</p>
                <nav>
                    <Link href="/dashboard">Overview</Link>
                    <Link href="/dashboard/settings">Settings</Link>
                </nav>
            </aside>
            <section>{children}</section>
        </div>
    );
}
```

### Templates: Re-render on Navigation

Templates are like layouts but **re-mount on every navigation** (fresh state, effects re-run).

```tsx
// app/dashboard/template.tsx
'use client';

import { useEffect } from 'react';

export default function Template({ children }: { children: React.ReactNode }) {
    useEffect(() => {
        // Runs on EVERY navigation (unlike layout)
        logPageView();
    }, []);

    return <div className="animate-in">{children}</div>;
}
```

| Feature | Layout | Template |
|---------|--------|----------|
| Re-mounts on navigation | No (persists) | Yes (fresh) |
| Maintains state | Yes | No |
| Effects re-run | No | Yes |
| Use case | Shared UI, nav, sidebar | Animations, analytics, form resets |

### Watch It!
⚠️ **Layouts cannot access the current route!** They don't know which child page is active. Use `usePathname()` in a Client Component child if you need to highlight active nav links.

⚠️ **Don't pass data from layout to children via props!** Layouts don't re-render when children change. Use React Context or fetch data independently in each page.

### Brain Power
🧠 You have a multi-step form wizard at `/onboarding/step-1`, `/onboarding/step-2`, etc. Should you use a layout or template for the shared wrapper?

**Answer:** Use a **layout** if you want to preserve form state between steps (user navigates back without losing data). Use a **template** if each step should start fresh (reset form, re-run validation effects).

### There are NO Dumb Questions

**Q: Can I have multiple root layouts?**
**A:** Yes! Route groups let you have different root layouts: `(marketing)/layout.tsx` and `(app)/layout.tsx` each with their own `<html>` and `<body>`.

**Q: Why doesn't my layout re-render when I navigate?**
**A:** That's the point! Layouts persist to avoid unnecessary work. Only the `page.tsx` inside changes. Use a template if you need re-mounting behavior.

**Q: Can I access route params in a layout?**
**A:** Yes! Layouts receive a `params` prop: `function Layout({ children, params }: { children: ReactNode, params: { slug: string } })`.

---

## 12. Styling: Writing CSS

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

### Watch It!
⚠️ **CSS-in-JS libraries (styled-components, Emotion) require `'use client'`!** They use React context and hooks internally, so they can't run in Server Components. This adds client-side JavaScript. Prefer CSS Modules or Tailwind for Server Components.

### Brain Power
🧠 Why does Next.js recommend CSS Modules or Tailwind over CSS-in-JS?

**Answer:** CSS Modules and Tailwind extract CSS at build time (zero runtime cost). CSS-in-JS generates styles at runtime, adding JavaScript to the client bundle and requiring hydration. For Server Components, build-time CSS is the only option that works without `'use client'`.

### There are NO Dumb Questions

**Q: Which styling approach should I choose for a new Next.js project?**
**A:** Tailwind CSS is the most popular choice in the Next.js ecosystem (used by Vercel's own templates). CSS Modules are great if you prefer writing traditional CSS with scoping.

**Q: Can I use global CSS files?**
**A:** Yes, but only import them in `layout.tsx` or `page.tsx` files. Importing global CSS in components causes ordering issues.

**Q: How do I handle dynamic styles in Server Components?**
**A:** Use CSS custom properties (variables) set via inline `style` prop, or conditional class names with CSS Modules/Tailwind. No runtime CSS-in-JS allowed in Server Components.

---

## 13. Testing Your Next.js App

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
        ok: true,
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

## 14. Optimizations: Images, Fonts, Scripts

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

### Instrumentation & OpenTelemetry

Monitor your app's performance deeply with Instrumentation!

**What is it?**
A way to run code **before** your app starts and hook into Next.js internals to track performance, errors, and behavior.

**Setup:**
Create `instrumentation.ts` (or `.js`) in your root (or `src/`) directory.

```ts
// instrumentation.ts
export async function register() {
    if (process.env.NEXT_RUNTIME === 'nodejs') {
        await import('./instrumentation-node');
    }

    if (process.env.NEXT_RUNTIME === 'edge') {
        await import('./instrumentation-edge');
    }
}
```

**OpenTelemetry:**
Standardize your logging and tracing.

```bash
npm install @vercel/otel
```

```js
// next.config.js
module.exports = {
    experimental: {
        instrumentationHook: true,
    },
};
```

### Brain Power
🧠 Why would you lazy load a component instead of importing it normally?

**Answer:** Reduce initial bundle size! Heavy components (charts, editors, maps) make your first page load slow. Lazy loading splits them into separate chunks that only load when needed, making the initial page fast.

### Watch It!
⚠️ **Don't lazy load everything!** Only lazy load heavy components that aren't immediately needed. Lazy loading adds complexity and a small delay. Use it strategically for components like modals, charts, or below-the-fold content.

### There are NO Dumb Questions

**Q: Do I need to configure image domains?**
**A:** Yes! For external images, add allowed domains in `next.config.js`: `images: { remotePatterns: [{ hostname: 'example.com' }] }`. This prevents misuse of your image optimization.

**Q: Can I use `next/font` with Tailwind CSS?**
**A:** Yes! Assign the font to a CSS variable and reference it in your Tailwind config: `fontFamily: { sans: ['var(--font-inter)'] }`.

**Q: What's the difference between `priority` and lazy loading for images?**
**A:** `priority` preloads the image (for above-the-fold hero images). Without it, images lazy load by default (only load when scrolled into view).

---

## 15. API Routes: Building APIs

### Creating API Routes

```tsx
// app/api/webhooks/stripe/route.ts
import { headers } from 'next/headers';
import Stripe from 'stripe';

const stripe = new Stripe(process.env.STRIPE_SECRET_KEY);
const webhookSecret = process.env.STRIPE_WEBHOOK_SECRET;

export async function POST(request: Request) {
    const body = await request.text();
    const signature = headers().get('stripe-signature');

    let event;

    try {
        event = stripe.webhooks.constructEvent(body, signature, webhookSecret);
    } catch (err) {
        return Response.json({ error: `Webhook Error: ${err.message}` }, { status: 400 });
    }

    // Handle the event
    switch (event.type) {
        case 'checkout.session.completed':
            const session = event.data.object;
            // Fulfill the purchase...
            await db.orders.updateStatus(session.metadata.orderId, 'paid');
            break;
        default:
            console.log(`Unhandled event type ${event.type}`);
    }

    return Response.json({ received: true });
}
```

Visit `/api/webhooks/stripe` → (Handled by Stripe)

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

### There are NO Dumb Questions

**Q: Should I use API Routes or Server Actions for my backend?**
**A:** Server Actions for form mutations and internal data changes. API Routes for public APIs, webhooks, third-party integrations, or when you need specific HTTP methods/headers.

**Q: Can I use API Routes with the Edge Runtime?**
**A:** Yes! Add `export const runtime = 'edge'` to your route file. Great for fast, globally distributed endpoints that don't need Node.js APIs.

**Q: How do I handle CORS in API Routes?**
**A:** Set CORS headers manually in your response: `headers: { 'Access-Control-Allow-Origin': '*' }`. Or use middleware for global CORS handling.

---

## 16. Middleware: Request Processing

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

## 17. Caching: Performance

### How Next.js Caching Works

Next.js has **four caching layers** that work together:

```
Request → Router Cache (client) → Full Route Cache (server) → Data Cache (server) → Data Source
```

| Cache Layer | Location | Purpose | Duration |
|-------------|----------|---------|----------|
| **Request Memoization** | Server | Dedup same fetch in one render | Per request |
| **Data Cache** | Server | Store fetch responses | Persistent (until revalidated) |
| **Full Route Cache** | Server | Cache rendered HTML/RSC | Persistent (until revalidated) |
| **Router Cache** | Client | Cache visited routes | Session (30s dynamic, 5min static) |

### fetch() Cache Options

```tsx
// DEFAULT: Cached indefinitely (static)
const data = await fetch('https://api.example.com/data');

// Time-based revalidation: refetch after 1 hour
const data = await fetch('https://api.example.com/data', {
    next: { revalidate: 3600 }  // seconds
});

// Never cache: always fetch fresh (dynamic)
const data = await fetch('https://api.example.com/data', {
    cache: 'no-store'
});

// Tag-based: label fetches for targeted revalidation
const posts = await fetch('https://api.example.com/posts', {
    next: { tags: ['posts'] }
});

const user = await fetch(`https://api.example.com/users/${id}`, {
    next: { tags: ['users', `user-${id}`] }
});
```

### Route Segment Cache Config

Control caching at the page/layout level:

```tsx
// app/dashboard/page.tsx

// Make entire route dynamic (no caching)
export const dynamic = 'force-dynamic';

// Or set revalidation for all fetches in this route
export const revalidate = 60;  // Revalidate every 60 seconds

// Other options:
export const dynamic = 'auto';           // Default: Next.js decides
export const dynamic = 'force-static';   // Force static (error if dynamic)
export const fetchCache = 'force-no-store';  // No caching for all fetches
```

### On-Demand Revalidation

Invalidate cache when data changes (e.g., after a mutation):

```tsx
// app/actions.ts
'use server';

import { revalidatePath, revalidateTag } from 'next/cache';

export async function createPost(formData: FormData) {
    await db.posts.create({
        data: { title: formData.get('title') as string }
    });

    // Option 1: Revalidate a specific path
    revalidatePath('/posts');          // Revalidates /posts page
    revalidatePath('/posts', 'layout'); // Revalidates /posts and all nested routes

    // Option 2: Revalidate by tag (more granular)
    revalidateTag('posts');            // Invalidates all fetches tagged 'posts'
}

export async function updateUser(id: string, formData: FormData) {
    await db.users.update({ where: { id }, data: { ... } });

    // Revalidate just this user's data
    revalidateTag(`user-${id}`);
}
```

### Caching Non-fetch Data (unstable_cache)

Cache database queries, computations, or any async function:

```tsx
import { unstable_cache } from 'next/cache';

// Cache a database query
const getCachedPosts = unstable_cache(
    async (authorId: string) => {
        return await db.posts.findMany({
            where: { authorId },
            orderBy: { createdAt: 'desc' }
        });
    },
    ['posts-by-author'],  // Cache key parts
    {
        revalidate: 3600,     // Revalidate every hour
        tags: ['posts']       // Tag for on-demand revalidation
    }
);

// Usage in a Server Component
export default async function AuthorPosts({ authorId }: { authorId: string }) {
    const posts = await getCachedPosts(authorId);
    return <PostList posts={posts} />;
}
```

### Cache Strategies by Use Case

```tsx
// Blog posts: Cache forever, revalidate on publish
const post = await fetch(`/api/posts/${id}`, {
    next: { tags: [`post-${id}`] }
});

// User dashboard: Short cache, frequent updates
const stats = await fetch('/api/stats', {
    next: { revalidate: 30 }  // Fresh every 30 seconds
});

// Auth/session: Never cache
const session = await fetch('/api/auth/session', {
    cache: 'no-store'
});

// Product catalog: Medium cache, revalidate on inventory change
const products = await fetch('/api/products', {
    next: { revalidate: 300, tags: ['products'] }
});
```

### Watch It!
⚠️ **POST requests are never cached!** Only GET requests in fetch() use the Data Cache. If you need to cache a POST response, use `unstable_cache` wrapper instead.

⚠️ **Dynamic functions opt out of caching!** Using `cookies()`, `headers()`, or `searchParams` in a Server Component makes the entire route dynamic. Move these calls to the specific components that need them.

### Brain Power
🧠 You have a product page showing price and reviews. Price changes rarely but reviews update constantly. How would you cache them differently?

**Answer:** Use different revalidation strategies:
- Price: `next: { revalidate: 3600, tags: ['product-price'] }` (cache 1 hour)
- Reviews: `next: { revalidate: 30, tags: ['product-reviews'] }` (refresh every 30s)
- Or: Make reviews a Client Component with React Query, and keep the price in the cached Server Component

### There are NO Dumb Questions

**Q: How do I completely disable all caching during development?**
**A:** In Next.js 15+, fetch requests are uncached by default in development. For older versions, add `cache: 'no-store'` or set `export const dynamic = 'force-dynamic'` on your pages.

**Q: When should I use `revalidatePath` vs `revalidateTag`?**
**A:** Use `revalidatePath` when a mutation affects an entire page. Use `revalidateTag` when you want granular control - one mutation might invalidate data used across multiple pages.

**Q: Does the Router Cache cause stale data problems?**
**A:** It can! The client-side Router Cache means navigating back to a page shows the cached version. Call `router.refresh()` after mutations, or use Server Actions (they auto-invalidate the Router Cache).

---

## 18. Configuration: Setting Up Your App

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

### Linting (ESLint) & Formatting (Prettier)

Keep your code clean and consistent!

**ESLint (Built-in):**
Next.js comes with ESLint out of the box.

```bash
# Run linter
npm run lint
```

```json
// .eslintrc.json
{
  "extends": ["next/core-web-vitals", "next/typescript"]
}
```

**Prettier (Formatting):**
ESLint finds errors, Prettier fixes style.

```bash
npm install -D prettier eslint-config-prettier
```

```json
// .eslintrc.json
{
  "extends": ["next/core-web-vitals", "prettier"]
}
```

**Watch It!**
⚠️ **Always extend "prettier" last!** This turns off ESLint rules that might conflict with Prettier's formatting.

**Prettier Config:**
```json
// .prettierrc
{
  "semi": true,
  "singleQuote": true,
  "trailingComma": "es5"
}
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
date: "2025-01-15"
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

## 19. Authentication: Protecting Your App

### What is NextAuth.js (Auth.js)?

NextAuth.js (now called Auth.js) is the most popular authentication library for Next.js. It handles:
- OAuth providers (Google, GitHub, etc.)
- Email/password authentication
- Session management
- JWT tokens

### Installation

```bash
npm install next-auth
```

### Setting Up Providers

```tsx
// app/api/auth/[...nextauth]/route.ts
import NextAuth from 'next-auth';
import GoogleProvider from 'next-auth/providers/google';
import GitHubProvider from 'next-auth/providers/github';
import CredentialsProvider from 'next-auth/providers/credentials';

const handler = NextAuth({
    providers: [
        GoogleProvider({
            clientId: process.env.GOOGLE_CLIENT_ID!,
            clientSecret: process.env.GOOGLE_CLIENT_SECRET!,
        }),
        GitHubProvider({
            clientId: process.env.GITHUB_ID!,
            clientSecret: process.env.GITHUB_SECRET!,
        }),
        CredentialsProvider({
            name: 'Credentials',
            credentials: {
                email: { label: 'Email', type: 'email' },
                password: { label: 'Password', type: 'password' }
            },
            async authorize(credentials) {
                // Add your own logic here
                const user = await verifyUser(credentials.email, credentials.password);
                if (user) {
                    return user;
                }
                return null;
            }
        })
    ],
    pages: {
        signIn: '/login',
        error: '/auth/error',
    },
    callbacks: {
        async session({ session, token }) {
            session.user.id = token.sub;
            return session;
        },
    },
});

export { handler as GET, handler as POST };
```

### Session Provider

```tsx
// app/providers.tsx
'use client';

import { SessionProvider } from 'next-auth/react';

export function Providers({ children }: { children: React.ReactNode }) {
    return <SessionProvider>{children}</SessionProvider>;
}

// app/layout.tsx
import { Providers } from './providers';

export default function RootLayout({ children }) {
    return (
        <html>
            <body>
                <Providers>{children}</Providers>
            </body>
        </html>
    );
}
```

### Using Sessions in Client Components

```tsx
'use client';

import { useSession, signIn, signOut } from 'next-auth/react';

export default function AuthButton() {
    const { data: session, status } = useSession();

    if (status === 'loading') {
        return <p>Loading...</p>;
    }

    if (session) {
        return (
            <div>
                <p>Welcome, {session.user?.name}!</p>
                <img src={session.user?.image} alt="Avatar" />
                <button onClick={() => signOut()}>Sign out</button>
            </div>
        );
    }

    return (
        <div>
            <button onClick={() => signIn('google')}>Sign in with Google</button>
            <button onClick={() => signIn('github')}>Sign in with GitHub</button>
        </div>
    );
}
```

### Using Sessions in Server Components

```tsx
// app/dashboard/page.tsx
import { getServerSession } from 'next-auth';
import { redirect } from 'next/navigation';

export default async function Dashboard() {
    const session = await getServerSession();

    if (!session) {
        redirect('/login');
    }

    return (
        <div>
            <h1>Welcome, {session.user?.name}!</h1>
            <p>Email: {session.user?.email}</p>
        </div>
    );
}
```

### Protecting API Routes

```tsx
// app/api/protected/route.ts
import { getServerSession } from 'next-auth';
import { NextResponse } from 'next/server';

export async function GET() {
    const session = await getServerSession();

    if (!session) {
        return NextResponse.json(
            { error: 'Unauthorized' },
            { status: 401 }
        );
    }

    return NextResponse.json({
        message: 'Protected data',
        user: session.user
    });
}
```

### Middleware Authentication

```tsx
// middleware.ts
import { withAuth } from 'next-auth/middleware';

export default withAuth({
    pages: {
        signIn: '/login',
    },
});

export const config = {
    matcher: ['/dashboard/:path*', '/admin/:path*'],
};
```

### Brain Power
🧠 Why use NextAuth.js instead of building your own auth?

**Answer:** Security is hard! NextAuth.js handles CSRF protection, secure cookies, token rotation, and more. Building secure auth from scratch is error-prone. Let the experts handle it!

### Watch It!
⚠️ **Never store sensitive auth secrets in client components!** Use environment variables without NEXT_PUBLIC_ prefix for OAuth secrets. They should only be accessible on the server.

### There are NO Dumb Questions

**Q: What's the difference between NextAuth.js and Auth.js?**
**A:** Auth.js is the new name for NextAuth.js v5. It's framework-agnostic (works with SvelteKit, Express, etc.) but the Next.js adapter is the most mature.

**Q: How do I protect Server Components?**
**A:** Call `getServerSession()` at the top of your Server Component or layout. If no session, redirect to login. Middleware is faster for route-level protection.

**Q: Should I use JWT or database sessions?**
**A:** JWT for stateless/serverless (no DB needed per request, faster). Database sessions for more control (revocation, session listing). JWT is simpler for most apps.

---

## 20. Navigation Hooks: useParams, usePathname, useSearchParams

### useParams: Get Route Parameters

```tsx
'use client';

import { useParams } from 'next/navigation';

// URL: /blog/hello-world
// app/blog/[slug]/page.tsx
export default function BlogPost() {
    const params = useParams();
    // params = { slug: 'hello-world' }

    return <h1>Post: {params.slug}</h1>;
}
```

**Multiple parameters:**
```tsx
// URL: /shop/electronics/laptop
// app/shop/[category]/[product]/page.tsx
export default function Product() {
    const params = useParams();
    // params = { category: 'electronics', product: 'laptop' }

    return (
        <div>
            <p>Category: {params.category}</p>
            <p>Product: {params.product}</p>
        </div>
    );
}
```

### usePathname: Get Current Path

```tsx
'use client';

import { usePathname } from 'next/navigation';

export default function Navigation() {
    const pathname = usePathname();
    // pathname = '/dashboard/settings'

    return (
        <nav>
            <a
                href="/dashboard"
                className={pathname === '/dashboard' ? 'active' : ''}
            >
                Dashboard
            </a>
            <a
                href="/dashboard/settings"
                className={pathname === '/dashboard/settings' ? 'active' : ''}
            >
                Settings
            </a>
        </nav>
    );
}
```

### useSearchParams: Get Query Parameters

```tsx
'use client';

import { useSearchParams } from 'next/navigation';

// URL: /search?q=nextjs&page=2
export default function SearchPage() {
    const searchParams = useSearchParams();

    const query = searchParams.get('q'); // 'nextjs'
    const page = searchParams.get('page'); // '2'
    const missing = searchParams.get('foo'); // null

    return (
        <div>
            <p>Search: {query}</p>
            <p>Page: {page}</p>
        </div>
    );
}
```

**Updating search params:**
```tsx
'use client';

import { useSearchParams, useRouter, usePathname } from 'next/navigation';

export default function Filters() {
    const searchParams = useSearchParams();
    const router = useRouter();
    const pathname = usePathname();

    const updateFilter = (key: string, value: string) => {
        const params = new URLSearchParams(searchParams.toString());
        params.set(key, value);
        router.push(`${pathname}?${params.toString()}`);
    };

    return (
        <div>
            <button onClick={() => updateFilter('sort', 'price')}>
                Sort by Price
            </button>
            <button onClick={() => updateFilter('sort', 'date')}>
                Sort by Date
            </button>
        </div>
    );
}
```

### Combining Hooks

```tsx
'use client';

import { useParams, usePathname, useSearchParams } from 'next/navigation';

// URL: /products/shoes?color=red&size=10
export default function ProductPage() {
    const params = useParams();       // { category: 'shoes' }
    const pathname = usePathname();   // '/products/shoes'
    const searchParams = useSearchParams();

    return (
        <div>
            <p>Category: {params.category}</p>
            <p>Path: {pathname}</p>
            <p>Color: {searchParams.get('color')}</p>
            <p>Size: {searchParams.get('size')}</p>
        </div>
    );
}
```

### Watch It!
⚠️ **These hooks only work in Client Components!** Add `'use client'` directive. For Server Components, use the `params` and `searchParams` props passed to the page.

### There are NO Dumb Questions

**Q: What's the difference between params prop and useParams hook?**
**A:** The `params` prop is for Server Components (passed from Next.js). The `useParams()` hook is for Client Components. Same data, different access methods.

**Q: How do I update search params without a full page reload?**
**A:** Use `useRouter().push()` or `useRouter().replace()` with the new URL. Or use the native `URLSearchParams` API to construct the new query string and navigate programmatically.

### Brain Power
🧠 Why does Next.js separate navigation into `useParams`, `usePathname`, and `useSearchParams` instead of one unified hook?

**Answer:** Separation of concerns and re-rendering efficiency. If search params change, only components using `useSearchParams` re-render. Components using `usePathname` stay untouched. One big hook would cause unnecessary re-renders everywhere.

---

## 21. Special Files: File Conventions

### not-found.tsx: Custom 404 Page

```tsx
// app/not-found.tsx (root level)
import Link from 'next/link';

export default function NotFound() {
    return (
        <div>
            <h1>404 - Page Not Found</h1>
            <p>The page you're looking for doesn't exist.</p>
            <Link href="/">Go back home</Link>
        </div>
    );
}
```

**Trigger programmatically:**
```tsx
import { notFound } from 'next/navigation';

export default async function BlogPost({ params }) {
    const post = await getPost(params.slug);

    if (!post) {
        notFound(); // Shows not-found.tsx
    }

    return <article>{post.content}</article>;
}
```

**Nested not-found:**
```tsx
// app/blog/not-found.tsx
// Only shown for /blog/* 404s
export default function BlogNotFound() {
    return <p>Blog post not found. Check our latest posts!</p>;
}
```

### generateStaticParams: Static Dynamic Routes

Pre-render dynamic routes at build time!

```tsx
// app/blog/[slug]/page.tsx

// Generate static pages for these slugs
export async function generateStaticParams() {
    const posts = await getPosts();

    return posts.map((post) => ({
        slug: post.slug,
    }));
}

// Page component
export default async function BlogPost({ params }) {
    const post = await getPost(params.slug);
    return <article>{post.content}</article>;
}
```

**Multiple parameters:**
```tsx
// app/products/[category]/[id]/page.tsx
export async function generateStaticParams() {
    const products = await getProducts();

    return products.map((product) => ({
        category: product.category,
        id: product.id,
    }));
}
// Generates: /products/electronics/123, /products/clothing/456, etc.
```

**With fetch:**
```tsx
export async function generateStaticParams() {
    const res = await fetch('https://api.example.com/posts');
    const posts = await res.json();

    return posts.map((post) => ({
        slug: post.slug,
    }));
}
```

### global-error.tsx: Root Error Boundary

```tsx
// app/global-error.tsx
'use client';

export default function GlobalError({
    error,
    reset,
}: {
    error: Error;
    reset: () => void;
}) {
    return (
        <html>
            <body>
                <h2>Something went wrong!</h2>
                <button onClick={() => reset()}>Try again</button>
            </body>
        </html>
    );
}
```

### route.ts: Route Handlers

Supported HTTP methods:

```tsx
// app/api/resource/route.ts
export async function GET(request: Request) {}
export async function POST(request: Request) {}
export async function PUT(request: Request) {}
export async function PATCH(request: Request) {}
export async function DELETE(request: Request) {}
export async function HEAD(request: Request) {}
export async function OPTIONS(request: Request) {}
```

### File Convention Summary

```
app/
├── layout.tsx          # Shared UI wrapper
├── page.tsx            # Route UI
├── loading.tsx         # Loading UI
├── error.tsx           # Error UI
├── not-found.tsx       # 404 UI
├── global-error.tsx    # Root error UI
├── route.ts            # API endpoint
├── template.tsx        # Re-renders on navigation
├── default.tsx         # Parallel route fallback
└── middleware.ts       # Request middleware (root only)
```

### Brain Power
🧠 Why use generateStaticParams instead of letting pages render on-demand?

**Answer:** Performance! Static pages are pre-built and served from CDN instantly. No server rendering needed. Perfect for blogs, docs, and content that doesn't change often.

### Watch It!
⚠️ **`error.tsx` must be a Client Component!** It uses `'use client'` because error boundaries need to catch errors on the client side too. Always include a `reset` button so users can retry.

### There are NO Dumb Questions

**Q: What's the difference between `error.tsx` and `global-error.tsx`?**
**A:** `error.tsx` catches errors in its segment and below. `global-error.tsx` catches errors in the root layout itself (the only way to handle root-level errors). It must include its own `<html>` and `<body>` tags.

**Q: When would I use `default.tsx`?**
**A:** Only with parallel routes. It's the fallback shown when a parallel slot doesn't match the current URL (like navigating to a route that doesn't have content for that slot).

**Q: Can I have `loading.tsx` at every route level?**
**A:** Yes! Each segment can have its own loading state. Deeper loading files override parent ones for that segment, creating granular loading UIs.

---

## 22. Security Best Practices

### Content Security Policy (CSP)

```tsx
// middleware.ts
import { NextResponse } from 'next/server';

export function middleware(request) {
    const nonce = Buffer.from(crypto.randomUUID()).toString('base64');

    const cspHeader = `
        default-src 'self';
        script-src 'self' 'nonce-${nonce}' 'strict-dynamic';
        style-src 'self' 'unsafe-inline';
        img-src 'self' blob: data:;
        font-src 'self';
        object-src 'none';
        base-uri 'self';
        form-action 'self';
        frame-ancestors 'none';
        upgrade-insecure-requests;
    `.replace(/\s{2,}/g, ' ').trim();

    const response = NextResponse.next();
    response.headers.set('Content-Security-Policy', cspHeader);
    response.headers.set('x-nonce', nonce);

    return response;
}
```

### Security Headers

```tsx
// next.config.js
module.exports = {
    async headers() {
        return [
            {
                source: '/:path*',
                headers: [
                    {
                        key: 'X-DNS-Prefetch-Control',
                        value: 'on'
                    },
                    {
                        key: 'Strict-Transport-Security',
                        value: 'max-age=63072000; includeSubDomains; preload'
                    },
                    {
                        key: 'X-Frame-Options',
                        value: 'SAMEORIGIN'
                    },
                    {
                        key: 'X-Content-Type-Options',
                        value: 'nosniff'
                    },
                    {
                        key: 'Referrer-Policy',
                        value: 'origin-when-cross-origin'
                    },
                    {
                        key: 'Permissions-Policy',
                        value: 'camera=(), microphone=(), geolocation=()'
                    }
                ]
            }
        ];
    }
};
```

### Input Validation with Zod

```tsx
'use server';

import { z } from 'zod';

const userSchema = z.object({
    email: z.string().email('Invalid email'),
    password: z.string().min(8, 'Password must be at least 8 characters'),
    name: z.string().min(2).max(50),
});

export async function createUser(formData: FormData) {
    const rawData = {
        email: formData.get('email'),
        password: formData.get('password'),
        name: formData.get('name'),
    };

    const result = userSchema.safeParse(rawData);

    if (!result.success) {
        return { errors: result.error.flatten().fieldErrors };
    }

    // Safe to use result.data
    await db.users.create({ data: result.data });
}
```

### Environment Variable Validation

```tsx
// lib/env.ts
import { z } from 'zod';

const envSchema = z.object({
    DATABASE_URL: z.string().url(),
    NEXTAUTH_SECRET: z.string().min(32),
    NEXTAUTH_URL: z.string().url(),
});

export const env = envSchema.parse(process.env);
```

### Rate Limiting

```tsx
// lib/rate-limit.ts
const rateLimit = new Map();

export function rateLimiter(ip: string, limit = 10, window = 60000) {
    const now = Date.now();
    const windowStart = now - window;

    const requestTimestamps = rateLimit.get(ip) || [];
    const requestsInWindow = requestTimestamps.filter(
        (timestamp: number) => timestamp > windowStart
    );

    if (requestsInWindow.length >= limit) {
        return false; // Rate limited
    }

    requestsInWindow.push(now);
    rateLimit.set(ip, requestsInWindow);
    return true; // Allowed
}
```

```tsx
// app/api/submit/route.ts
import { rateLimiter } from '@/lib/rate-limit';

export async function POST(request: Request) {
    const ip = request.headers.get('x-forwarded-for') || 'unknown';

    if (!rateLimiter(ip)) {
        return Response.json(
            { error: 'Too many requests' },
            { status: 429 }
        );
    }

    // Process request...
}
```

### Brain Power
🧠 Why is server-side validation not enough? Why do we also need CSP headers?

**Answer:** Validation prevents malicious data from being stored. CSP prevents malicious scripts from executing even if they slip through (defense in depth). A stored XSS payload might bypass validation but CSP blocks it from running in the browser.

### Watch It!
⚠️ **Never trust client input!** Always validate on the server. Client-side validation is for UX, server-side validation is for security. Use libraries like Zod for both.

### There are NO Dumb Questions

**Q: Do I need CSP for every app?**
**A:** For production apps with user content, YES! CSP prevents XSS attacks. Start strict and loosen as needed.

**Q: Why validate environment variables?**
**A:** Fail fast! If a required env var is missing, you want to know at startup, not when a user hits that code path.

---

## 23. Turbopack: The New Bundler

### What is Turbopack?

Turbopack is Next.js's new Rust-based bundler, designed to replace Webpack. It's significantly faster!

**Benefits:**
- Up to 700x faster than Webpack
- Incremental compilation
- Built in Rust for speed
- Drop-in replacement

### Using Turbopack

```bash
# Development with Turbopack
next dev --turbo

# Or in package.json
{
    "scripts": {
        "dev": "next dev --turbo"
    }
}
```

### When to Use Turbopack

**Use Turbopack when:**
- You want faster dev server startup
- You want faster hot module replacement (HMR)
- You're starting a new project

**Stick with Webpack when:**
- You need custom Webpack plugins
- You use unsupported features
- You need production builds (Turbopack is dev-only currently)

### Configuration

```js
// next.config.js
module.exports = {
    experimental: {
        turbo: {
            rules: {
                '*.svg': {
                    loaders: ['@svgr/webpack'],
                    as: '*.js',
                },
            },
        },
    },
};
```

### Watch It!
⚠️ **Turbopack is still in beta for production builds!** Use it for development, but production builds still use Webpack. Check the Next.js docs for the latest status.

### Brain Power
🧠 Why is Turbopack written in Rust instead of JavaScript?

**Answer:** Bundling is CPU-intensive work (parsing, transforming, linking). Rust is orders of magnitude faster than JavaScript for computation-heavy tasks. Webpack runs in Node.js (single-threaded JS), while Turbopack leverages Rust's zero-cost abstractions and parallelism.

### There are NO Dumb Questions

**Q: Do I need to change my code to use Turbopack?**
**A:** No! It's a drop-in replacement. Your components, imports, and config work the same. Only custom Webpack plugins might need migration.

**Q: Can I still use Webpack plugins with Turbopack?**
**A:** Not directly. Turbopack has its own plugin system (`turbo.rules`). Some Webpack loaders work, but complex plugins need alternatives. Check the Turbopack docs for compatibility.

**Q: Should I switch to Turbopack now?**
**A:** For development, yes! The speed improvement is dramatic. For production builds, wait until it's stable (check `next build --turbo` support in your Next.js version).

---

## 24. Partial Prerendering (PPR)

### What is PPR?

Partial Prerendering combines static and dynamic rendering in a single page. The static shell loads instantly, then dynamic content streams in.

```
┌─────────────────────────────┐
│ Static Header (instant)     │
├─────────────────────────────┤
│ Static Content (instant)    │
├─────────────────────────────┤
│ [Loading...] → Dynamic Data │
├─────────────────────────────┤
│ Static Footer (instant)     │
└─────────────────────────────┘
```

### Enabling PPR

```js
// next.config.js
module.exports = {
    experimental: {
        ppr: true,
    },
};
```

### Using PPR

```tsx
// app/dashboard/page.tsx
import { Suspense } from 'react';

export default function Dashboard() {
    return (
        <div>
            {/* Static - rendered at build time */}
            <header>
                <h1>Dashboard</h1>
                <nav>...</nav>
            </header>

            {/* Dynamic - streams in */}
            <Suspense fallback={<p>Loading stats...</p>}>
                <DynamicStats />
            </Suspense>

            {/* Static */}
            <footer>© 2025 My App</footer>
        </div>
    );
}

async function DynamicStats() {
    const stats = await fetch('https://api.example.com/stats', {
        cache: 'no-store' // Makes this dynamic
    });

    return <StatsDisplay data={stats} />;
}
```

### How PPR Works

1. **Build time:** Static parts are pre-rendered
2. **Request time:** Static shell served instantly from CDN
3. **Streaming:** Dynamic parts stream in with Suspense

### Benefits

- **Fastest possible initial load** (static shell)
- **Fresh dynamic data** (streaming)
- **Best of both worlds** (SSG + SSR)

### Brain Power
🧠 How is PPR different from regular Suspense streaming?

**Answer:** Regular streaming renders everything on request. PPR pre-renders the static shell at build time and only streams the dynamic parts. The static shell loads from CDN instantly!

### Watch It!
⚠️ **PPR is experimental!** It's a preview feature as of Next.js 14. The API may change. Great to learn, but check docs before production use.

### There are NO Dumb Questions

**Q: Do I need to change my code to use PPR?**
**A:** Mostly no! If you're already using Suspense boundaries for dynamic content, PPR automatically detects static vs dynamic parts. Just enable it in config.

**Q: What makes a component "dynamic" in PPR?**
**A:** Any component that uses `cookies()`, `headers()`, `searchParams`, or uncached data fetching. Everything else is treated as static and pre-rendered.

**Q: Can I use PPR with any hosting provider?**
**A:** Currently best supported on Vercel. Self-hosting PPR requires Node.js infrastructure that can handle streaming responses.

---

## 25. Deployment: Going Live

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

### Output Modes & Adapters

Customize your build for your hosting platform.

**Standalone Mode (Docker/Self-hosting):**
Automatically traces dependencies and creates a minimal server folder. Huge space saver!

```js
// next.config.js
module.exports = {
    output: 'standalone'
};
```

**Result:**
Creates `.next/standalone`. You can run this folder with just `node server.js` without `node_modules` (mostly)!

### Brain Power
🧠 Why is "standalone" mode better for Docker?

**Answer:** It copies only the necessary files from `node_modules` into the output folder. Your Docker image becomes significantly smaller because you don't need the entire 500MB+ `node_modules` folder, just the parts you actually use.

### Watch It!
⚠️ **Static export (`output: 'export'`) disables server features!** No Server Components, no API routes, no middleware, no ISR. Only use it for purely static sites (docs, marketing pages). For most apps, use `standalone` or deploy to Vercel.

### There are NO Dumb Questions

**Q: Can I deploy Next.js anywhere, or only Vercel?**
**A:** Anywhere! Vercel is easiest (zero config), but Next.js works on AWS, GCP, Railway, Docker, or any Node.js host. Use `standalone` output for self-hosting.

**Q: Do I need a Node.js server for Next.js?**
**A:** For full features (SSR, API routes, Server Actions), yes. For static export, any CDN/static host works (Netlify, GitHub Pages, S3).

**Q: How do I handle environment variables in production?**
**A:** Set them in your hosting platform's dashboard (Vercel, Railway, etc.) or in your Docker container. Never commit `.env.local` to git. Build-time vars (`NEXT_PUBLIC_`) are baked into the bundle.

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

**Authentication (NextAuth.js):**
```tsx
// app/api/auth/[...nextauth]/route.ts
import NextAuth from 'next-auth';
import GoogleProvider from 'next-auth/providers/google';

const handler = NextAuth({
    providers: [
        GoogleProvider({
            clientId: process.env.GOOGLE_CLIENT_ID!,
            clientSecret: process.env.GOOGLE_CLIENT_SECRET!,
        }),
    ],
});
export { handler as GET, handler as POST };

// Check session (server)
import { getServerSession } from 'next-auth';
const session = await getServerSession();

// Check session (client)
'use client';
import { useSession } from 'next-auth/react';
const { data: session } = useSession();
```

**Navigation Hooks:**
```tsx
'use client';
import { useParams, usePathname, useSearchParams } from 'next/navigation';

const params = useParams();           // { slug: 'hello' }
const pathname = usePathname();       // '/blog/hello'
const searchParams = useSearchParams();
const query = searchParams.get('q');  // 'nextjs'
```

**Special Files:**
```tsx
// not-found.tsx - Custom 404
import { notFound } from 'next/navigation';
if (!post) notFound();

// generateStaticParams - Pre-render dynamic routes
export async function generateStaticParams() {
    const posts = await getPosts();
    return posts.map((post) => ({ slug: post.slug }));
}
```

**Security:**
```tsx
// Input validation with Zod
import { z } from 'zod';
const schema = z.object({
    email: z.string().email(),
    password: z.string().min(8),
});
const result = schema.safeParse(data);
```

**Turbopack:**
```bash
# Fast dev server with Turbopack
next dev --turbo
```

**Partial Prerendering (PPR):**
```tsx
// next.config.js
module.exports = { experimental: { ppr: true } };

// Static shell + dynamic streaming
<Suspense fallback={<Loading />}>
    <DynamicComponent />
</Suspense>
```

---

**Created in the style of Head First books**

*Now go build the next big thing with Next.js!*