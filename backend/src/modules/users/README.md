# User Management Module — users

## 1. Overview

The `users/` module handles user profile and account management functionality in the EduMesh application.

It is responsible for retrieving, managing and updating user information after an account has been created.

The module works alongside the authentication module but maintains a separate responsibility.

While authentication verifies a user's identity, user management handles the user's profile and account-related information.

## 2. Responsibilities

The `users/` module is responsible for:

- Retrieving user profile information.
- Updating user profile details.
- Managing user account information.
- Retrieving user-related information.
- Supporting user-specific application operations.
- Managing user data through Prisma ORM.
- Enforcing permissions for user-related operations.

## 3. Planned Folder Structure

```text
users/
│
├── README.md
├── users.routes.js
├── users.controller.js
├── users.service.js
└── users.validation.js
```

### File Responsibilities

| File | Responsibility |
|---|---|
| `README.md` | Documents user management architecture |
| `users.routes.js` | Defines user-related API endpoints |
| `users.controller.js` | Handles user-related HTTP requests and responses |
| `users.service.js` | Implements user management business logic |
| `users.validation.js` | Validates user-related request data |

Additional files may be introduced if required.

## 4. User Management Features

### 4.1 Retrieve User Profile

Allows authenticated users to retrieve their profile information.

Potential information includes:

- User ID.
- Name.
- Email address.
- Assigned role.
- Account creation date.
- Other approved profile information.

Sensitive information such as password hashes and authentication secrets must never be returned.

### 4.2 Update User Profile

Allows users to update permitted profile information.

Potential editable fields include:

- Name.
- Other approved profile details.

Email changes, if supported, must follow a separate verification and security process.

Users must not be allowed to modify privileged fields such as their role through ordinary profile updates.

### 4.3 User Information Retrieval

Provides user information required by other application features.

Only authorized information should be exposed through user-related operations.

## 5. Authentication and Authorization

The users module works with the shared authentication and authorization middleware.

Authentication ensures that the requesting user has a valid session.

Authorization determines whether the user is allowed to perform the requested operation.

### Access Rules

- Users must authenticate before accessing protected profile operations.
- Users may retrieve their own profile.
- Users may update only permitted fields of their own profile.
- Access to other users' information must follow explicit authorization rules.
- Privileged account operations must be restricted to authorized roles.

The backend must enforce all permissions independently of frontend navigation.

## 6. Proposed API Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/api/users/me` | Retrieve the current user's profile |
| PATCH | `/api/users/me` | Update the current user's permitted profile fields |
| GET | `/api/users/:userId` | Retrieve permitted information about a specific user, subject to authorization |

These endpoints are proposed and must be finalized during frontend-backend API contract coordination.

The current session endpoint `/api/auth/me` remains the responsibility of the authentication module.

## 7. Database Integration

The users module interacts with the User model defined in the Prisma schema.

Required database operations may include:

- Retrieving user records.
- Updating permitted profile fields.
- Checking whether a user exists.
- Retrieving approved user information.

Database operations will be implemented through Prisma Client inside the users service.

The module must never expose password hashes or other sensitive authentication data.

## 8. Validation

The proposed validation library is Zod.

User-related requests will be validated before business logic is executed.

Validation responsibilities include:

- Required fields.
- Valid field types.
- String length restrictions.
- Permitted editable fields.
- Rejection of unauthorized or unexpected fields.
- Validation of user identifiers.

Only explicitly permitted fields should be accepted during profile updates.

## 9. Error Handling

The users module must handle errors such as:

- User not found.
- Missing authentication.
- Unauthorized profile access.
- Invalid profile update data.
- Empty or invalid update requests.
- Database operation failures.

Error responses must not expose sensitive internal information.

## 10. Integration with Other Modules

The users module provides user-related information to other backend features.

Examples:

- The authentication module uses user records during login and registration.
- The resources module associates contributions with users.
- The reviews module identifies moderators.
- The ratings module identifies users who submit feedback.
- The quizzes module associates attempts with users.
- The progress module retrieves student-related performance data.
- The notifications module associates notifications with recipients.

Cross-module access should follow clear service boundaries and authorization requirements.

## 11. Frontend Integration

The users module communicates with the React frontend through REST APIs.

Frontend responsibilities include:

- Displaying profile information.
- Providing profile editing interfaces.
- Showing loading and error states.
- Updating displayed information after successful changes.

Backend responsibilities include:

- Retrieving profile data.
- Validating profile updates.
- Enforcing user permissions.
- Performing database operations.
- Returning consistent JSON responses.

Authenticated Axios requests must use `withCredentials: true`.

## 12. Development Workflow

User management implementation will follow these steps:

1. Review the User model in the Prisma schema.
2. Define permitted profile information.
3. Coordinate API contracts with the frontend developer.
4. Define profile validation rules.
5. Implement user-related routes.
6. Implement controllers.
7. Implement service-layer database operations.
8. Apply authentication and authorization middleware.
9. Test profile retrieval.
10. Test profile updates and permission restrictions.
11. Verify that sensitive information is not exposed.
12. Update documentation when necessary.

## 13. Security and Development Rules

- Never expose password hashes.
- Never allow ordinary profile updates to change privileged roles.
- Authenticate protected user operations.
- Enforce authorization on the backend.
- Allow updates only to explicitly permitted fields.
- Validate all incoming user data.
- Avoid exposing unnecessary personal information.
- Keep user management logic separate from authentication logic.
- Use Prisma Client for database operations.
- Maintain consistent API responses.

---

**EduMesh User Management Module**

Secure user profiles. Controlled account management. Protected user information.
