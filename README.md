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