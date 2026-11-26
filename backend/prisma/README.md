# Prisma — Database Management

## 1. Overview

The `prisma/` directory contains the database-related configuration and resources used by the EduMesh backend.

EduMesh uses PostgreSQL as its relational database and Prisma ORM to interact with it.

Prisma provides a structured way to define database models, establish relationships, perform database operations and manage schema changes.

This directory is responsible for maintaining the database structure and tracking changes made to it throughout development.

## 2. Technology

| Technology | Purpose |
|---|---|
| PostgreSQL | Relational database management system |
| Prisma ORM | Database access and query management |
| Prisma Schema | Defines database models and relationships |
| Prisma Migrate | Manages database schema migrations |
| Prisma Client | Provides database access from JavaScript |

## 3. Responsibilities

The `prisma/` directory is responsible for:

- Defining the database schema.
- Creating and maintaining database models.
- Establishing relationships between models.
- Defining primary keys and foreign keys.
- Managing database migrations.
- Maintaining database constraints and indexes.
- Generating Prisma Client.
- Providing initial database seed data.
- Maintaining consistency between the application and database schema.

## 4. Planned Folder Structure

```text
prisma/
│
├── README.md
│
├── schema.prisma
│
├── migrations/
│   └── README.md
│
└── seed.js
```

### File Responsibilities

| File | Responsibility |
|---|---|
| `README.md` | Documents database architecture and management |
| `schema.prisma` | Defines database models, relationships and Prisma configuration |
| `migrations/` | Stores database schema migration history |
| `seed.js` | Inserts initial or development database records |

The actual schema and seed implementation will be added during database development.

## 5. Database Design

The EduMesh database will support the following major entities and application features:

- Users
- Subjects
- Topics
- Resources
- Resource Reviews and Moderation
- Ratings and Feedback
- Quiz Questions
- Quizzes
- Quiz Attempts
- Student Progress
- Learning Goals
- Notifications

Additional supporting models may be introduced when required.

### Database Design Principles

- Use appropriate primary keys and foreign keys.
- Establish meaningful relationships between models.
- Maintain data integrity through database constraints.
- Avoid unnecessary duplication of data.
- Use appropriate indexes for frequently queried fields.
- Apply suitable field types and default values.
- Maintain consistent naming conventions.
- Use enums where a fixed set of values is appropriate.

## 6. Model Relationships

The database will use relational associations to connect application entities.

Examples of planned relationships include:

- A user can contribute multiple resources.
- A subject can contain multiple topics.
- A topic can contain multiple learning resources.
- A resource can receive multiple ratings.
- A moderator can review multiple resource submissions.
- A quiz can contain multiple questions.
- A user can have multiple quiz attempts.
- A user can have multiple notifications.

The exact cardinality, optionality and referential actions will be finalized during database schema design.

## 7. Database Migrations

Prisma Migrate will be used to manage database schema changes.

Migrations provide a history of structural changes made to the database.

They help developers maintain consistent database structures across development environments.

Migration responsibilities include:

- Creating new database tables.
- Modifying existing columns.
- Establishing relationships.
- Adding indexes and constraints.
- Tracking schema changes.
- Applying migrations in the correct order.

All migration files must be maintained and committed to Git.

## 8. Database Seeding

The `seed.js` file will contain logic for inserting initial database records.

Potential seed data includes:

- Initial subjects.
- Topics associated with subjects.
- Development users.
- Sample learning resources.
- Sample quiz questions.

Seed data must be appropriate for the development environment.

Sensitive credentials must never be hardcoded into seed files.

## 9. Prisma Client

Prisma Client will be used by backend services to perform database operations.

It provides methods for:

- Creating records.
- Retrieving records.
- Updating records.
- Deleting records.
- Filtering and sorting records.
- Performing relational queries.
- Executing transactions.

Database operations should be performed through Prisma Client rather than writing unnecessary raw SQL queries.

## 10. Database Development Workflow

The database development process will follow these steps:

1. Identify application entities.
2. Define model attributes.
3. Establish model relationships.
4. Define primary keys and foreign keys.
5. Add constraints and indexes.
6. Implement the Prisma schema.
7. Generate Prisma Client.
8. Create database migrations.
9. Apply migrations to the development database.
10. Add initial seed data.
11. Test database operations.
12. Update documentation when the schema changes.

## 11. Important Development Rules

- The Prisma schema is the source of truth for the application's database model definitions.
- Every meaningful schema change must be tracked through migrations.
- Migration files must not be deleted or casually modified after being applied and shared.
- Database credentials must be stored in environment variables.
- Never commit actual `.env` files containing secrets.
- Use Prisma Client inside the appropriate backend services.
- Use transactions when multiple database operations must succeed or fail together.
- Test schema changes before integrating them into shared development environments.
- Coordinate database model changes with the backend and frontend API contracts.

## 12. Integration with Backend Modules

The Prisma database layer supports all backend feature modules.

| Backend Module | Database Responsibilities |
|---|---|
| `auth/` | User authentication records |
| `users/` | User profiles and account information |
| `learning-hub/` | Subjects and topics |
| `resources/` | Learning resource records |
| `reviews/` | Resource moderation records |
| `ratings/` | Ratings, feedback and reports |
| `quizzes/` | Quizzes, questions and attempts |
| `progress/` | Student performance and learning progress |
| `notifications/` | Notification records |

Feature-specific database operations will be implemented through the respective backend services.

---

**EduMesh Database Management**

PostgreSQL + Prisma ORM. Structured relationships. Controlled schema evolution.
