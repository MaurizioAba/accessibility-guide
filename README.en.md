# 📘 Accessibility Best Practices in Web Development (WCAG)

A practical guide for **building accessible React interfaces**, based on WCAG (https://www.w3.org/WAI/standards-guidelines/wcag/) and community-shared best practices.

> This guide, written in Italian, is intended for developers who want to write code that's **inclusive**, **keyboard-navigatable**, screen-reader compatible, and more sustainable for everyone.

---

## 🚀 Goals

- Use semantic HTML correctly
- Implement full keyboard navigation
- Build React components with accessibility in mind
- Avoid common patterns that hinder usability for people with disabilities

---

## Recommended Tools

- axe DevTools – Browser accessibility testing
- Lighthouse – Performance & accessibility audits
- eslint-plugin-jsx-a11y – Accessibility linting for JSX
- React ARIA – ARIA-ready components library

## Helpful Resources

- WCAG 2.2 Quick Reference
- MDN Accessibility Guide
- The A11Y Project
- Inclusive Components

## Best Practice

### 1. **Use Semantic HTML**
- Use proper tags: `button`, `header`, `nav`, `main`, `footer`, `form` etc.
- Avoid using `div` or `span`. as replacements for semantic elements.

### 2. **Keyboard Navigation**
- Ensure all interactions are accessible via `Tab`, `Enter` or `Space`.
- Avoid non-focusable elements like  `div onClick`.

### 3. **Use ARIA Attributes When Needed**
- Use `aria-label`, `aria-describedby`, `role="alert"` where appropriate.
- Prefer native HTML semantics before reaching for ARIA.

### 4. **Focus Management**
- Use `tabIndex={0}` for custom focusable elements.
- Use  `ref` and `element.focus()`  to handle dynamic flows (e.g. modals, skip links).

### 5. **Accessible Forms**
- Associate `label` elements using (`htmlFor` and `id`).
- Display errors using `role="alert"`.
- Add instructions using `aria-describedby`.

### 6. **Color and Contrast**
- Ensure a minimum contrast ratio of 4.5:1 for regular text.
- Use [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/).

### 7. **Skip to Content**
Allow users to skip directly to main content:
`<a href="#main-content" className="sr-only focus:not-sr-only">Skip to content</a>`

### 8. **Prefer Native Interactive Elements**
- Avoid recreating buttons or links using <div> or <span> with onClick.
- This breaks accessibility because:
- They're not keyboard-focusable without tabIndex
- They don't trigger expected keyboard behaviors (e.g. Enter or Space)
- They lack predefined roles and screen reader announcements
Always use native elements like:

`<button> for actions (submit, toggle, modal…) <a href> for navigation <input>, <textarea>` for forms

### 9. **Descriptive Alt Text for Images**
- Images must always include the alt attribute for screen reader accessibility.
For decorative images, use alt="" to avoid unnecessary screen reader announcements.

`<img src="profile.png" alt="Profile photo of Mario Rossi" />`

### 10. **Structured Headings (h1–h6)**
- Use headings in hierarchical order.
- Don’t skip levels (e.g., don’t use h3 without an h2).

### 11. **Accessible Responsiveness**
- Ensure all content is readable at 200% zoom.
- Avoid horizontal scrolling and fixed-width layouts that prevent scaling.

### 12. **Visible Focus States**
- Make sure focus indicators are clearly visible (e.g. outline, border, shadow).
Use :focus-visible or maintain consistent outline styling.

### 13. **Announcing Dynamic Updates**
- Use role="status" or role="alert" for real-time notifications.
Example: “Item added to cart.”

### 14. **Screen Reader Testing**
- Test with screen readers like VoiceOver, NVDA, or JAWS.
- Check for consistent reading of content and form fields.

### 15. **Animations and Motion**
- Avoid fast or complex animations.
- Respect the user’s system preference for reduced motion (prefers-reduced-motion).

### 16. **ARIA Live Regions**
- Use aria-live="polite" or aria-live="assertive" for dynamic updates.
Example: real-time filter results.

### 17. **Landmark Roles**
- Use semantic landmarks: `<main>, <nav>, <aside> or role="main", role="navigation"`, etc.
These help screen reader users navigate more efficiently.

### 18. **Media Content**
- Video: Always include captions
- Audio: Provide transcripts

### 19. **Error Handling in Forms**
- Highlight errors with both color and text (not just red).
- Use `aria-invalid="true` and aria-describedby for contextual info.

### 20. **Accessible Custom Components**
- When building custom UI elements (modals, dropdowns, menus):
Allow closing with Esc
Trap focus within the component
- Announce content using aria-labelledby
