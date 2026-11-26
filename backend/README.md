# EduMesh — Backend Development

## 1. Overview

The backend is responsible for powering the EduMesh application by managing business logic, database operations, authentication, authorization, API endpoints and communication with the frontend.

EduMesh (NST Learning Hub) is a Community-Powered Learning and Student Productivity Platform designed for NST students.

The backend provides the infrastructure required to support learning resources, student contributions, resource moderation, ratings, quizzes, progress tracking and notifications.

### Primary Responsibilities

- Handle client requests through REST APIs.
- Manage user registration, authentication and authorization.
- Process application business logic.
- Manage database operations using Prisma ORM.
- Store and retrieve application data from PostgreSQL.
- Validate incoming requests.
- Enforce role-based access control.
- Handle errors and API responses.
- Support frontend-backend integration.

## 2. Technology Stack

| Technology | Purpose |
|---|---|
| Node.js | JavaScript runtime environment |
| Express.js | Backend web framework |
| JavaScript | Backend programming language |
| ES Modules | JavaScript module system |
| PostgreSQL | Relational database |
| Prisma ORM | Database access and management |
| JWT | Authentication |
| bcrypt | Password hashing |
| Zod | Proposed request validation library |

Additional libraries will be introduced only when required by the application.

## 3. Backend Architecture

The backend follows a feature-based modular architecture with separation of responsibilities.

Each feature is maintained inside its own module, while shared backend functionality is maintained in dedicated directories.

### Architectural Principles

- **Modularity:** Organize code according to application features.
- **Separation of Concerns:** Keep routing, HTTP handling, business logic and database operations separate.
- **Reusability:** Maintain shared utilities and middleware.
- **Maintainability:** Keep the codebase organized and easy to extend.
- **Security:** Apply authentication, authorization and input validation.
- **Scalability:** Allow individual modules to evolve independently.

### Request Processing Flow

Client Request → Routes → Middleware → Controller → Service → Prisma ORM → PostgreSQL

The response is returned to the client through the controller.

## 4. Backend Folder Organization

The backend is organized into the following major directories:

| Directory | Responsibility |
|---|---|
| `prisma/` | Database schema, migrations and seed data |
| `src/` | Main backend application source code |
| `src/config/` | Environment and database configuration |
| `src/modules/` | Feature-specific backend modules |
| `src/middleware/` | Authentication, authorization, validation and error handling |
| `src/routes/` | Central API route registration |
| `src/utils/` | Reusable backend helper functions |
| `tests/` | Unit and integration tests |

Each directory has its own README documenting its purpose and responsibilities.

## 5. Feature Modules

The backend contains the following feature modules:

### 5.1 Authentication (`auth/`)

Responsible for:
- Student registration.
- User login and logout.
- Password hashing and verification.
- JWT generation and verification.
- Authentication-related operations.

### 5.2 Users (`users/`)

Responsible for:
- User profile management.
- Retrieving user information.
- Updating profile details.
- User account-related operations.

### 5.3 Learning Hub (`learning-hub/`)

Responsible for:
- Subject management.
- Topic management.
- Learning content organization.
- Retrieving resources associated with subjects and topics.

### 5.4 Resources (`resources/`)

Responsible for:
- Resource submission.
- Resource retrieval.
- Resource management.
- Contributor-related operations.
- Resource status management.

### 5.5 Reviews (`reviews/`)

Responsible for:
- Resource moderation.
- Reviewing submitted resources.
- Approving or rejecting submissions.
- Managing moderation feedback.

### 5.6 Ratings (`ratings/`)

Responsible for:
- Resource ratings.
- User feedback and comments.
- Helpful votes.
- Resource reporting.
- Rating calculations and rankings.

### 5.7 Quizzes (`quizzes/`)

Responsible for:
- Quiz management.
- Question management.
- Quiz generation.
- Quiz attempts.
- Answer evaluation.
- Quiz results and history.

### 5.8 Progress (`progress/`)

Responsible for:
- Student performance tracking.
- Topic and subject progress.
- Mistake history.
- Learning goals.
- Progress calculations and recommendations.

### 5.9 Notifications (`notifications/`)

Responsible for:
- Creating notifications.
- Retrieving notifications.
- Unread notification counts.
- Read and unread status management.

## 6. Authentication and Authorization

EduMesh uses JWT-based authentication with HTTP-only cookies.

### Authentication Rules

- Public registration is restricted to students.
- The backend automatically assigns the STUDENT role during public registration.
- Registration requires name, email and password.
- Minimum password length is 8 characters.
- Passwords are hashed using bcrypt.
- JWT is delivered through an HTTP-only cookie.
- JWT verification is handled by backend authentication middleware.
- Protected endpoints require authentication.

### Authorization

Role-based authorization controls access to protected operations.

The backend is responsible for enforcing permissions regardless of frontend navigation or visibility.

Final role permissions and cookie security configuration will be documented alongside the relevant implementation and API contracts.

