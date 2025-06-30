# 🧩 Micro-Frontends in System Design

Micro-frontends is an architectural style where a frontend app is **split into smaller, semi-independent "micro-apps"**, owned by different teams, and composed together in a single UI.

It brings the **microservices philosophy** to the frontend world.

---

## 🧠 Why Micro-Frontends?

- Frontend monoliths become **hard to scale** and evolve with growing teams
- Dev teams need **autonomy** to build, deploy, and scale independently
- Supports **parallel development** and faster delivery in large orgs

---

## 🔧 Core Principles

1. **De-centralize code ownership**  
   Each team owns their micro-app end-to-end.

2. **Isolate deployments**  
   Teams can deploy independently, without needing full app rebuild.

3. **Tech agnostic**  
   Different teams can use different frameworks (e.g., React + Vue in same app).

4. **Composable UI**  
   Final app is composed at build-time, runtime, or client-side.

---

## 🛠️ Implementation Strategies

### 1. **Build-Time Integration**
- All micro-apps are imported and bundled together during the main app’s build.
- Simple, but **tight coupling**.

### 2. **Run-Time Integration via Module Federation (Webpack 5)**
- Micro-apps are **exposed remotely** and loaded at runtime.
- Enables **true independence** and lazy loading.

> Common in apps using Next.js + Webpack Module Federation

### 3. **iFrame Integration**
- Micro-apps loaded in iFrames
- Easy to isolate, but poor UX and interop.

### 4. **Server-Side Composition**
- Server assembles micro-frontend HTML from various services
- Useful for SSR-heavy apps (e.g., retail platforms)

---

## 🧪 Tools & Frameworks

- **Webpack Module Federation**
- **Single-SPA** (or parcel-based frameworks)
- **Module Federation Plugin (Next.js)**  
- **Nx** (for monorepo setups)
- **Luigi Framework** (SAP)

---

## 📦 Real-World Examples

- **Spotify**: each section (browse, library, player) is a micro-app
- **Amazon**: product detail page composed of micro-apps (ads, price, description)
- **Zalando**, **IKEA**, and many e-commerce giants

---

## ✅ Benefits

| Feature | Value |
|--------|-------|
| 🔁 Scalability | Different teams own different domains |
| 🚀 Faster releases | Independent deployments |
| 🧩 Flexibility | Mix tech stacks (if needed) |
| 🧪 Fault isolation | One micro-app fails? Rest survive. |

---

## ❌ Drawbacks

| Concern | Description |
|--------|-------------|
| 📦 Bundle duplication | Same libraries across micro-apps |
| 📉 UX inconsistency | Varying styles / behaviors |
| ⚙️ Dev complexity | Setup, routing, and shared state are harder |
| 🔗 Shared dependencies | Must carefully version-manage shared libs |

---

## 📍 When to Use Micro-Frontends?

✅ Go for it when:
- You have multiple large teams
- You're building a platform with distinct sections/domains
- You want CI/CD autonomy for teams

❌ Avoid if:
- App is small-to-medium sized
- You don’t have infra to support this complexity

---

## 📘 Summary

- Micro-frontends help scale frontend teams for large orgs
- Comes with infra & architectural complexity
- Best suited for **product ecosystems**, not just apps

