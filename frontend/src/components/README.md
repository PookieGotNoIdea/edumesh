# Components Folder — Frontend

## 1. Folder Overview

The `components/` folder organizes reusable React components used across the EduMesh frontend application.

These components provide common interface elements that can be shared by multiple pages and functional modules.

The purpose of this folder is to reduce code duplication, maintain consistent UI behaviour and make the application easier to maintain.

## 2. Planned Folder Structure

```text
components/
│
├── README.md
│
└── common/
    └── README.md
```

The `common/` folder contains reusable components that are not limited to one particular EduMesh feature.

Actual component files will be added as the frontend develops.

## 3. What Belongs in This Folder?

The components organization is intended for reusable interface elements.

Examples of components that may be shared across multiple features include:

- Buttons.
- Input fields.
- Form controls.
- Loading indicators.
- Modal dialogs.
- Confirmation dialogs.
- Reusable pagination controls.
- Empty-state displays.
- Error displays.
- Reusable badges.

A component should be placed in the common component area when it has a genuine use across different parts of the application.

## 4. Common Components vs Feature-Specific Components

It is important to distinguish between shared UI components and feature-specific components.

| Common Components | Feature-Specific Components |
|---|---|
| Reused across multiple features | Used primarily within one feature |
| Located inside `components/common/` | Located inside the relevant `features/` folder |
| Provide general UI functionality | Implement module-specific interface functionality |
| Should not contain unrelated feature business logic | May contain logic related to their own feature |

### Example: Common Components

- `Button.jsx`
- `InputField.jsx`
- `LoadingSpinner.jsx`
- `Modal.jsx`
- `Pagination.jsx`

### Example: Feature-Specific Components

- `LoginForm.jsx` inside `features/auth/`
- `ResourceCard.jsx` inside `features/learning-hub/`
- `QuizQuestion.jsx` inside `features/quizzes/`
- `MistakeCard.jsx` inside `features/progress/`

These are examples of possible component filenames, not files that must all be created immediately.

## 5. Component Design Guidelines

1. Build components with a clear and focused responsibility.
2. Use PascalCase for React component filenames and component names.
3. Use props to pass data and configuration into reusable components.
4. Avoid hard-coding feature-specific information into common components.
5. Keep components reusable without making them unnecessarily complicated.
6. Use React state and event handlers for interactive behaviour.
7. Maintain consistent styling across shared components.
8. Add appropriate element IDs to important interactive elements according to the EduMesh element ID conventions.

## 6. Styling Guidelines

Common components should follow the approved frontend styling approach:

- Tailwind CSS for utility-based styling.
- Vanilla CSS for custom styles when needed.
- Consistent spacing, typography and visual behaviour.
- Responsive layouts for different screen sizes.

Avoid duplicating the same styling rules across multiple components.

## 7. Important Development Rules

1. Keep reusable UI components inside `components/common/`.
2. Keep feature-specific components inside their respective feature folders.
3. Do not place page-level feature logic in common components.
4. Avoid creating multiple components that perform the same purpose.
5. Use props instead of duplicating similar components for slightly different data.
6. Add new shared components when a genuine reuse requirement exists.
7. Follow the EduMesh Frontend Guide for detailed component and element ID conventions.

## 8. Important Note

This folder defines the shared component organization for EduMesh.

Actual React components will be created progressively when required by the application.

The presence of this README does not mean that all listed components have already been implemented.