## 7. Database Management

PostgreSQL is the primary relational database.

Prisma ORM is used for:

- Defining database models.
- Establishing model relationships.
- Performing database queries.
- Creating and applying migrations.
- Managing database operations.
- Seeding initial application data.

Database schema design and relationships will be documented and implemented inside the `prisma/` directory.

## 8. API Architecture

The backend exposes RESTful APIs to communicate with the React frontend.

API endpoints are organized according to application modules.

### Proposed API Organization

| Module | Proposed Base Endpoint |
|---|---|
| Authentication | `/api/auth` |
| Users | `/api/users` |
| Learning Hub | `/api/learning-hub` |
| Resources | `/api/resources` |
| Reviews | `/api/reviews` |
| Ratings | `/api/ratings` |
| Quizzes | `/api/quizzes` |
| Progress | `/api/progress` |
| Notifications | `/api/notifications` |

These are proposed API base paths. Final endpoints, request structures, response formats, validation rules and permissions must be agreed upon with the frontend developer before integration.

## 9. Error Handling and Validation

The backend follows centralized error-handling principles.

Responsibilities include:

- Validating incoming requests.
- Returning appropriate HTTP status codes.
- Providing consistent error responses.
- Handling database errors.
- Preventing sensitive information from leaking through error messages.
- Handling unexpected server errors.

Request validation will be implemented using the selected validation approach and will remain independent of frontend validation.

## 10. Testing Strategy

The backend will use two levels of testing.

### Unit Testing

Used to test individual functions and business logic independently.

Examples:
- Password validation.
- Authentication logic.
- Quiz answer evaluation.
- Progress calculations.

### Integration Testing

Used to test interactions between backend components.

Examples:
- Authentication API requests.
- Database operations.
- Resource submission workflows.
- Quiz attempt workflows.
- Authorization and protected routes.

Testing tools and configurations will be documented in the `tests/` directory.

## 11. Frontend Integration

The backend communicates with the React frontend through HTTP-based REST APIs.

### Integration Responsibilities

- Provide agreed API endpoints.
- Accept and validate frontend requests.
- Return consistent JSON responses.
- Support HTTP-only cookie authentication.
- Handle authenticated requests.
- Enforce user permissions.
- Provide appropriate error responses.

Axios requests requiring authentication must support credential-based cookie transmission.

Frontend and backend development will initially happen independently, followed by joint integration testing.

## 12. Development Workflow

Backend development follows this sequence:

1. Synchronize the backend development branch with the latest shared documentation.
2. Establish the backend folder structure.
3. Document folder responsibilities using README files.
4. Initialize the Node.js project.
5. Install and configure backend dependencies.
6. Configure Express.js.
7. Configure PostgreSQL and Prisma ORM.
8. Design and implement the database schema.
9. Establish shared middleware and API routing.
10. Implement feature modules individually.
11. Perform unit and integration testing.
12. Coordinate API contracts with the frontend developer.
13. Perform joint frontend-backend integration.
14. Commit and push completed work regularly.

## 13. Git Workflow

Repository: `PookieGotNoIdea/edumesh`

| Branch | Responsibility |
|---|---|
| `main` | Stable shared project |
| `backend-dev` | Backend development |
| `frontend-dev` | Frontend development |

### Commit Convention

Follow Conventional Commits:

`<type>(<scope>): <description>`

Examples:

- `docs(backend): add backend architecture documentation`
- `feat(auth): implement student registration`
- `feat(resources): add resource submission endpoint`
- `fix(quizzes): correct answer evaluation`
- `test(auth): add authentication integration tests`

Aim for at least five meaningful commits per development day whenever sufficient work is completed.

Never create empty or meaningless commits.

## 14. Development Scope

The initial backend implementation focuses on the following core features:

1. Authentication
2. User Management
3. Learning Hub
4. Resource Contribution
5. Resource Moderation
6. Ratings and Feedback
7. Quiz and Practice System
8. Progress Tracking
9. Notifications

Additional productivity and AI-powered functionality may be considered after the core application is completed.

## 15. Documentation Structure

The backend documentation is distributed across the following directories:

- `prisma/README.md` — Database and Prisma documentation.
- `prisma/migrations/README.md` — Migration documentation.
- `src/README.md` — Source code organization.
- `src/config/README.md` — Configuration documentation.
- `src/modules/README.md` — Feature module architecture.
- Individual module README files — Feature-specific documentation.
- `src/middleware/README.md` — Middleware documentation.
- `src/routes/README.md` — API routing documentation.
- `src/utils/README.md` — Shared utility documentation.
- `tests/README.md` — Testing strategy.
- `tests/unit/README.md` — Unit testing.
- `tests/integration/README.md` — Integration testing.

Each README provides detailed information about the responsibilities, planned files, dependencies and implementation approach of its respective directory.

---

**EduMesh Backend Development**

Documentation-first development. Modular architecture. Clean implementation. Reliable integration.
