# Utilities — Frontend

## 1. Folder Overview

The `utils/` folder contains reusable JavaScript helper functions and shared utilities used throughout the EduMesh frontend.

Utilities help avoid repeating common operations across different components and feature modules.

Examples include:

- Date and time formatting.
- Number formatting.
- String manipulation.
- Input formatting.
- Reusable validation helpers where appropriate.
- Shared application constants.
- Small data transformation functions.

Utility functions should be simple, reusable and focused on one responsibility.

## 2. Planned Folder Structure

```text
utils/
│
├── README.md
│
├── dateUtils.js
├── formatUtils.js
├── stringUtils.js
└── constants.js
```

This is a proposed initial structure. Additional files should be introduced only when there is a genuine requirement.

Do not create every proposed file immediately if the project does not need it yet.

## 3. Utility File Responsibilities

### A. dateUtils.js

Purpose: Contains reusable date and time helper functions.

Possible responsibilities:

- Formatting dates for display.
- Formatting timestamps.
- Handling date comparisons.
- Converting date values into readable formats.

Possible use cases:

- Quiz attempt dates.
- Resource submission dates.
- Notification timestamps.
- Progress history dates.

### B. formatUtils.js

Purpose: Contains general formatting functions.

Possible responsibilities:

- Formatting numerical values.
- Formatting percentages.
- Formatting rating values.
- Formatting counts and durations.

Possible use cases:

- Quiz scores.
- Progress percentages.
- Resource ratings.
- Dashboard statistics.

### C. stringUtils.js

Purpose: Contains reusable string-processing functions.

Possible responsibilities:

- Trimming unnecessary whitespace.
- Formatting display text.
- Handling capitalization.
- Normalizing strings for frontend display or comparison.

These helpers should not replace backend validation or security checks.

### D. constants.js

Purpose: Contains shared frontend constants that are used in multiple areas of the application.

Possible examples:

- Pagination defaults.
- Shared display labels.
- Common UI configuration values.
- Reusable frontend limits where agreed.

Do not store private credentials, backend secrets or sensitive configuration in this file.

Feature-specific constants should remain inside their corresponding feature folders unless they are genuinely shared.

## 4. Utility Coding Conventions

All utility files should follow these conventions:

- Use JavaScript ES Modules.
- Use descriptive function names.
- Use camelCase for filenames and function names.
- Use `export` to make reusable functions available.
- Keep functions focused on one responsibility.
- Avoid unnecessary dependencies.
- Avoid duplicating existing helper functions.
- Handle invalid or unexpected input appropriately.
- Add comments when the function's behaviour is not obvious.

Utility functions should generally be pure functions where possible.

A pure function produces the same output for the same input and does not modify external state.

## 5. Example Utility Function

Example: A reusable percentage formatter.

```javascript
export const formatPercentage = (value) => {
  if (typeof value !== "number" || !Number.isFinite(value)) {
    return "—";
  }

  return `${value.toFixed(1)}%`;
};
```

This function accepts a numerical value and returns a formatted percentage.

It also handles invalid numerical input.

This is an illustrative example and should only be added when required by the application.

## 6. Utilities vs Feature Logic

The `utils/` folder should contain general-purpose helper functions, not feature-specific application logic.

| Location | Responsibility | Example |
|---|---|---|
| `src/utils/` | Shared helper functions | Date formatting |
| `features/quizzes/` | Quiz-specific functionality | Quiz attempt handling |
| `features/progress/` | Progress-specific functionality | Progress data presentation |
| `features/ratings/` | Rating-specific functionality | Rating interface |
| `features/auth/` | Authentication functionality | Login and registration |

For example, formatting a date can be a shared utility.

However, calculating a student's official quiz score or deciding whether a topic is mastered belongs to the appropriate backend business logic.

## 7. Important Development Rules

- Do not place React components inside `utils/`.
- Do not use this folder for API requests.
- Do not place React hooks here.
- Do not store application state here.
- Do not implement backend business rules in frontend utilities.
- Do not duplicate feature-specific functions unnecessarily.
- Keep utilities independent of individual page components wherever possible.

## 8. Testing Checklist

Before considering a utility function complete, verify:

- [ ] The function has a clear purpose.
- [ ] The function can be reused where needed.
- [ ] The function handles expected input correctly.
- [ ] Invalid input is handled appropriately.
- [ ] The function does not unexpectedly modify external data.
- [ ] The function does not contain unnecessary dependencies.
- [ ] The function is not duplicating existing functionality.
- [ ] The function does not contain feature-specific business logic.

## 9. Development Guidelines

During frontend development:

- Add utilities when common logic needs to be reused.
- Check whether an equivalent utility already exists.
- Keep feature-specific helpers inside their feature folders.
- Prefer simple functions over unnecessary abstractions.
- Test helper functions with normal and edge-case inputs.
- Document complex helper behaviour when necessary.

---

**Utils Folder Status:** Shared utility responsibilities, proposed helper files, coding conventions and separation from feature-specific logic documented. Actual utility functions should be introduced as implementation requirements arise.
