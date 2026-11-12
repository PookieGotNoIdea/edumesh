# EduMesh System Architecture

EduMesh follows a modular monolithic architecture.

## Architecture Components

### 1. Frontend
- Developed using React.js.
- Provides the user interface.
- Handles navigation, forms and user interactions.
- Communicates with the backend through REST APIs.

### 2. Backend
- Developed using Node.js and Express.js.
- Handles application logic.
- Manages authentication and authorization.
- Processes resource submissions, ratings, quizzes and study tasks.

### 3. Database
- PostgreSQL stores application data.
- Prisma ORM manages database operations.
- Maintains relationships between users, subjects, resources, quizzes and tasks.

## Application Flow

1. The user interacts with the React frontend.
2. The frontend sends requests to the Express backend.
3. The backend validates requests and processes business logic.
4. Prisma communicates with PostgreSQL.
5. The backend returns the appropriate response to the frontend.
