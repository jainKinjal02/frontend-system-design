
---

### 📄 `05-design-principles/accessibility.md`

```markdown
# ♿ Accessibility in Frontend Design

**Accessibility (a11y)** ensures that apps are usable by **everyone**, including people with disabilities — vision, hearing, mobility, or cognitive.

It’s not just ethical — it’s **required by law** (WCAG, ADA, etc).

---

## 🎯 Why Accessibility Matters

- 1 in 7 people worldwide has a disability
- Enhances UX for everyone (keyboard users, low bandwidth)
- Improves SEO (screen readers love structure)
- Legal compliance & inclusivity

---

## 🧩 Key Principles (WCAG 2.1)

| Principle | Description |
|----------|-------------|
| 🧠 Perceivable | Users must see/hear content (alt text, captions) |
| 🖱️ Operable | Fully usable via keyboard |
| 📚 Understandable | Clear labels, instructions, feedback |
| 🔐 Robust | Works with assistive tech (screen readers, ARIA) |

---

## 🛠️ Techniques

### ✅ Semantic HTML

```html
<button>Submit</button> <!-- Good -->
<div onClick="submit()">Submit</div> <!-- Bad -->


✅ Keyboard Navigation
Use tabindex, <a>, <button>

Ensure modal/dialog focus trapping

✅ ARIA Roles
html
Copy
Edit
<div role="alert">Form error</div>
Use ARIA only when semantic HTML doesn't suffice