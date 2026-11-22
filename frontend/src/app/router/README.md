# Router Folder — Frontend

## 1. Folder Overview

The `router/` folder contains the routing configuration for the EduMesh frontend application.

EduMesh uses React Router to manage navigation between application pages.

The routing system determines:

- Which page should be displayed for a particular URL.
- How users navigate between application modules.
- Which pages require authentication.
- Which pages are restricted to particular user roles.
- Where users should be redirected when they are not authorized to access a page.

All application route definitions and route-protection components should be maintained inside this folder.

## 2. Planned Folder Structure

```text
router/
│
├── README.md
│
├── AppRouter.jsx
├── ProtectedRoute.jsx
└── RoleRoute.jsx
```

The actual React files will be created during frontend initialization.

| File | Responsibility |
|---|---|
| `AppRouter.jsx` | Defines and organizes all application routes |
| `ProtectedRoute.jsx` | Restricts access to authenticated users |
| `RoleRoute.jsx` | Restricts access according to authorized user roles |

## 3. Application Routes

The following is the proposed initial page and route structure for EduMesh.

### A. Authentication

| Page | Route | Access |
|---|---|---|
| Login | `/login` | Public |
| Signup | `/signup` | Public |

### B. Student Dashboard

| Page | Route | Access |
|---|---|---|
| Student Dashboard | `/dashboard` | Authenticated student |

### C. Moderator Dashboard

| Page | Route | Access |
|---|---|---|
| Moderator Dashboard | `/moderation` | Authorized moderator |

### D. Learning Hub

| Page | Route | Access |
|---|---|---|
| Learning Hub | `/learning-hub` | Authenticated user |
| Subject Details | `/learning-hub/subjects/:subjectId` | Authenticated user |
| Topic Details | `/learning-hub/topics/:topicId` | Authenticated user |
| Resource Details | `/resources/:resourceId` | Authenticated user |

### E. Resource Contribution and Review

| Page | Route | Access |
|---|---|---|
| Submit Resource | `/resources/submit` | Authorized contributor |
| My Resources | `/my-resources` | Authenticated user |
| Moderator Review Details | `/moderation/resources/:resourceId` | Authorized moderator |

### F. Practice and Quiz System

| Page | Route | Access |
|---|---|---|
| Quiz Discovery | `/quizzes` | Authenticated student |
| Quiz Instructions | `/quizzes/:quizId` | Authenticated student |
| Quiz Attempt | `/quizzes/:quizId/attempt` | Authenticated student |
| Quiz Results and Analysis | `/quizzes/results/:attemptId` | Authenticated student |
| Quiz History | `/quiz-history` | Authenticated student |

### G. Progress Tracking

| Page | Route | Access |
|---|---|---|
| Progress Dashboard | `/progress` | Authenticated student |
| Subject Progress | `/progress/subjects/:subjectId` | Authenticated student |
| Mistake History | `/progress/mistakes` | Authenticated student |
| Learning Goals | `/progress/goals` | Authenticated student |

### H. Profile and Notifications

| Page | Route | Access |
|---|---|---|
| User Profile | `/profile` | Authenticated user |
| Notifications | `/notifications` | Authenticated user |

**Initial planning estimate: 22 primary pages/views.**

This is the proposed initial route map, not a final restriction on the number of routes. Additional detail routes or nested views may be introduced when module requirements are finalized.

Ratings and Feedback functionality will be integrated into relevant Learning Hub and Resource Details pages. It does not require separate primary pages at this stage.

## 4. Protected Routes

Some EduMesh pages must only be accessible after successful authentication.

`ProtectedRoute.jsx` should handle authenticated access.

### Expected Behaviour

- If the user is authenticated, allow access to the requested protected page.
- If the user is not authenticated, redirect them to `/login`.
- Preserve the originally requested URL where practical so the user can return after logging in.
- Handle the authentication loading state before making an access decision.

The frontend should obtain authentication information through the agreed authentication context.

The backend remains responsible for independently verifying authentication and authorization on protected API endpoints.

## 5. Role-Based Routes

EduMesh supports different user roles and permissions.

The initial role categories include:

- `STUDENT`
- `TEACHER`
- `CONTRIBUTOR`
- `MODERATOR`
- `ADMIN`

`RoleRoute.jsx` should control access to pages that require specific roles.

### Expected Behaviour

- Check the authenticated user's role.
- Allow access when the role satisfies the page's requirements.
- Prevent unauthorized users from accessing restricted pages.
- Redirect unauthorized users to an appropriate page or display an access-denied view.

### Examples

| Page | Intended Access |
|---|---|
| Student Dashboard | STUDENT |
| Quiz pages | STUDENT |
| Progress pages | STUDENT |
| Moderator Dashboard | MODERATOR and ADMIN, subject to final permissions |
| Moderator Review Details | MODERATOR and ADMIN, subject to final permissions |
| Resource Submission | Authenticated users with the appropriate contribution permission |

The exact permissions for teachers and contributors must be finalized in coordination with backend RBAC.

Hiding a page or button in the frontend is not a substitute for backend authorization.

## 6. Authentication and Navigation Flow

The routing system should support the following general flow:

1. An unauthenticated user opens EduMesh.
2. The user accesses the login or signup page.
3. After successful authentication, the frontend obtains the authenticated user's information.
4. A student is directed to `/dashboard`.
5. An authorized moderator is directed to `/moderation`.
6. Protected pages check authentication and required permissions.
7. On logout, the user is redirected to `/login`.

The authentication context is responsible for exposing the current authentication state. The router should not independently implement JWT handling.

## 7. Error and Fallback Routes

The routing system should handle invalid or inaccessible URLs.

Recommended behaviour:

- Unknown routes should display a Not Found page or suitable fallback.
- Unauthenticated access should redirect to login.
- Unauthorized access should display an appropriate access-denied state or redirect.
- Authentication loading should not cause incorrect redirects.

A dedicated Not Found page can be introduced when the application is initialized.

## 8. Development Guidelines

1. Use React Router for application navigation.
2. Keep route definitions inside `AppRouter.jsx`.
3. Keep authentication protection inside `ProtectedRoute.jsx`.
4. Keep role-based protection inside `RoleRoute.jsx`.
5. Do not place individual feature implementation inside the router folder.
6. Do not duplicate authentication logic in multiple route components.
7. Use the agreed authentication context to access the current user and authentication status.
8. Keep frontend route protection consistent with backend authorization rules.
9. Update the route documentation when new pages are approved.
10. Follow the EduMesh Frontend Guide for detailed page and module requirements.

## 9. Important Note

This folder defines the planned routing architecture of EduMesh.

The route list and access categories are initial design decisions and may be refined as backend permissions and module contracts are finalized.

Creating these routes does not mean the corresponding pages or backend APIs have already been implemented.
