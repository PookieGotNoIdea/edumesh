# EduMesh — NST Learning Hub

*A Community-Powered Learning and Student Productivity Platform*

## Project Overview

EduMesh is a full-stack web application designed to create a centralized, collaborative learning environment for NST students.

The platform brings together syllabus-specific learning resources, student-contributed notes, educational videos, practice questions, quizzes, and academic progress tracking in one place.

EduMesh encourages students to learn collaboratively by allowing students, seniors, and teachers to contribute useful academic resources and practice questions. These contributions can be reviewed and moderated to maintain the quality and reliability of the platform.

The application aims to make academic learning more organized, accessible, interactive, and community-driven.

## Problem Statement

Students often rely on multiple disconnected platforms and sources to find academic notes, tutorials, practice questions, and other learning materials. These resources may not be organized according to their university syllabus, making it difficult to identify relevant and reliable content.

Additionally, students lack a centralized system to practise questions, track their academic progress, identify weak topics, and learn from their mistakes.

EduMesh aims to address these challenges by providing a unified learning platform tailored to the academic requirements of NST students.

## Project Objectives

The primary objectives of EduMesh are to:

- Provide a centralized platform for accessing NST syllabus-specific learning resources.
- Encourage collaborative learning through student, senior, and teacher contributions.
- Maintain resource quality through a structured review and moderation process.
- Help students practise academic concepts through interactive quizzes and question sets.
- Track student performance, identify weak topics, and monitor learning progress.
- Improve the organization, accessibility, and discoverability of academic content.

## Core Features

### A. Learning Hub

- Organizes learning materials according to NST subjects and topics.
- Provides access to notes, educational videos, and external tutorials.
- Supports searching and filtering learning resources.
- Highlights the top three eligible YouTube videos for each topic based on resource ratings.

### B. Resource Contribution and Review

- Allows authorized contributors to submit learning resources.
- Associates submitted resources with relevant subjects and topics.
- Provides a moderation workflow for reviewing, approving, rejecting, or requesting changes to submissions.
- Supports updating or removing outdated resources.

### C. Ratings and Feedback

- Allows authenticated NST students to rate approved resources on a five-star scale.
- Supports comments, helpful votes, and resource reports.
- Displays resource ratings, rating counts, and rating distributions.
- Uses weighted ratings to rank resources more reliably.
- Supports sorting and filtering resources based on ratings and other relevant criteria.

### D. Practice System

- Provides multiple question formats, including MCQs, fill-in-the-blanks, and code-output questions.
- Supports topic-based and mixed-topic quizzes.
- Offers timed and untimed practice modes.
- Provides immediate feedback and detailed quiz results.
- Maintains quiz attempt history and performance analysis.
- Supports bookmarks, custom quizzes, and retrying incorrect questions.
- Allows authorized contributors to submit questions for moderation.

### E. Progress and Mistake History

- Maintains a history of incorrectly answered questions.
- Tracks topic-wise and subject-wise performance.
- Categorizes learning progress using statuses such as New, Needs Practice, Improving, and Mastered.
- Identifies weak topics and provides rule-based learning recommendations.
- Supports learning goals, streaks, and progress visualizations.

## Technology Stack

EduMesh follows a modern full-stack architecture with separate frontend and backend applications.

| Layer | Technology | Purpose |
|---|---|---|
| Frontend | React + Vite | User interface and development environment |
| Frontend language | JavaScript | Application logic |
| Routing | React Router | Client-side navigation |
| State management | React Context + Hooks | Shared application state |
| Styling | Tailwind CSS + Vanilla CSS | UI styling and layout |
| Form handling | React Hook Form + Zod | Form management and client-side validation |
| API communication | Axios | HTTP requests to backend APIs |
| Analytics | Recharts | Progress and performance visualizations |
| Backend | Node.js + Express.js | Server-side application and REST APIs |
| Backend language | JavaScript (ES Modules) | Backend application logic |
| ORM | Prisma ORM | Database access and management |
| Database | PostgreSQL | Relational data storage |
| Authentication | bcrypt + JWT | Password hashing and token-based authentication |

## System Architecture

EduMesh follows a **three-tier architecture**, separating the presentation layer, application layer, and data layer.

