# Features Folder — Frontend

## 1. Folder Overview

The `features/` folder contains the individual functional modules of the EduMesh frontend application.

EduMesh follows a feature-based architecture. Each feature has its own components, pages, hooks, services and other functionality wherever required.

This organization keeps related code together and makes individual modules easier to develop, test, maintain and integrate with the backend.

## 2. Planned Folder Structure

```text
features/
│
├── README.md
│
├── auth/
│   └── README.md
│
├── learning-hub/
│   └── README.md
│
├── resources/
│   └── README.md
│
├── reviews/
│   └── README.md
│
├── ratings/
│   └── README.md
│
├── quizzes/
│   └── README.md
│
├── progress/
│   └── README.md
│
└── notifications/
    └── README.md
```

Each feature folder will contain its own implementation files as development progresses.

## 3. Feature Responsibilities

| Feature | Responsibility |
|---|---|
| `auth/` | User login, registration and authentication-related interface functionality |
| `learning-hub/` | Subjects, topics, learning resources, search and filtering |
| `resources/` | Resource submission, editing and personal resource management |
| `reviews/` | Resource moderation, review queues and approval workflow |
| `ratings/` | Resource ratings, comments, helpful votes and reports |
| `quizzes/` | Quiz discovery, questions, attempts, results and quiz history |
| `progress/` | Academic performance, progress tracking, mistake history and learning goals |
| `notifications/` | Notification display, unread count and notification interactions |

## 4. Feature Folder Organization

Each feature should keep its related implementation together.

A feature may contain the following types of files when required:

| File / Folder | Purpose |
|---|---|
| `components/` | React components specific to the feature |
| `pages/` | Page-level React components |
| `hooks/` | Feature-specific custom React hooks |
| `services/` | API functions related to the feature |
| `utils/` | Helper functions specific to the feature |
| `README.md` | Feature documentation and implementation reference |

Not every feature needs every folder. Create only the files and folders that are genuinely required.

## 5. Example Feature Structure

The following is an example of how a feature may be organized.

```text
learning-hub/
│
├── README.md
│
├── components/
│   ├── SubjectCard.jsx
│   ├── TopicCard.jsx
│   └── ResourceCard.jsx
│
├── pages/
│   ├── LearningHubPage.jsx
│   ├── SubjectDetailsPage.jsx
│   └── TopicDetailsPage.jsx
│
├── hooks/
│
├── services/
│   └── learningHubService.js
│
└── utils/
```

This is an organizational example, not a requirement to create all these files immediately.

The actual structure should depend on the feature's implementation needs.

## 6. Feature Independence

Each feature should manage its own functionality as much as possible.

For example:

- Authentication UI belongs in `auth/`.
- Learning resource browsing belongs in `learning-hub/`.
- Resource submission belongs in `resources/`.
- Moderation interfaces belong in `reviews/`.
- Rating and feedback interfaces belong in `ratings/`.
- Quiz functionality belongs in `quizzes/`.
- Academic performance interfaces belong in `progress/`.
- Notification interfaces belong in `notifications/`.

Features may communicate through shared application state, common components and backend APIs where required.

Avoid placing unrelated feature logic inside another feature's folder.

## 7. Common Components vs Feature Components

| Common Components | Feature Components |
|---|---|
| Used across multiple application areas | Used primarily within one feature |
| Stored in `src/components/common/` | Stored inside the relevant feature |
| Provide general UI functionality | Provide module-specific functionality |

For example:

- `Button.jsx` belongs in `components/common/`.
- `QuizQuestion.jsx` belongs in `features/quizzes/`.
- `LoginForm.jsx` belongs in `features/auth/`.
- `MistakeCard.jsx` belongs in `features/progress/`.

## 8. Backend Integration

Each feature should communicate with the backend through its relevant service functions.

Development guidelines:

1. Use the centralized Axios configuration.
2. Keep feature-specific API functions organized in the relevant service files.
3. Follow the agreed API endpoint and JSON contracts.
4. Handle loading, success, error and empty states.
5. Use mock data while the corresponding backend APIs are under development.
6. Do not independently implement backend responsibilities in the frontend.
7. Follow the detailed frontend-backend integration documentation.

## 9. Development Workflow

The frontend features will be developed progressively.

For each feature:

1. Review its requirements in the EduMesh Frontend Guide.
2. Review the relevant feature README.
3. Follow the agreed component IDs and API contracts.
4. Implement the interface and feature-specific logic.
5. Use mock data if the backend is not ready.
6. Test the frontend functionality independently.
7. Commit and push completed work to `frontend-dev`.
8. Perform joint frontend-backend integration when the corresponding backend module is ready.

## 10. Important Note

This folder defines the planned organization of EduMesh's functional frontend modules.

The eight feature folders represent the current planned frontend organization. They do not all need to be implemented simultaneously.

Actual React components, pages, hooks and API services will be added progressively.

The presence of a README file does not mean that the corresponding feature has already been implemented.
