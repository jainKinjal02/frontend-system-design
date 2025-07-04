# 🔐 Authentication & Authorization in Frontend

Authentication = **who you are**  
Authorization = **what you can access**

Modern frontend apps must handle both **securely**, **scalably**, and **UX-smoothly**.

---

## 🧠 Key Differences

| Feature           | Authentication            | Authorization                   |
|------------------|----------------------------|----------------------------------|
| Purpose          | Identity verification      | Access control                   |
| Result           | Logged-in session          | Permission to use features/data |
| Happens When     | On login                   | On each API / route              |

---

## 🛠️ Common Authentication Methods

### 1. **Token-Based (JWT)**
- Login returns JWT token
- Token stored in client (browser)
- Sent with every API call in `Authorization` header

### 2. **Session-Based (via Cookies)**
- Server sets a session cookie
- Automatically sent with every request
- Common with SSR frameworks

---

## ⚠️ Where to Store Tokens?

| Storage        | Pros                          | Cons                          |
|----------------|-------------------------------|-------------------------------|
| `localStorage` | Easy to use                   | Vulnerable to XSS             |
| `sessionStorage`| Short-lived tabs             | Still XSS-prone               |
| `httpOnly Cookies` | Secure from JS (XSS safe) | CSRF risk (can be mitigated) |

> ✅ **Preferred:** `httpOnly secure cookies` for sensitive apps (esp. SSR).

---

## 🛣️ Authentication Flow (Frontend Perspective)

1. User submits login form
2. Token or session is returned
3. Frontend stores auth state (cookie, localStorage, context)
4. Protect routes / fetch user data
5. Logout = remove token / cookie

---

## 🔐 Authorization in Frontend

Frontend must enforce **what users can see or do**:

### Examples:
- Admin-only routes
- Conditional UI (`if (user.role === 'manager')`)
- Button visibility
- API calls to restricted endpoints

---

## 🛡️ Protecting Routes

### React (Client Side)
```js
<Route path="/admin" element={user?.role === 'admin' ? <AdminPage /> : <Navigate to="/403" />} />

Next.js SSR example:
export const getServerSideProps = async (ctx) => {
  const token = getTokenFromCookie(ctx.req);
  if (!token || !isAdmin(token)) {
    return { redirect: { destination: '/login', permanent: false } };
  }
  return { props: {} };
};

Token Refresh & Auto-Logout
Short-lived access tokens + long-lived refresh tokens

Auto-logout when refresh fails

Use interceptors (e.g., Axios) for token renewal

axios.interceptors.response.use(null, async error => {
  if (error.response.status === 401) {
    await refreshAccessToken(); // Try refreshing token
    return retryOriginalRequest(); // Retry original request
  }
});


Security Best Practices:

| Practice                                   | Benefit                |
| ------------------------------------------ | ---------------------- |
| `SameSite` cookies                         | Prevent CSRF           |
| Use `secure`, `httpOnly`                   | Prevent XSS data theft |
| Don’t store sensitive info in localStorage | Prevent exposure       |
| Use server-based auth when possible        | Harder to tamper with  |

