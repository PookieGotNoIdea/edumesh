# Backend Feature Modules — modules

## 1. Overview

The `modules/` directory contains the feature-specific implementation of the EduMesh backend.

Each module represents a major application feature and is responsible for handling its respective business logic, API operations, validation and database interactions.

EduMesh follows a feature-based modular architecture to keep related functionality organized and maintainable.

Instead of placing all controllers, services and validation files in separate global directories, related files are grouped according to their respective application features.

## 2. Responsibilities

The `modules/` directory is responsible for:

- Organizing backend functionality by application feature.
- Maintaining independent feature modules.
- Separating routes, controllers, services and validation logic.
- Managing feature-specific business rules.
- Handling feature-related database operations through Prisma.
- Supporting modular development and testing.
- Making the application easier to maintain and extend.

## 3. Planned Folder Structure

```text
modules/
│
├── README.md
│
├── auth/
│   └── README.md
│
├── users/
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

Each module will contain its own implementation files as development progresses.

## 4. Standard Module Architecture

Feature modules will follow a consistent internal organization wherever appropriate.

Example:

```text
auth/
│
├── README.md
├── auth.routes.js
├── auth.controller.js
├── auth.service.js
└── auth.validation.js
```

### File Responsibilities

| File | Responsibility |
|---|---|
| `README.md` | Documents the feature and its architecture |
| `auth.routes.js` | Defines feature-specific API endpoints |
| `auth.controller.js` | Handles HTTP requests and responses |
| `auth.service.js` | Contains feature-specific business logic |
| `auth.validation.js` | Validates incoming request data |

Additional files may be introduced when a feature requires them.

For example, complex modules may require separate helper functions, constants or specialized services.

## 5. Module Responsibilities

### 5.1 Authentication (`auth/`)

Handles:
- Student registration.
- User login and logout.
- Password hashing and verification.
- JWT generation and verification.
- Authentication-related operations.

### 5.2 Users (`users/`)

Handles:
- User profile management.
- Retrieving user information.
- Updating profile details.
- Account-related operations.

### 5.3 Learning Hub (`learning-hub/`)

Handles:
- Subject management.
- Topic management.
- Learning content organization.
- Retrieving subject and topic information.
- Connecting topics with learning resources.

### 5.4 Resources (`resources/`)

Handles:
- Resource submission.
- Resource retrieval.
- Resource editing where permitted.
- Contributor-related operations.
- Resource status management.

### 5.5 Reviews (`reviews/`)

Handles:
- Resource moderation.
- Reviewing submitted resources.
- Approving or rejecting submissions.
- Managing moderation feedback.
- Maintaining moderation records.

### 5.6 Ratings (`ratings/`)

Handles:
- Resource ratings.
- Comments and feedback.
- Helpful votes.
- Resource reporting.
- Rating calculations and rankings.

### 5.7 Quizzes (`quizzes/`)

Handles:
- Quiz management.
- Question management.
- Quiz generation.
- Quiz attempts.
- Answer evaluation.
- Quiz results and history.
- Incorrect-question retries.

### 5.8 Progress (`progress/`)

Handles:
- Student performance tracking.
- Subject and topic progress.
- Mistake history.
- Learning goals.
- Progress calculations.
- Learning recommendations.

### 5.9 Notifications (`notifications/`)

Handles:
- Notification creation.
- Retrieving notifications.
- Unread notification counts.
- Read and unread status management.
- Notification-related operations.

## 6. Separation of Responsibilities

Every module should maintain clear boundaries between different application responsibilities.

### Routes

Routes define the available API endpoints and connect them to their respective controllers.

### Controllers

Controllers handle incoming HTTP requests, extract required information and return appropriate HTTP responses.

Controllers should remain lightweight and should not contain complex business logic.

### Services

Services contain the actual business logic of the application.

They communicate with Prisma Client when database operations are required.

### Validation

Validation files define the rules for incoming request data.

Zod is the proposed validation library for validating request bodies, parameters and query strings.

Backend validation remains authoritative regardless of frontend validation.

## 7. Module Communication

Modules may interact with other modules when application functionality requires it.

Examples:

- The resources module may use information managed by the learning-hub module.
- The reviews module may update resource moderation status.
- The ratings module may retrieve resource information.
- The quizzes module may retrieve topic information.
- The progress module may use quiz attempt results.
- The notifications module may receive notification requests from other features.

Cross-module communication should maintain clear boundaries and avoid unnecessary dependencies.

## 8. Database Integration

Each module interacts with the database through Prisma ORM.

Feature-specific database queries should be maintained inside the appropriate service layer.

Examples:

- Authentication services interact with user records.
- Resource services manage resource records.
- Quiz services manage questions and attempts.
- Progress services retrieve and update progress information.

Database schema definitions and migrations remain centralized in the root `prisma/` directory.

## 9. API Integration

Each module is responsible for its feature-specific API endpoints.

The central route registration system connects individual module routers to the Express application.

API endpoint paths, request bodies, response structures, authentication requirements and authorization rules must be coordinated with the frontend developer before integration.

## 10. Development Principles

- Keep each module focused on one application feature.
- Maintain consistent internal file organization.
- Separate HTTP handling from business logic.
- Keep controllers lightweight.
- Maintain database operations inside appropriate services.
- Reuse shared middleware and utilities.
- Avoid unnecessary cross-module dependencies.
- Validate incoming requests.
- Enforce authorization at the backend level.
- Write tests for important business logic and API operations.
- Document significant changes to module responsibilities.

## 11. Development Workflow

Feature modules will be implemented in the following general order:

1. Understand the feature requirements.
2. Review its corresponding README.
3. Identify required database models and relationships.
4. Coordinate API contracts with the frontend developer.
5. Define validation requirements.
6. Implement routes.
7. Implement controllers.
8. Implement services and database operations.
9. Add authentication and authorization where required.
10. Test the feature independently.
11. Update documentation when necessary.

---

**EduMesh Backend Modules**

Feature-based architecture. Independent responsibilities. Organized business logic.
