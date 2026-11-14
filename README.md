# EduMesh
> A centralized learning and resource-sharing platform for NST students.
## About EduMesh

EduMesh is a centralized, college-specific learning platform designed for NST students.

It provides a common space where students, seniors and teachers can share educational resources such as notes, study materials, reference links and YouTube videos.

The platform helps students discover reliable and useful learning resources through community-based ratings and reviews, reducing the time spent searching across multiple websites.

EduMesh aims to make learning resources more accessible, organized and relevant to the college syllabus.
## Problem Statement

Students often struggle to find reliable, organized and syllabus-specific learning resources.

Study materials are scattered across different websites, YouTube channels, shared drives and messaging groups. Students may spend considerable time searching for appropriate notes, tutorials and practice materials without knowing which resources are actually helpful.

There is also a lack of a centralized platform where students can contribute resources and share their learning experiences.

EduMesh addresses these challenges by bringing learning materials together in one community-driven platform.

## Project Objectives

- Create a centralized learning platform specifically for NST students.
- Allow students, seniors and teachers to contribute educational resources.
- Organize resources according to subjects and topics.
- Enable students to rate and review the usefulness of shared resources.
- Display highly rated YouTube learning resources for individual topics.
- Provide a structured practice system for evaluating subject knowledge.
- Help students organize assignments, study tasks and revision schedules.
- Track quiz performance and identify topics that require additional practice.
  
## Core Features

### 1. Learning Hub
- Subject-wise and topic-wise organization.
- Access to notes, documents, reference links and videos.
- Community-contributed learning materials.

### 2. Resource Contribution and Moderation
- Students, seniors and teachers can submit resources.
- Review and approval workflow for submitted content.
- Management of published learning materials.

### 3. Resource Rating and Ranking
- Students can rate the usefulness of resources.
- Resource feedback and rating history.
- Display of the top three eligible YouTube resources for each topic.

### 4. Practice and Assessment
- Multiple-choice questions.
- Fill-in-the-blanks.
- Code-output prediction questions.
- Quiz scores, explanations and attempt history.

### 5. Student Productivity Planner
- Create and manage study tasks.
- Organize tasks by subject and topic.
- Set priorities and due dates.
- Track task completion.

### 6. Learning Progress
- View quiz performance.
- Identify frequently incorrect questions.
- Maintain practice and revision history.

## Technology Stack

| Technology | Purpose |
|---|---|
| HTML5 | Web page structure |
| CSS3 | Styling and layouts |
| JavaScript | Application functionality |
| React.js | Frontend development |
| Node.js | Backend runtime |
| Express.js | REST API development |
| PostgreSQL | Relational database |
| Prisma ORM | Database management |
| Git | Version control |
| GitHub | Source code hosting |

### Architecture

EduMesh follows a modular monolithic architecture.

The React frontend communicates with the Express.js backend through REST APIs. The backend handles application logic and database operations using Prisma ORM, while PostgreSQL stores the application's relational data.

### Database

PostgreSQL is used to maintain structured and relational data, including:

- User accounts and roles.
- Subjects and topics.
- Learning resources and reviews.
- Resource ratings.
- Quizzes and questions.
- Quiz attempts and answers.
- Student study tasks.

## Project Scope

EduMesh focuses on improving the learning experience of NST students through a centralized academic platform.

The initial version includes:

- Subject-wise and topic-wise learning resources.
- Community-based resource contributions and ratings.
- Resource review and moderation.
- Practice quizzes and assessment.
- Student task and study management.
- Quiz performance and mistake history.

### Future Scope

The following features may be considered in future versions:

- AI-assisted learning recommendations.
- Personalized study plans.
- Advanced learning analytics.
- Intelligent resource recommendations.

These features are not part of the initial implementation.

## Project Status

EduMesh is currently in the planning and initial development stage.

Core requirements, system architecture and database design are being planned before implementation.

## Target Users

EduMesh is intended for:

- NST students who want to access organized learning materials.
- Seniors who want to share useful academic resources.
- Teachers who want to contribute educational content.
- Reviewers and administrators who manage platform resources.

## Project Vision

Our vision is to create a common academic learning space where students can easily discover, share and evaluate educational resources relevant to their college syllabus.

## Project Mission

- Make academic resources easier to access.
- Encourage collaborative learning.
- Promote sharing of useful study materials.
- Help students identify reliable learning resources.
- Support structured practice and academic planning.

- ## Repository Structure

edumesh/
├── client/          # React frontend
├── server/          # Node.js and Express backend
├── docs/            # Project documentation
├── README.md
├── CONTRIBUTING.md
└── .gitignore

## Project Highlights

- College-focused learning platform.
- Organized academic resources.
- Community-driven resource sharing.
- Student-focused learning experience.
- Structured academic practice.

## Learning Resource Types

EduMesh aims to support different types of academic resources, including:

- PDF notes and documents.
- Reference websites.
- Educational YouTube videos.
- Subject-wise study materials.
- Practice questions.
