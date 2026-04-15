# Todo Card Component

This directory contains a modern, fully responsive, and accessible Todo/Task Card component built for the **Frontend Wizards — Stage 0 Task**.

## Features & Requirements Checklist

The implementation has been verified and it **successfully meets all the specified requirements**:

### Exact `data-testid` Signatures

- `test-todo-card` (Root `<article>` element)
- `test-todo-title` (`<h2>` Task title)
- `test-todo-description` (`<p>` Task description)
- `test-todo-priority` (Priority label displaying "High")
- `test-todo-due-date` (Formatted `<time>` element)
- `test-todo-time-remaining` (`<time>` element that auto-updates)
- `test-todo-status` (Status indicator)
- `test-todo-complete-toggle` (`<input type="checkbox">` with label)
- `test-todo-tags` (`<div role="list">` Tags container)
- `test-todo-tag-work` & `test-todo-tag-urgent` (Specific list items)
- `test-todo-edit-button` (Edit `<button>`)
- `test-todo-delete-button` (Delete `<button>`)

### Semantic HTML

- Wraps the component cleanly within an `<article>`.
- Appropriately uses native `<time>`, `<p>`, `<h2>`, `<button>` and valid nested text containers.
- Inputs and forms use native elements `<label>` > `<input type="checkbox">`.

### Accessibility (A11y)

- Added `aria-label` where needed (e.g. for badges and buttons).
- Defined roles implicitly and explicitly where needed (`role="list"` for tags mapping).
- Used `aria-live="polite"` on the countdown timer to keep screen readers updated safely.
- Explicit and custom `:focus-visible` ring on interactable elements to guarantee keyboard navigability.

### ✅ Mobile & Responsiveness

- Adheres to standard mobile viewport principles (100% width padded structure on small screens).
- Restricts layout gently to `max-width: 540px` on desktop layouts, fulfilling the relaxed, structured task requirement.
- Implements `flex-wrap` correctly so overflow never occurs within the tags grouping.

### Dynamics / Interactions

- **Live Countdown**: Computes dynamically on load using vanilla `Date` comparison logic and refreshes every 60 seconds smoothly.
- **Visual Checkbox**: Listens for state changes via `onChange` and applies visual changes natively to the card and its titles.
- **Console Methods**: Dummy events linked to buttons to verify interactability.

## Instructions

1. Clone or open this folder.
2. Run `index.html` within your preferred lightweight server or simply by double-clicking it to evaluate the render on a modern web-browser.
3. You can also view it in this [Live Demo](https://frontend-wizards-task-1.vercel.app/)
