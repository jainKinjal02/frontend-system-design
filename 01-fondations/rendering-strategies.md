# 🌐 Rendering Strategies in Frontend System Design

Rendering strategies define **when** and **where** your frontend app generates the HTML that users eventually see. Choosing the right strategy depends on your product’s goals — speed, SEO, personalization, scalability, etc.

---

## 1️⃣ Client-Side Rendering (CSR)

In CSR, the browser downloads a bare HTML shell and a JavaScript bundle. Rendering happens **entirely in the browser**.

### ✅ Pros
- Rich interactivity
- Faster after initial load (SPA-like experience)
- Works well with CDNs

### ❌ Cons
- Slower initial paint (blank screen → JS download → render)
- Poor SEO by default

### 💡 Use When
- App is highly interactive (dashboards, tools)
- SEO is not a priority

---

## 2️⃣ Server-Side Rendering (SSR)

In SSR, HTML is generated **on the server at request time** and sent to the client.

### ✅ Pros
- Faster first contentful paint
- SEO-friendly
- Better performance on slower devices

### ❌ Cons
- Slower TTFB (Time To First Byte)
- Server load increases
- Needs backend infra to render

### 💡 Use When
- SEO is critical (marketing pages, blogs)
- Personalization needed before first paint

---

## 3️⃣ Static Site Generation (SSG)

Pages are **pre-rendered at build time** into static HTML. No server work needed on each request.

### ✅ Pros
- Blazing fast
- Scalable (served from CDN)
- Great for SEO

### ❌ Cons
- Not good for frequent updates or dynamic content
- Rebuilds needed after content changes

### 💡 Use When
- Content doesn’t change often (docs, blogs, landing pages)

---

## 4️⃣ Incremental Static Regeneration (ISR) (Next.js)

A hybrid where pages are statically built but can be updated **at runtime** on a timer or trigger.

### ✅ Pros
- Combines benefits of SSG + SSR
- Pages update without full rebuild

### ❌ Cons
- Complex caching logic
- Might serve stale content for a short while

### 💡 Use When
- Semi-dynamic content (product pages, news articles)

---

## 🧠 Comparison Table

| Strategy | TTFB | SEO Friendly | Personalization | Infra Need | Example Use Case |
|----------|------|--------------|------------------|-------------|------------------|
| CSR      | ⛔️ High | ❌ No       | ✅ Yes          | Low         | Dashboards       |
| SSR      | ✅ Medium | ✅ Yes     | ✅ Yes          | Medium      | Ecommerce pages  |
| SSG      | ✅ Low | ✅ Yes       | ❌ No           | Very Low    | Docs, blogs      |
| ISR      | ✅ Low-Medium | ✅ Yes | ✅ Partial     | Medium      | Product listings |

---

## 🔗 Tools & Framework Support

- **React** – CSR by default
- **Next.js** – Supports CSR, SSR, SSG, ISR
- **Gatsby** – Focused on SSG
- **Astro** – Island architecture, partial hydration
- **Remix** – Embraces SSR + streaming

---

## 🖼️ Bonus: Simple Diagram

