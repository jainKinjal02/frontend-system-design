# 💤 Lazy Loading in Frontend Performance

Lazy loading is a performance optimization strategy where **non-critical resources** are loaded **only when needed**, reducing initial load time and improving user experience.

---

## 🎯 Why Lazy Load?

- Reduce **initial bundle size**
- Improve **First Contentful Paint (FCP)**
- Prioritize what matters to users *first*

---

## 🧠 What Can You Lazy Load?

- Images
- Components
- Routes
- Third-party libraries
- Videos, charts, heavy modules

---

## 🔧 Implementing Lazy Loading

### 🖼️ Lazy Loading Images

```html
<img src="image.jpg" loading="lazy" alt="..." />


import React, { lazy, Suspense } from 'react';

const Chart = lazy(() => import('./Chart'));

function Dashboard() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <Chart />
    </Suspense>
  );
}

🛣️ Route-Based Lazy Loading (React Router)
const Admin = lazy(() => import('./pages/Admin'));

<Route path="/admin" element={<Admin />} />


![Lazy Loading Diagram](./image.png)