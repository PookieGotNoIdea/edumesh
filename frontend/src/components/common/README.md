# Common Components — Frontend

## 1. Folder Overview

The `common/` folder contains reusable React UI components that can be used across multiple sections of the EduMesh application.

These components provide common interface functionality and help maintain a consistent design throughout the platform.

They should be independent of individual EduMesh modules wherever possible.

## 2. Planned Folder Structure

```text
common/
│
├── README.md
│
├── Button.jsx
├── InputField.jsx
├── SelectField.jsx
├── TextAreaField.jsx
├── Modal.jsx
├── ConfirmDialog.jsx
├── LoadingSpinner.jsx
├── AlertMessage.jsx
├── EmptyState.jsx
└── Pagination.jsx
```

The listed files are examples of reusable components that may be created when required. They do not all need to be implemented immediately.

## 3. Component Responsibilities

| Component | Responsibility |
|---|---|
| `Button.jsx` | Reusable buttons for common interface actions |
| `InputField.jsx` | Reusable text and other input fields |
| `SelectField.jsx` | Reusable dropdown selection field |
| `TextAreaField.jsx` | Reusable multiline text input |
| `Modal.jsx` | Reusable modal dialog container |
| `ConfirmDialog.jsx` | Confirmation dialog for actions requiring user approval |
| `LoadingSpinner.jsx` | Displays a loading indicator |
| `AlertMessage.jsx` | Displays general success, error or informational messages |
| `EmptyState.jsx` | Displays a message when no content is available |
| `Pagination.jsx` | Provides reusable pagination controls |

Additional common components may be introduced when a genuine application-wide requirement exists.

## 4. Component Requirements

### A. Button

The reusable button should support:

- Button text or child content.
- Click handling.
- Different visual variants.
- Disabled state.
- Loading state where appropriate.
- Accessible button behaviour.

### B. Form Fields

Reusable form fields should support:

- Labels.
- Input values.
- Change handling.
- Placeholder text.
- Required and disabled states.
- Validation error messages.
- Appropriate input types.

React Hook Form and Zod should be used according to the approved form-validation architecture.

### C. Modal

The modal component should provide:

- Open and close behaviour.
- A content area.
- A suitable title where needed.
- Accessible interaction.
- Consistent application styling.

### D. Confirmation Dialog

The confirmation dialog should be suitable for actions that require explicit confirmation.

Examples include:

- Confirming deletion.
- Confirming removal of an item.
- Confirming other important user actions.

The component should provide clear confirm and cancel actions.

### E. Loading Spinner

The loading component should indicate that an operation is in progress.

It may be used during:

- API requests.
- Page loading.
- Form submission.
- Data processing.

### F. Alert Message

The alert component should display general feedback such as:

- Success messages.
- Error messages.
- Informational messages.
- Warning messages.

Feature-specific error handling should remain inside the relevant feature.

### G. Empty State

The empty-state component should provide a clear message when a section has no available content.

It may optionally display an illustration or an action relevant to the section using it.

### H. Pagination

The pagination component should provide reusable navigation between pages of data.

It should receive pagination information and event handlers through props rather than making API requests itself.

## 5. Props and Reusability Guidelines

Common components should receive configurable information through React props.

For example, a reusable button may accept:

| Prop | Purpose |
|---|---|
| `children` | Button content |
| `onClick` | Click event handler |
| `variant` | Visual style |
| `disabled` | Controls whether the button can be used |
| `type` | HTML button type |
| `isLoading` | Indicates an ongoing operation |

The exact props should be defined during component implementation.

Avoid creating separate common components for every small variation. Prefer configurable components when their behaviour and purpose are genuinely shared.

## 6. Element ID Guidelines

Important interactive elements should use descriptive and stable HTML IDs.

Examples:

| Component | Example ID |
|---|---|
| Common button | `btn-{action-name}` |
| Input field | `{field-name}` |
| Modal | `{modal-name}-modal` |
| Confirmation button | `btn-confirm-action` |
| Cancel button | `btn-cancel-action` |
| Loading indicator | `{section-name}-loading` |

When the same common component is rendered multiple times on one page, ensure that generated IDs remain unique.

Feature-specific element ID requirements should follow the relevant module's frontend documentation.

## 7. Development Guidelines

1. Keep only genuinely reusable UI components inside this folder.
2. Use PascalCase for React component filenames.
3. Keep component responsibilities focused.
4. Accept configurable data and behaviour through props.
5. Avoid including feature-specific business logic.
6. Do not make API requests directly from common UI components.
7. Keep styling consistent with the EduMesh design.
8. Support responsive layouts and accessible interaction.
9. Avoid unnecessary duplication.
10. Add components progressively as development requires them.

## 8. What Should Not Be Stored Here?

The following should remain in their respective feature folders:

| Component | Correct Location |
|---|---|
| `LoginForm.jsx` | `features/auth/` |
| `SignupForm.jsx` | `features/auth/` |
| `ResourceCard.jsx` | `features/learning-hub/` |
| `ResourceSubmissionForm.jsx` | `features/resources/` |
| `ReviewCard.jsx` | `features/reviews/` |
| `RatingStars.jsx` | `features/ratings/` |
| `QuizQuestion.jsx` | `features/quizzes/` |
| `MistakeCard.jsx` | `features/progress/` |
| `NotificationItem.jsx` | `features/notifications/` |

These components belong to specific EduMesh modules and should not be moved into the common folder simply because they contain reusable-looking UI elements.

## 9. Important Note

This folder defines the planned organization of shared UI components.

Actual React components will be created when required during frontend implementation.

The presence of this README does not mean that all listed components have already been implemented.
