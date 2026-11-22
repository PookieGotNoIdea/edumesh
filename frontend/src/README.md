# Source Code — Frontend

## 1. Folder Overview

The `src/` folder contains the main source code of the EduMesh frontend application.

All React components, application logic, feature modules, API services, custom hooks, utilities and styles will be organized inside this folder.

The source code follows a feature-based architecture to keep the application modular, maintainable and easy to develop.

## 2. Folder Structure

```text
src/
│
├── README.md
│
├── app/
│   ├── README.md
│   ├── router/
│   │   └── README.md
│   └── providers/
│       └── README.md
│
├── assets/
│   └── README.md
│
├── components/
│   ├── README.md
│   └── common/
│       └── README.md
│
├── features/
│   ├── README.md
│   ├── auth/
│   ├── learning-hub/
│   ├── resources/
│   ├── reviews/
│   ├── ratings/
│   ├── quizzes/
│   ├── progress/
│   └── notifications/
│
├── layouts/
│   └── README.md
│
├── services/
│   └── README.md
│
├── hooks/
│   └── README.md
│
├── utils/
│   └── README.md
│
└── styles/
    └── README.md
```

## 3. Folder Responsibilities

| Folder | Responsibility |
|---|---|
| `app/` | Application-level configuration and organization |
| `assets/` | Imported images, icons and other application assets |
| `components/` | Shared component organization |
| `features/` | Individual EduMesh functional modules |
| `layouts/` | Shared application layouts |
| `services/` | Axios configuration and API communication |
| `hooks/` | Reusable custom React hooks |
| `utils/` | Common helper functions |
| `styles/` | Global CSS and shared styling |

Each folder has its own README file explaining its responsibilities and the type of files that belong there.

## 4. Feature-Based Organization

EduMesh uses feature-based organization to keep related functionality together.

The `features/` folder contains the individual application modules.

| Feature | Responsibility |
|---|---|
| `auth/` | Login, registration and authentication |
| `learning-hub/` | Subjects, topics and learning resources |
| `resources/` | Resource submission and management |
| `reviews/` | Resource moderation and review |
| `ratings/` | Ratings, comments, helpful votes and reports |
| `quizzes/` | Practice questions, quizzes and results |
| `progress/` | Performance tracking and mistake history |
| `notifications/` | User notifications |

Feature-specific components, pages, hooks and service files should remain inside their respective feature folders wherever practical.

## 5. Code Organization Guidelines

### React Components

- Store React components in the folder responsible for their functionality.
- Use `.jsx` for React component files.
- Use PascalCase for component filenames.
- Keep components focused on clear responsibilities.
- Reuse common components instead of duplicating UI code.

### JavaScript Logic

- Use `.js` for regular JavaScript files.
- Use camelCase for functions and variables.
- Keep reusable logic in appropriate hooks or utility files.
- Avoid placing unrelated application logic in a single file.

### API Communication

- Keep API communication inside the services layer or the relevant feature service files.
- Use the centralized Axios configuration.
- Follow the agreed frontend-backend API contracts.

### Styling

- Use Tailwind CSS and Vanilla CSS according to the approved frontend stack.
- Keep global styling inside `styles/`.
- Keep component-specific styling close to the relevant component when appropriate.
- Use descriptive kebab-case CSS class names.

## 6. Important Development Rules

1. Keep the source code organized according to the approved folder structure.
2. Do not mix unrelated feature logic.
3. Keep reusable UI components inside `components/common/`.
4. Keep feature-specific components inside their respective feature folders.
5. Use React Context and hooks for shared application state where appropriate.
6. Avoid unnecessary duplication.
7. Do not directly manipulate the DOM when React state and event handling should be used.
8. Add files and folders as development progresses rather than creating unnecessary empty files.
9. Follow the detailed EduMesh Frontend Guide for module-specific requirements.

## 7. Important Note

This is the planned source-code organization for EduMesh.

The folders will gradually contain actual React components, JavaScript files, API services, hooks and styles during frontend development.

The presence of a README file does not mean that the corresponding functionality has already been implemented.
