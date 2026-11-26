# Backend Source Code — src

## 1. Overview

The `src/` directory contains the main application source code for the EduMesh backend.

It includes the configuration, feature modules, middleware, API routes and reusable utilities required to run the backend application.

The source code is organized using a feature-based modular architecture with separation of responsibilities.

Each directory has a specific purpose and works together to provide the backend functionality.

## 2. Responsibilities

The `src/` directory is responsible for:

- Organizing backend application code.
- Managing application configuration.
- Implementing feature-specific business logic.
- Handling HTTP requests and responses.
- Managing API routing.
- Implementing authentication and authorization middleware.
- Providing reusable backend utilities.
- Connecting application modules with the Prisma database layer.

## 3. Planned Folder Structure

```text
src/
│
├── README.md
│
├── config/
│   └── README.md
│
├── modules/
│   ├── README.md
│   │
│   ├── auth/
│   ├── users/
│   ├── learning-hub/
│   ├── resources/
│   ├── reviews/
│   ├── ratings/
│   ├── quizzes/
│   ├── progress/
│   └── notifications/
│
├── middleware/
│   └── README.md
│
├── routes/
│   └── README.md
│
└── utils/
    └── README.md
```

The individual directories will contain their respective implementation files as development progresses.

## 4. Directory Responsibilities

### 4.1 config/

Contains application configuration files.

Responsibilities:
- Environment variable management.
- Database connection configuration.
- Centralized application configuration.

### 4.2 modules/

Contains feature-specific backend functionality.

Each module is responsible for a particular EduMesh feature.

Planned modules:

- `auth/` — Authentication and session management.
- `users/` — User profiles and account management.
- `learning-hub/` — Subjects, topics and learning content.
- `resources/` — Resource contribution and management.
- `reviews/` — Resource moderation.
- `ratings/` — Ratings and feedback.
- `quizzes/` — Quiz and practice functionality.
- `progress/` — Student performance and progress tracking.
- `notifications/` — Notification management.

Each module maintains its own routes, controllers, services and validation logic where required.

### 4.3 middleware/

Contains reusable Express middleware.

Responsibilities:
- Authentication.
- Role-based authorization.
- Request validation.
- Centralized error handling.
- Handling unavailable routes.

### 4.4 routes/

Contains the central API route registration.

Responsibilities:
- Registering feature-specific routes.
- Organizing API endpoints.
- Connecting module routers to the main Express application.
- Maintaining consistent API route prefixes.

### 4.5 utils/

Contains reusable helper functions and shared backend utilities.

Responsibilities:
- Common error handling utilities.
- Asynchronous request handling helpers.
- Shared response-related functionality where appropriate.
- Reusable application-level helper functions.

## 5. Backend Request Flow

The source code follows this general request-processing flow:

1. A client sends an HTTP request.
2. The corresponding route receives the request.
3. Middleware performs required checks.
4. The controller handles the HTTP request.
5. The service executes business logic.
6. Prisma Client performs required database operations.
7. The controller returns the appropriate response.

This structure ensures that routing, HTTP handling, business logic and database operations remain separate.

## 6. Coding Principles

The following principles must be maintained throughout backend development:

- Use ES Modules for JavaScript imports and exports.
- Keep modules focused on their respective responsibilities.
- Avoid unnecessary duplication of code.
- Keep controllers lightweight.
- Place business logic inside services.
- Use Prisma Client for database operations.
- Reuse shared middleware where appropriate.
- Follow consistent naming conventions.
- Handle asynchronous operations safely.
- Use centralized error handling.
- Avoid placing unrelated functionality inside a single file.

## 7. Naming Conventions

| Element | Convention | Example |
|---|---|---|
| Folders | kebab-case | `learning-hub/` |
| JavaScript files | camelCase or descriptive names | `auth.service.js` |
| Classes | PascalCase | `ApiError.js` |
| Functions | camelCase | `createUser()` |
| Constants | UPPER_SNAKE_CASE | `JWT_EXPIRES_IN` |
| Environment variables | UPPER_SNAKE_CASE | `DATABASE_URL` |

## 8. Integration with Prisma

The source code interacts with PostgreSQL through Prisma ORM.

Database-related operations should be handled by the appropriate feature services.

The Prisma configuration and schema are maintained separately in the root `prisma/` directory.

## 9. Development Workflow

Backend source code will be developed in the following order:

1. Configure the application environment.
2. Establish the database connection.
3. Configure the Express application.
4. Implement shared middleware.
5. Configure central API routes.
6. Implement authentication and user management.
7. Implement the remaining feature modules.
8. Connect services with Prisma Client.
9. Test individual modules.
10. Perform integration testing.

## 10. Development Rules

- Do not place all application logic inside `server.js` or `app.js`.
- Keep configuration separate from feature implementation.
- Maintain clear boundaries between controllers and services.
- Use middleware for reusable request-processing logic.
- Keep database queries inside appropriate services.
- Avoid circular dependencies between modules.
- Document significant architectural changes.
- Coordinate API contracts with the frontend developer.

---

**EduMesh Backend Source Code**

Modular development. Clear responsibilities. Maintainable application architecture.
