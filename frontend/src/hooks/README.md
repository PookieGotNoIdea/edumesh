# Shared React Hooks — Frontend

## 1. Folder Overview

The `hooks/` folder contains reusable custom React hooks used across multiple parts of the EduMesh frontend.

Custom hooks allow us to reuse stateful logic and behaviour without repeating the same code in different components.

Examples of reusable functionality include:

- Detecting screen size.
- Managing reusable form behaviour.
- Handling common loading states.
- Managing debounced values.
- Tracking whether a component is mounted, where necessary.

This folder should contain only hooks that are genuinely shared across multiple features.

Hooks used by only one feature should remain inside that feature's own `hooks/` folder.

## 2. Planned Folder Structure

```text
hooks/
│
├── README.md
│
├── useDebounce.js
├── useMediaQuery.js
└── useDocumentTitle.js
```

This is a proposed initial structure. Additional shared hooks may be introduced when required.

Do not create every proposed hook immediately. Add a hook when there is a real requirement for it.

## 3. What Is a Custom React Hook?

A custom hook is a JavaScript function that uses React hooks to share reusable logic between components.

Custom hooks:

- Must follow React's Rules of Hooks.
- Must start with the word `use`.
- Can use built-in React hooks such as `useState`, `useEffect` and `useCallback`.
- Can return values and functions for components to use.
- Should focus on one reusable responsibility.

Example:

```jsx
import { useState } from "react";

function useToggle(initialValue = false) {
  const [value, setValue] = useState(initialValue);

  const toggle = () => {
    setValue((previousValue) => !previousValue);
  };

  return { value, toggle };
}

export default useToggle;
```

This is an illustrative example of a reusable custom hook. It does not need to be added unless the project has a genuine use for it.

## 4. Shared Hook Responsibilities

### A. useDebounce.js

Purpose: Provides a debounced value.

A debounced value updates only after a specified period of inactivity.

Possible use cases:

- Search input in the Learning Hub.
- Quiz discovery search.
- Other shared search interfaces.

The hook should accept a value and delay, then return the debounced value.

### B. useMediaQuery.js

Purpose: Allows components to respond to screen-size or media-query changes.

Possible use cases:

- Responsive navigation.
- Mobile and desktop layout behaviour.
- Shared responsive components.

The hook should return whether a specified media query currently matches.

### C. useDocumentTitle.js

Purpose: Provides a reusable way to update the browser document title.

Possible use cases:

- Updating the title when a page changes.
- Displaying the current section name.
- Maintaining consistent page titles.

## 5. Shared Hooks vs Feature-Specific Hooks

EduMesh separates shared hooks from feature-specific hooks.

| Hook Location | Responsibility | Example |
|---|---|---|
| `src/hooks/` | Reusable logic shared across features | `useDebounce.js` |
| `features/auth/hooks/` | Authentication-specific logic | `useAuth.js` |
| `features/quizzes/hooks/` | Quiz-specific logic | `useQuizAttempt.js` |
| `features/progress/hooks/` | Progress-specific logic | `useProgress.js` |
| `features/notifications/hooks/` | Notification-specific logic | `useNotifications.js` |

### Important Rule

Do not move a hook into the shared folder just because it is a custom hook.

It belongs in `src/hooks/` when multiple unrelated features can use it without depending on feature-specific business logic.

## 6. Hook Coding Conventions

All shared hooks should follow these conventions:

- Use JavaScript ES Modules.
- Use descriptive names beginning with `use`.
- Use camelCase for filenames and function names.
- Follow React's Rules of Hooks.
- Keep each hook focused on one responsibility.
- Avoid unnecessary state and effects.
- Include appropriate cleanup for subscriptions or event listeners.
- Avoid direct DOM manipulation unless genuinely required.
- Keep API requests inside the appropriate feature service layer.
- Do not place React components inside the hooks folder.
- Do not introduce unnecessary dependencies.

## 7. Error and State Handling

Hooks should handle their own reusable state logic where appropriate.

For example:

- A hook managing a debounced value should handle its update timing correctly.
- A media-query hook should respond to changes in the viewport.
- A document-title hook should update the title consistently.

Feature-specific loading, API error and business states should normally remain inside the corresponding feature hooks or components.

Shared hooks should not become a place for unrelated application logic.

## 8. Testing Checklist

Before considering a shared hook complete, verify:

- [ ] The hook has a clear reusable purpose.
- [ ] The hook follows React's Rules of Hooks.
- [ ] Its name begins with `use`.
- [ ] Its return value is clear and predictable.
- [ ] It works when used by multiple components.
- [ ] It handles relevant state changes correctly.
- [ ] Effects and event listeners are cleaned up where necessary.
- [ ] It does not contain feature-specific business logic.
- [ ] It does not duplicate existing shared functionality.

## 9. Development Guidelines

During frontend development:

- Create shared hooks only when a genuine reuse requirement appears.
- Keep feature-specific hooks inside their feature folders.
- Avoid creating hooks for logic that is simpler to keep inside one component.
- Reuse existing hooks before introducing duplicate implementations.
- Test hooks with the components that use them.
- Keep the implementation simple and maintainable.

---

**Hooks Folder Status:** Shared custom hook responsibilities, proposed hook examples and separation from feature-specific hooks documented. Actual hooks should be added when implementation requirements justify them.
