# EduMesh Frontend

## 1. Frontend Overview

The EduMesh frontend is responsible for providing the user interface and user experience of the EduMesh learning platform.

EduMesh is a community-powered learning and student productivity platform designed primarily for NST students.

The frontend will be developed using React and Vite with JavaScript.

It will allow students and other authorized users to access learning resources, contribute educational content, practise questions, track academic progress and interact with platform features.

The frontend communicates with the backend through REST APIs using Axios.

## 2. Frontend Technology Stack

| Technology | Purpose |
|---|---|
| React | Building reusable UI components |
| Vite | Frontend development environment and build tool |
| JavaScript | Application logic |
| JSX | Writing React components |
| React Router | Application navigation and routing |
| Context API | Managing shared application state |
| React Hooks | Managing component state and reusable logic |
| Axios | Communicating with backend APIs |
| Tailwind CSS | Utility-based styling |
| Vanilla CSS | Custom styling |
| React Hook Form | Managing forms |
| Zod | Frontend form validation |
| Recharts | Displaying progress charts and analytics |

The frontend should follow the approved technology stack. Additional libraries should not be introduced without discussing the requirement with the team.

## 3. Folder Structure

The frontend follows a feature-based folder organization.

```text
frontend/
│
├── README.md
│
├── public/
│   └── README.md
│
└── src/
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
    │   │   └── README.md
    │   ├── learning-hub/
    │   │   └── README.md
    │   ├── resources/
    │   │   └── README.md
    │   ├── reviews/
    │   │   └── README.md
    │   ├── ratings/
    │   │   └── README.md
    │   ├── quizzes/
    │   │   └── README.md
    │   ├── progress/
    │   │   └── README.md
    │   └── notifications/
    │       └── README.md
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

This is the planned frontend directory structure. Actual application files will be added progressively during development.

## 4. Folder Responsibilities

| Folder | Responsibility |
|---|---|
| `public/` | Static files such as favicon and public assets |
| `src/` | Main frontend source code |
| `src/app/` | Application-level configuration and organization |
| `src/app/router/` | Application routing and route protection |
| `src/app/providers/` | Global React context providers |
| `src/assets/` | Images, icons and imported assets |
| `src/components/` | Shared component organization |
| `src/components/common/` | Reusable UI components |
| `src/features/` | Individual EduMesh functional modules |
| `src/layouts/` | Shared application layouts |
| `src/services/` | Axios configuration and API services |
| `src/hooks/` | Reusable custom React hooks |
| `src/utils/` | Common helper functions |
| `src/styles/` | Global CSS and shared styling |

Detailed responsibilities are documented in the README file inside each respective folder.

## 5. Feature Organization

Each feature folder contains the components and logic associated with that functionality.

| Feature | Responsibility |
|---|---|
| `auth/` | Login, registration and authentication |
| `learning-hub/` | Subjects, topics and learning resources |
| `resources/` | Resource submission, editing and management |
| `reviews/` | Resource moderation and review workflow |
| `ratings/` | Ratings, comments, helpful votes and reports |
| `quizzes/` | Practice questions, quizzes, attempts and results |
| `progress/` | Progress tracking, performance and mistake history |
| `notifications/` | User notifications and notification interactions |

Feature-specific components should remain inside their respective feature folders.

Components used across multiple features should be placed inside `src/components/common/`.

## 6. Coding Conventions

Follow these naming and file organization conventions.

| Item | Convention | Example |
|---|---|---|
| React component filenames | PascalCase | `LoginForm.jsx` |
| JavaScript filenames | camelCase | `authService.js` |
| React components | PascalCase | `ProgressDashboard` |
| Variables and functions | camelCase | `fetchProgress()` |
| Constants | UPPER_SNAKE_CASE | `API_BASE_URL` |
| Folder names | kebab-case | `learning-hub/` |
| CSS class names | kebab-case | `resource-card` |
| Element IDs | kebab-case | `login-email` |

### File Extensions

- Use `.jsx` for React components.
- Use `.js` for regular JavaScript files.
- Use `.css` for CSS stylesheets.

### Element ID Guidelines

Important UI elements should have stable and descriptive HTML IDs.

Examples:

- `login-form`
- `login-email`
- `btn-login`
- `learning-hub-page`
- `resource-card-{resourceId}`
- `progress-dashboard-page`

IDs should be unique within the rendered page.

Follow the detailed element ID and component requirements documented in the EduMesh Frontend Guide.

## 7. API Integration Rules

The frontend communicates with the backend using REST APIs.

The following rules must be followed:

1. Use Axios for API communication.
2. Maintain a centralized Axios configuration.
3. Keep feature-specific API functions inside their respective service files.
4. Use JSON for standard API request and response bodies.
5. Use `withCredentials: true` for requests that require authentication cookies.
6. Never read the JWT from JavaScript.
7. Never store authentication tokens in localStorage or sessionStorage.
8. Handle loading, success, error and empty states.
9. Follow the agreed frontend-backend API contracts.

The frontend must use the backend as the source of truth for permissions, resource approval, quiz scoring and academic performance calculations.

## 8. Application Modules

EduMesh currently has five main functional modules:

1. Learning Hub
2. Resource Contribution and Review
3. Ratings and Feedback
4. Practice and Quiz System
5. Progress Tracking

Authentication and notifications support these modules as shared platform features.

The Student Productivity Planner and other future enhancements are not part of the initial core implementation scope.

## 9. Development Guidelines

1. Follow the approved frontend folder structure.
2. Keep feature-specific code inside its respective feature folder.
3. Keep reusable components inside `components/common/`.
4. Keep API communication inside the services layer.
5. Use React Context and hooks for shared application state.
6. Avoid unnecessary duplication of components and logic.
7. Do not manipulate the DOM directly when React state and event handling should be used.
8. Add new files and folders when required rather than creating unnecessary empty files in advance.
9. Use mock data when backend APIs are not yet ready.
10. Follow the EduMesh Frontend Guide for detailed module requirements and API contracts.

## 10. Documentation References

The following resources should be used during frontend development:

- **EduMesh — Divya's Frontend Guide:** Detailed frontend requirements for each module, including element IDs, React components, routes, API endpoints, validation and testing.
- **EduMesh GitHub Repository:** Source code, project documentation and shared API contracts.
- **Folder-specific README files:** Responsibilities and implementation guidance for individual frontend folders.

## 11. Development Workflow

The frontend is developed independently from the backend during the initial implementation phase.

- Frontend development takes place on the `frontend-dev` branch.
- Backend development takes place on the `backend-dev` branch.
- Both sides follow the shared API and component contracts.
- Divya independently tests frontend functionality.
- Backend and frontend are integrated and tested together when matching modules are ready.
- Successfully integrated work is incorporated into `main`.

## 12. Important Note

This is the planned frontend architecture and documentation reference.

The presence of a folder or README file does not mean that its functionality has already been implemented.

React components, pages, API services, styling and configuration files will be added progressively as frontend development advances.