```text
                 ┌──────────────────────────┐
                 │     Presentation Layer   │
                 │                          │
                 │       React + Vite       │
                 │      Frontend Client     │
                 └────────────┬─────────────┘
                              │
                         REST APIs
                         JSON Data
                              │
                 ┌────────────▼─────────────┐
                 │     Application Layer    │
                 │                          │
                 │       Node.js            │
                 │       Express.js         │
                 │                          │
                 │  Routes / Controllers    │
                 │  Services / Validation  │
                 │  Middleware / Utilities │
                 └────────────┬─────────────┘
                              │
                         Prisma ORM
                              │
                 ┌────────────▼─────────────┐
                 │        Data Layer        │
                 │                          │
                 │       PostgreSQL         │
                 │     Relational Data      │
                 └──────────────────────────┘
```

### Frontend Architecture

The frontend is organized using a feature-based structure to keep related pages, components, and functionality together.

Key architectural decisions include:

- React with Vite for frontend development.
- React Router for application routing.
- React Context and Hooks for shared state management.
- Axios with a centralized configuration for backend communication.
- Feature-specific API services for organizing requests.
- Tailwind CSS and Vanilla CSS for styling.
- React Hook Form and Zod for form handling and client-side validation.
- Recharts for academic progress and performance analytics.

### Backend Architecture

The backend uses Node.js and Express.js with a modular, layered architecture.

The backend is organized around feature modules, with responsibilities separated into distinct layers:

- **Routes:** Define API endpoints and connect them to controllers.
- **Controllers:** Handle incoming requests and outgoing responses.
- **Services:** Contain application business logic.
- **Validation:** Validate incoming request data.
- **Middleware:** Handle authentication, authorization, errors, and other cross-cutting concerns.
- **Configuration:** Manage environment settings and database connectivity.
- **Utilities:** Provide reusable helper functions.

The backend exposes RESTful APIs that communicate with the frontend using JSON.

### Authentication and Authorization

EduMesh uses email-and-password authentication with:

- bcrypt for secure password hashing.
- JSON Web Tokens (JWT) for token-based authentication.
- Role-Based Access Control (RBAC) to manage permissions for different user roles.

The backend validates requests independently of frontend validation and uses centralized error handling to return consistent API error responses.

## Database Architecture

EduMesh uses **PostgreSQL** as its relational database and **Prisma ORM** for database access and schema management.

The database is designed around related entities to maintain data consistency and support the platform's learning and collaboration features.

Key database design principles include:

- Relational data modelling with appropriate primary and foreign keys.
- Clearly defined relationships between users, subjects, topics, resources, ratings, questions, quizzes, and progress records.
- Prisma schema management and database migrations.
- Referential integrity and appropriate constraints.
- Separation of database access from application business logic.

### Database Interaction Flow

```text
Express.js Application
        |
        v
   Prisma ORM
        |
        v
    PostgreSQL
        |
        v
   Query Results
        |
        v
  Express.js Response
```

## Repository Structure

EduMesh follows a monorepo structure containing independently organized frontend and backend applications, along with shared project documentation.

```text
edumesh/
│
├── frontend/                 # React + Vite application
│
├── backend/                  # Node.js + Express application
│   ├── src/
│   │   ├── config/
│   │   ├── modules/
│   │   ├── middleware/
│   │   ├── utils/
│   │   ├── app.js
│   │   └── server.js
│   │
│   ├── prisma/               # Prisma schema and migrations
│   ├── uploads/              # Local development file storage
│   └── tests/
│
├── docs/
│   ├── architecture/
│   ├── database/
│   ├── api/
│   └── planning/
│
├── .gitignore
└── README.md
```

### Project Organization

