# App Folder — Frontend

## 1. Folder Overview

The `app/` folder contains application-level configuration and organization for the EduMesh frontend.

It manages how the overall React application is structured, initialized and connected.

This folder is responsible for coordinating application-wide functionality rather than implementing individual EduMesh modules.

The `app/` folder contains two main areas:

- `router/` — Application routes and route protection.
- `providers/` — Global React Context providers.

## 2. Folder Structure

```text
app/
│
├── README.md
│
├── router/
│   └── README.md
│
└── providers/
    └── README.md
```

Actual configuration and React files will be added when the application is initialized.

## 3. Folder Responsibilities

| Folder | Responsibility |
|---|---|
| `router/` | Defines application routes, navigation and route protection |
| `providers/` | Contains global React Context providers and application-wide state providers |

## 4. Application Routing

The router manages navigation between the different pages of EduMesh.

It should support:

- Login and registration pages.
- Student dashboard.
- Moderator dashboard.
- Learning Hub pages.
- Resource management pages.
- Quiz pages.
- Progress pages.
- Profile and notification pages.
- Protected routes for authenticated users.
- Role-based access to authorized pages.

The actual route definitions and access rules belong inside `router/`.

## 5. Global Providers

Global providers make shared application state and functionality available to components throughout EduMesh.

Examples include:

- Authentication state.
- Current authenticated user information.
- Theme state, if implemented.
- Other genuinely application-wide context.

Feature-specific state should remain within its relevant feature unless it needs to be shared application-wide.

## 6. Development Guidelines

1. Keep application-level configuration inside `app/`.
2. Keep route definitions inside `router/`.
3. Keep global React Context providers inside `providers/`.
4. Do not place individual feature pages or feature-specific business logic here.
5. Avoid duplicating state that already belongs to a feature.
6. Keep routing and provider responsibilities separate.
7. Follow the approved React Router and Context API architecture.

## 7. Important Note

This folder provides the application-level foundation for EduMesh.

It does not contain the implementation of individual functional modules such as Learning Hub, Quizzes or Progress Tracking.

Those modules are maintained separately inside `features/`.

The presence of this README does not mean routing or providers have already been implemented.
