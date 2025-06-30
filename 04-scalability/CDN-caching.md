
---

### 📄 `04-scalability/CDN-caching.md`

```markdown
# 🚀 CDN & Caching for Frontend Scalability

To handle millions of users globally with low latency, frontend systems need **CDNs (Content Delivery Networks)** and smart **caching** strategies.

---

## 🌍 What is a CDN?

A CDN is a globally distributed network of edge servers that **cache and serve content** closer to the user’s location.

### 📦 Common CDN-Served Assets
- JS/CSS bundles
- Images, fonts, videos
- Static HTML (SSG)
- APIs (in edge functions)

> Providers: Cloudflare, Akamai, Vercel, Netlify, AWS CloudFront

---

## 🔁 Caching Strategies

### 1. **Browser Caching**

Tell the browser how long to cache assets via HTTP headers.

```http
Cache-Control: max-age=31536000, immutable
