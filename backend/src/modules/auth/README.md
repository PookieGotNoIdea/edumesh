# Authentication Module — auth

## 1. Overview

The `auth/` module handles authentication-related functionality for the EduMesh application.

It manages student registration, user login, logout, password verification, JWT generation and authentication-related operations.

The module ensures that users can securely access the platform and that protected backend resources are accessible only to authenticated users.

EduMesh uses JWT-based authentication with HTTP-only cookies.

## 2. Responsibilities

The authentication module is responsible for:

- Student registration.
- User login.
- User logout.
- Password hashing using bcrypt.
- Password verification.
- JWT generation and verification.
- Authentication-related database operations.
- Managing authentication cookies.
- Supporting session restoration.
- Providing authentication functionality to protected backend routes.

## 3. Planned Folder Structure

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
| `README.md` | Documents authentication architecture |
| `auth.routes.js` | Defines authentication API endpoints |
| `auth.controller.js` | Handles authentication requests and responses |
| `auth.service.js` | Implements authentication business logic |
| `auth.validation.js` | Validates registration and login input |

Shared authentication middleware will be maintained separately in `src/middleware/`.

Additional files may be introduced if authentication functionality requires them.

## 4. Authentication Features

### 4.1 Student Registration

Allows new students to create an EduMesh account.

Registration requirements:

- Name.
- Email address.
- Password.

Registration rules:

- Public registration is restricted to students.
- The backend automatically assigns the STUDENT role.
- Minimum password length is 8 characters.
- Email addresses must be validated.
- Duplicate email registrations must be rejected.
- Passwords must be hashed using bcrypt before database storage.

Users must never be allowed to assign themselves privileged roles through public registration.

### 4.2 User Login

Allows registered students to authenticate using their credentials.

Login process:

1. Receive email and password.
2. Validate the incoming request.
3. Find the corresponding user.
4. Verify the supplied password against the stored password hash.
5. Generate a JWT after successful authentication.
6. Deliver the JWT through an HTTP-only cookie.
7. Return appropriate user information.

Invalid credentials must produce an appropriate error response.

### 4.3 User Logout

Allows authenticated users to end their current session.

Logout responsibilities:

- Clear the authentication cookie.
- Apply compatible cookie-clearing options.
- Return an appropriate logout response.

### 4.4 Session Restoration

Allows the frontend to determine whether a user already has an authenticated session.

The backend verifies the authentication cookie and returns the authenticated user's information.

The frontend will use this functionality when restoring authentication state after a page refresh.

## 5. Authentication Architecture

EduMesh uses JSON Web Tokens (JWT) for authentication.

### Authentication Flow

1. The user submits login credentials.
2. The backend validates the credentials.
3. The backend generates a JWT.
4. The JWT is delivered through an HTTP-only cookie.
5. The browser automatically includes the cookie in eligible requests.
6. Authentication middleware verifies the JWT.
7. The backend identifies the authenticated user.
8. The requested protected operation is processed.

The frontend must not access the JWT directly.

## 6. Password Security

Passwords are hashed using bcrypt before being stored in PostgreSQL.

Security requirements:

- Never store plain-text passwords.
- Never return password hashes in API responses.
- Verify passwords using bcrypt comparison functionality.
- Never log passwords.
- Validate passwords before processing registration.
- Keep password-related operations inside the authentication service.

## 7. JWT and Cookie Management

JWT authentication will use HTTP-only cookies.

### Security Requirements

- JWT must be signed using a secret stored in environment variables.
- JWT expiration must be configured.
- Cookies must use the HTTP-only attribute.
- Secure cookie settings must be configured appropriately for the deployment environment.
- SameSite settings must be coordinated with frontend deployment requirements.
- Cookie clearing during logout must use compatible cookie options.
- The frontend must not store authentication tokens in localStorage or sessionStorage.

Final cookie settings, expiration policies and CSRF protections must be coordinated before deployment.

## 8. Proposed API Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/api/auth/register` | Register a new student |
| POST | `/api/auth/login` | Authenticate a user |
| GET | `/api/auth/me` | Retrieve the current authenticated user |
| POST | `/api/auth/logout` | End the authenticated session |

These are proposed endpoints and must be finalized through frontend-backend API contract coordination.

## 9. Authentication Middleware Integration

The authentication module works with shared middleware located in:

`src/middleware/`

The authentication middleware is responsible for:

- Reading the authentication cookie.
- Verifying the JWT.
- Identifying the authenticated user.
- Attaching authenticated user information to the request.
- Rejecting requests with missing or invalid authentication.

Role-based authorization will be handled by the appropriate shared authorization middleware.

## 10. Database Integration

The authentication module interacts with the User model defined in the Prisma schema.

Required database operations include:

- Finding users by email.
- Creating new student accounts.
- Retrieving authenticated user information.
- Checking account existence.
- Preventing duplicate registrations.

Database operations will be implemented through Prisma Client inside the authentication service.

## 11. Validation

The proposed validation library is Zod.

Incoming registration and login requests will be validated before authentication business logic is executed.

Validation responsibilities include:

- Required fields.
- Valid email format.
- Minimum password length.
- Appropriate field types.
- Rejection of unexpected or invalid input where applicable.

Backend validation remains authoritative regardless of frontend validation.

## 12. Error Handling

The authentication module must handle errors such as:

- Missing registration fields.
- Invalid email format.
- Password shorter than the required minimum.
- Duplicate email registration.
- Incorrect login credentials.
- Missing authentication cookie.
- Invalid JWT.
- Expired JWT.
- Unauthorized access.

Sensitive information must not be exposed through error responses.

## 13. Frontend Integration

The authentication module communicates with the React frontend through REST APIs.

The frontend developer is responsible for:

- Registration and login interfaces.
- Form validation.
- Authentication Context.
- Protected routes.
- Session restoration.
- Logout interactions.

The backend is responsible for:

- Credential verification.
- Password hashing.
- JWT generation and verification.
- HTTP-only cookie management.
- User identification.
- Authentication enforcement.

Axios requests requiring authentication must use `withCredentials: true`.

## 14. Development Workflow

Authentication implementation will follow these steps:

1. Finalize the User database model.
2. Establish password hashing functionality.
3. Implement registration validation.
4. Implement student registration.
5. Implement login and credential verification.
6. Implement JWT generation.
7. Configure HTTP-only cookies.
8. Implement logout.
9. Implement the authenticated user endpoint.
10. Integrate authentication middleware.
11. Test successful and unsuccessful authentication scenarios.
12. Coordinate API contracts with the frontend developer.

## 15. Security and Development Rules

- Public registration must never allow privileged role assignment.
- Passwords must always be hashed.
- JWT secrets must be stored in environment variables.
- JWT must never be exposed through ordinary API response bodies.
- HTTP-only cookies must be used for browser authentication.
- Authentication and authorization must be enforced by the backend.
- Never trust frontend role or permission information.
- Avoid exposing sensitive user information.
- Use consistent error responses.
- Test authentication failure scenarios as well as successful scenarios.

---

**EduMesh Authentication Module**

Secure registration. Reliable authentication. Protected application access.
