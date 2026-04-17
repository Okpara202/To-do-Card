# Advanced Todo Card (Stage 1a)

**[🔥 View Live Demo](https://okparahng1.netlify.app/)** | **[💻 GitHub Repository](https://github.com/Okpara202/To-do-Card)**

This project extends the initial Stage 0 Todo Card into an interactive, stateful web component, thoroughly adhering to accessibility standards (WCAG) and fluid responsive design practices.

## What Changed from Stage 0 (How it Fulfills the Requirements)

The component has been significantly upgraded from a static UI to a dynamic, interactive state-driven module. Every requirement for Stage 1a has been met:

### 1. Interactive Edit Mode
- **What Changed:** Added an editing form `<div data-testid="test-todo-edit-form">` hidden by default. Clicking the `Edit` button transitions the card into Edit Mode.
- **Requirement Fulfilled:** The user can now update the title, description, priority, and due date. 
  - Allows saving updates or canceling to cleanly restore previous snapshot values.
  - Implements a sophisticated **focus trap** that keeps keyboard navigation strictly within the form when active, and gracefully returns focus back to the `Edit` button natively upon closing.

### 2. Status Controls & Bi-directional State
- **What Changed:** A `<select>` dropdown now controls the exact state of the task (`Pending`, `In Progress`, `Done`).
- **Requirement Fulfilled:** 
  - Valid logic: Marking a task as "Done" dynamically checks the footer `Mark as complete` toggle, strikes through the title contextually with muted styling, and halts the active due-date timer.
  - Unchecking "Mark as complete" seamlessly reverts the dropdown specific state back to "Pending".
  - Selecting "In Progress" correctly styles the card container with a distinct active-blue highlight.

### 3. Priority & Visual Accents
- **What Changed:** The component’s aesthetics actively respond to state object manipulation.
- **Requirement Fulfilled:** Toggling priority to `High` invokes a prominent red top-border and color badge, `Medium` yields warm-orange, and `Low` adapts muted gray UI. The class bindings actively update dynamically when changed via the Edit form.

### 4. Dynamic Time Management
- **What Changed:** Replaced boilerplate text with a `setInterval` loop calculating elapsed timestamp differences every 30 seconds.
- **Requirement Fulfilled:** Calculations handle and format accurate grammar outputting exactly `"Due in X hours"` and `"Due in X minutes"`. Once time mathematically expires, a flashing red **Overdue** badge renders securely and recolors ambient card-surfaces implicitly to a warning tone. Time stops recalculating fully when a task completes.

### 5. Expand & Collapse Behaviors
- **What Changed:** For excessively long strings of data, a text threshold checker toggles a collapse container module.
- **Requirement Fulfilled:** Any description exceeding `120` characters truncates visually with a gradient mask. Actively clicking the dynamic "Show more" button relies seamlessly on `aria-expanded="true/false"` ensuring visibility and complete screen reader notification mechanics.

### 6. Flawless Responsive Implementation
- **What Changed:** Modified breakpoints and flex wrapping limits natively accommodating extreme string inputs.
- **Requirement Fulfilled:** Design strictly scales securely across 320px mobile resolutions smoothly out to native 1024px+ desktop boundaries. The title safely uses `word-break` formatting without layout breaks, tags wrap safely, and importantly, Edit form elements intelligently collapse vertically exclusively onto responsive mobile frames minimizing layout breaks.

## New Design Decisions

1. **State-Driven Architecture (Vanilla JS):** Instead of isolated DOM manipulation everywhere, the logic centralizes using a vanilla JavaScript state object (`const state = { ... }`). A singular unified `applyState()` function is utilized sequentially propagating UI updates guaranteeing robust synchronization between the Checkbox matching what the Dropdown assumes.
2. **Snapshot Caching for UI Forms:** Cancel/rollback execution avoids messy conditional reverts simply by capturing profound deep-clones (`editSnapshot`). Restoring becomes incredibly swift.

## Known Limitations

- **Persistent Application Storage:** Because the component simulates front-end stage 1 requirements, the variables reset upon browser refresh. Next stages could adapt `localStorage` bindings to natively persist UI edits permanently.
- **Dates Input Restrictions:** Standard implementations of `datetime-local` elements dynamically lack min-date HTML blocking. Submitting dates located historically instantly triggers localized "Overdue" logic instead of rejecting input natively. 

## Accessibility Notes

- **Aria Roles and Live Regions:** `aria-live="polite"` binds successfully to real-time timer elements allowing standard screen readers to periodically inform contextually without randomly shouting timeline changes unprovoked to users.
- **Semantic For=>Id Mapping:** `<label for="[id]">` logic explicitly wraps every interactive user selection validating standard HTML Form semantics natively without reliance purely on nested visual text grouping.
- **Keyboard Tab Flow:** Traversal intelligently scopes sequentially moving accurately through specific components. Custom keydown events secure form submission contexts heavily assisting handicap accessibility.