- **frontend/** contains the React application and its user interface.
- **backend/** contains the Express application, API modules, business logic, and database integration.
- **backend/prisma/** contains the Prisma schema and database migrations.
- **backend/uploads/** is intended for local development file storage. Uploaded files are excluded from Git.
- **docs/** contains architecture documentation, database design, API contracts, and project planning documents.
- **.gitignore** excludes dependencies, environment secrets, build outputs, logs, and uploaded files from version control.

The frontend and backend are maintained as separate applications while sharing the same Git repository and project documentation.

## Team Responsibilities

EduMesh is developed collaboratively by a team of two members.

| Team Member | Responsibility | Technology Focus |
|---|---|---|
| Member 1 | Backend and Database Development | Node.js, Express.js, Prisma ORM, PostgreSQL |
| Member 2 | Frontend Development | React, Vite, JavaScript, Tailwind CSS |

Both members collaborate on architecture decisions, API contracts, integration, testing, and project documentation.

## Development Roadmap

EduMesh is being developed in structured phases to ensure a clear development process and gradual integration of its components.

| Phase | Description | Status |
|---|---|---|
| Phase 1 | Project foundation, repository setup, and Git workflow | Completed |
| Phase 2 | Frontend and backend application initialization | Upcoming |
| Phase 3 | Database design, Prisma setup, and migrations | Planned |
| Phase 4 | API contracts and frontend-backend coordination | Planned |
| Phase 5 | Core feature development | Planned |
| Phase 6 | Frontend-backend integration and testing | Planned |
| Phase 7 | Deployment, documentation, and final presentation | Planned |

## Future Enhancements

The initial development focuses on the five core modules described above. Additional capabilities may be explored as future enhancements:

- **Student Productivity Planner:** Tools for organizing academic tasks and study schedules.
- **Study Sessions and Revision Tasks:** Features for planning and tracking revision activities.
- **AI-Powered Assistance:** Intelligent learning assistance and personalized academic support.

These enhancements are outside the initial core development scope.

## Getting Started

EduMesh is currently in its foundation and planning stage. Detailed installation instructions, environment configuration, and application startup commands will be added as the frontend and backend applications are initialized.

The project will maintain separate setup instructions for the frontend and backend.

## Project Information

- **Project Name:** EduMesh
- **Project Type:** Advanced Programming Full-Stack Web Application
- **Target Audience:** NST Students
- **Repository:** [EduMesh on GitHub](https://github.com/PookieGotNoIdea/edumesh)

---

*EduMesh — Learn Together. Grow Together.*

## Frontend Architecture

EduMesh uses **React with Vite** to build a modular, component-based frontend application. The frontend is organized by features to keep the codebase maintainable, scalable, and easy to navigate.

### Frontend Technologies

- **React:** Builds the user interface using reusable components.
- **Vite:** Provides the frontend development environment and build tooling.
- **React Router:** Handles navigation and routing between application pages.
- **React Context and Hooks:** Manage shared application state and reusable logic.
- **Tailwind CSS and Vanilla CSS:** Handle styling and responsive layouts.
- **Axios:** Communicates with the backend REST APIs.
- **React Hook Form and Zod:** Manage frontend forms and input validation.
- **Recharts:** Displays progress statistics and learning analytics.

### Component-Based Structure

The frontend follows a component-based approach. Common interface elements are built as reusable components to maintain consistency across different pages.

The application separates:

- **Pages and layouts:** Organize the main application screens and shared page structures.
- **Common components:** Provide reusable UI elements.
- **Feature modules:** Group components and logic according to application functionality.
- **Services:** Handle communication with backend APIs.
- **Hooks and utilities:** Store reusable application logic and helper functions.
- **Providers:** Manage shared application contexts.

### Routing and Navigation

React Router is used to manage navigation between different sections of EduMesh.

The application will support protected routes for authenticated users and role-based route access for different user permissions.

### State Management

EduMesh initially uses React Context and built-in React Hooks for shared and local state management.

This approach keeps state management simple while allowing the application to expand as new features are introduced.

## Frontend Feature Organization

EduMesh follows a feature-based frontend structure. Each major application functionality is organized into its own feature module, keeping related components and logic together.

### Feature Modules

- **Authentication (`auth`):** Handles student registration, login, authentication state, and protected access.
- **Learning Hub (`learning-hub`):** Organizes subjects, topics, learning materials, and educational resources.
- **Resources (`resources`):** Displays and manages contributed learning resources.
- **Reviews (`reviews`):** Supports resource feedback, comments, helpful votes, and reports.
- **Ratings (`ratings`):** Manages resource ratings and rating-related information.
- **Quizzes (`quizzes`):** Provides quiz interfaces, question answering, results, and quiz history.
- **Progress (`progress`):** Displays student performance, learning progress, and mistake history.
- **Notifications (`notifications`):** Displays notifications and unread notification information.

### Shared Frontend Organization

In addition to feature modules, the frontend contains shared directories for:

- **Common components:** Reusable interface elements.
- **Layouts:** Shared page layouts.
- **Services:** API communication and backend integration.
- **Hooks:** Reusable React logic.
- **Utils:** Helper functions.
- **App providers:** Shared application contexts and configuration.

This organization allows individual features to be developed and maintained independently while reusing common application functionality.

## Frontend and Backend API Integration

The EduMesh frontend communicates with the backend through REST APIs using JSON for request and response data.

### Axios Configuration

Axios is used as the HTTP client for backend communication.

A centralized Axios instance is maintained to configure common settings such as the backend base URL and request headers. This avoids repeating API configuration across different components.

### Feature-Based API Services

API communication is organized into feature-specific service files. Each service handles requests related to its respective module, such as authentication, resources, quizzes, progress, and notifications.

This separation keeps API logic independent of UI components and makes the application easier to maintain.

### Request and Response Handling

The frontend sends HTTP requests to the Express.js backend and processes JSON responses.

The application handles API errors and displays appropriate feedback to users.

### Form Validation

React Hook Form is used to manage frontend forms, while Zod provides schema-based validation.

Frontend validation improves the user experience by identifying invalid inputs before submission. The backend independently validates incoming requests and remains responsible for enforcing data integrity and business rules.

### Backend Communication

The backend processes API requests, interacts with PostgreSQL through Prisma ORM, and returns structured JSON responses to the frontend.

## Git Workflow and Team Collaboration

EduMesh is developed collaboratively using Git and GitHub. The repository follows a branch-based workflow to separate frontend development, backend development, and stable project releases.

### Main Branches

- **`main`:** Contains stable and verified project code.
- **`backend-dev`:** Used for backend and database development.
- **`frontend-dev`:** Used for frontend development.

### Feature Branches

Temporary branches are created for individual tasks and features.

The naming convention is:

- `feature/<area>-<module>-<task>`
- `fix/<area>-<module>-<task>`
- `chore/<area>-<task>`
- `docs/<topic>`

Examples:

- `feature/backend-auth-registration-api`
- `feature/frontend-auth-login-page`
- `docs/readme`

### Commit Convention

The project follows Conventional Commits:

`<type>(<scope>): <description>`

Common commit types include:

- `feat`: New functionality.
- `fix`: Bug fixes.
- `refactor`: Code restructuring.
- `docs`: Documentation changes.
- `test`: Tests.
- `chore`: Maintenance tasks.
- `style`: Formatting and styling changes.

### Team Responsibilities

The project is developed by two team members:

- **Backend development:** Responsible for Express.js, Prisma ORM, PostgreSQL, backend APIs, authentication, and business logic.
- **Frontend development:** Responsible for React, Vite, user interfaces, routing, frontend state management, and API integration.

### Integration and Testing

Frontend and backend work are developed independently and integrated through agreed API contracts.

Completed modules are integrated and tested before being merged into the stable `main` branch.

Both team members coordinate changes to shared documentation and project architecture.

## Getting Started

This section describes the initial setup of the EduMesh development environment.

### Prerequisites

The following tools are required:

- Node.js
- npm
- Git
- PostgreSQL
- A code editor such as Visual Studio Code

### Clone the Repository

Clone the project repository:

```bash
git clone https://github.com/PookieGotNoIdea/edumesh.git
cd edumesh
```

### Frontend Setup

Navigate to the frontend directory:

```bash
cd frontend
```

Install the frontend dependencies:

```bash
npm install
```

Create a local environment file using the provided `.env.example` as a reference, when available.

Start the Vite development server:

```bash
npm run dev
```

The terminal will display the local development URL.

### Backend Setup

Backend setup instructions will be added once the backend dependencies, environment configuration, database connection, and startup scripts have been implemented and verified.

### Environment Variables

Environment variables are used to configure application-specific settings.

Sensitive values, including database credentials, authentication secrets, and private API keys, must remain in local environment files and must never be committed to Git.

The repository provides `.env.example` files as configuration references where applicable.

## Project Information

**Project:** EduMesh — NST Learning Hub

**Project Type:** Advanced Programming Full-Stack Web Application

**Frontend:** React and Vite

**Backend:** Node.js and Express.js

**Database:** PostgreSQL with Prisma ORM

**Repository:** [EduMesh on GitHub](https://github.com/PookieGotNoIdea/edumesh)

EduMesh aims to create a centralized, community-powered learning platform that helps NST students access educational resources, practise concepts, and track their academic progress.