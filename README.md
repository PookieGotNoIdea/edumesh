
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

## User Experience

EduMesh aims to provide a simple and organized experience for students.

The platform will focus on easy navigation, accessible learning materials and clear organization of academic content

## Resource Organization

Learning materials in EduMesh will be organized using an academic hierarchy.

- Subjects represent individual academic courses.
- Topics represent the chapters or concepts within subjects.
- Resources are associated with relevant topics.

This structure helps students locate materials related to specific syllabus topics.

## Resource Quality

EduMesh aims to encourage the sharing of useful and relevant academic resources.

Community ratings and reviews will help students understand the usefulness of available materials.

A review process will also help maintain the quality of published resources.

## Project Principles

EduMesh is guided by the following principles:

- Simplicity: Keep the platform easy to understand and use.
- Accessibility: Make academic resources easy to find.
- Collaboration: Encourage students to share knowledge.
- Organization: Maintain structured academic content.
- Reliability: Promote useful and relevant learning materials.

## Acknowledgements

We acknowledge the students, seniors and educators who contribute to academic knowledge sharing.

Their participation and feedback can help shape EduMesh into a useful learning platform for the NST student community.

## Project Category

EduMesh falls under the category of:

- Educational Technology
- Web-Based Learning Platform
- Collaborative Learning
- Academic Resource Management

## Platform Availability

EduMesh is planned as a web-based platform that students can access through a web browser.

The interface will be designed to provide a consistent experience across commonly used devices.

## Academic Content Organization

Educational content will follow a structured hierarchy:

- Academic subjects
- Individual topics
- Related learning materials
- Practice questions

This organization will help students navigate academic content more easily.

## Collaboration

EduMesh encourages collaboration within the NST academic community.

Students, seniors and teachers can contribute useful educational materials and help build a shared learning environment.

## Resource Discovery

EduMesh aims to simplify the process of finding relevant educational materials.

Students will be able to explore resources based on their subjects and topics, helping them locate content related to their academic requirements.

## Learning Assessment

The platform will include practice-based assessments to support student learning.

Students will be able to attempt different question types and review their performance to understand their learning progress.

## Student Productivity

EduMesh aims to support students in organizing their academic activities.

The productivity planner will provide options to create study tasks, assign priorities and track task completion.

## Content Moderation

EduMesh will include a resource review process to help maintain the quality of shared academic materials.

Submitted resources will be checked before being made available to other students.

## Expected Benefits

EduMesh aims to provide the following benefits:

- Easier access to academic materials.
- Better organization of study resources.
- Increased knowledge sharing among students.
- Easier discovery of useful educational videos.
- Structured practice and revision.
- Improved organization of study activities.

## Documentation

Project documentation will be maintained alongside the source code.

It will cover the system architecture, database design, development process and other important aspects of EduMesh.


## Project Summary

EduMesh brings academic resources and student learning activities together in one platform.

It focuses on making syllabus-related materials easier to access, explore and share within the NST community.

## Intended Audience

EduMesh is primarily intended for the NST academic community.

The platform focuses on students looking for study materials, seniors sharing their academic knowledge and teachers contributing educational resources.

## Subject-Wise Navigation

EduMesh will organize academic materials according to subjects and their respective topics.

This approach will help students navigate learning content based on the subjects they are currently studying.

## Learning Material Accessibility

EduMesh aims to provide a common place for accessing different academic resources.

Students will be able to explore available materials without having to search through multiple unrelated platforms.
## Community Feedback

Community feedback is an important part of EduMesh.

Students will be able to share their opinions about learning resources through ratings and reviews, helping others make informed choices.

## Academic Resource Relevance

EduMesh focuses on learning materials relevant to the NST academic syllabus.

Organizing resources around subjects and topics will help students find materials connected to their coursework.

## Practice Question Types

The practice system is planned to include:

- Multiple-choice questions.
- Fill-in-the-blank questions.
- Code-output prediction questions.

These question types will support practice across different academic concepts.

## Learning History

EduMesh will maintain records of student practice activities and quiz attempts.

This information will help students review their previous performance and identify topics that may require further revision.

## Study Task Organization

Students will be able to organize their study activities using tasks.

Tasks can include details such as:

- Task title.
- Related subject.
- Priority.
- Due date.
- Completion status.

## Development Approach

EduMesh will be developed incrementally.

The development process will focus on establishing the project structure, implementing core modules, integrating the database and testing individual functionalities before bringing the complete platform together.

## Platform Objectives

EduMesh aims to:

- Provide a common space for academic resources.
- Encourage knowledge sharing among NST students.
- Improve the organization of learning materials.
- Support regular practice and revision.

## Resource Contributions

EduMesh will allow members of the academic community to contribute useful learning materials.

Contributors will be able to submit relevant resources for review before they become available to other students.

## Topic-Based Learning

Learning materials will be associated with individual topics within academic subjects.

This structure will make it easier for students to find resources related to a particular concept or chapter.
## Resource Evaluation

Students will be able to provide ratings for shared learning resources.

These ratings will help the community understand which materials are considered useful by other learners.

## Educational Video Resources

EduMesh will support educational video links as part of its learning resource collection.

For individual topics, the platform aims to highlight the top three eligible YouTube videos based on student usefulness ratings.

## Study Task Priorities

The productivity planner will support task prioritization.

Students will be able to assign priorities to their study tasks to help organize their academic workload.

## Quiz Feedback

After attempting a quiz, students will be able to review their results.

The assessment system is intended to provide scores, correct answers and explanations to support better understanding of concepts.

## Revision Support

EduMesh aims to help students revisit topics that need additional practice.

Previous quiz attempts and incorrectly answered questions will provide useful information for planning revision activities.

## Consistency Goals

EduMesh aims to maintain consistency across its academic content.

Subjects, topics and learning resources will follow a structured organization to make information easier to navigate and maintain.
