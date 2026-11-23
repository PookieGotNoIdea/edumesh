# Authentication Module — Frontend

## 1. Module Overview

The Authentication module manages user login, registration and authentication-related interactions in EduMesh.

It allows NST students to create accounts, log in securely, maintain an authenticated session and log out.

The frontend is responsible for:

- Displaying login and registration forms.
- Collecting and validating user input.
- Communicating with authentication APIs.
- Displaying authentication errors and success messages.
- Maintaining authentication state through React Context.
- Supporting protected application routes.
- Providing logout functionality.

The backend is responsible for password verification, password hashing, JWT generation, cookie management and authentication verification.

## 2. Planned Folder Structure

```text
auth/
│
├── README.md
│
├── components/
│   ├── LoginForm.jsx
│   └── SignupForm.jsx
│
├── pages/
│   └── AuthPage.jsx
│
├── services/
│   └── authService.js
│
└── hooks/
    └── useAuth.js
```

This is the proposed organization. Additional files may be introduced when required.

Global authentication state should be maintained through `src/app/providers/AuthProvider.jsx`, rather than creating a second independent authentication provider inside this feature.

## 3. Login Interface

The Login interface allows registered students to access EduMesh.

### Required Element IDs

| Category | Element Type | Required ID | Purpose |
|---|---|---|---|
| Login form | `<form>` | `login-form` | Contains login inputs |
| Email input | `<input>` | `login-email` | Accepts registered email |
| Password input | `<input>` | `login-password` | Accepts account password |
| Login button | `<button>` | `btn-login` | Submits login form |
| Signup navigation | `<button>` | `btn-show-signup` | Opens registration interface |
| Error message | `<div>` | `login-error` | Displays login errors |
| Success message | `<div>` | `login-success` | Displays success feedback |
| Loading state | `<div>` | `login-loading` | Indicates login processing |

### Login Behaviour

- Accept email and password.
- Validate required fields.
- Submit credentials to the backend.
- Display appropriate validation and authentication errors.
- Prevent repeated submission while processing.
- Update authentication state after successful login.
- Redirect the user according to the agreed navigation rules.

## 4. Registration Interface

The Registration interface allows new NST students to create an EduMesh account.

Public registration is restricted to students.

The backend automatically assigns the `STUDENT` role. Users must not be allowed to select their role during public registration.

### Required Element IDs

| Category | Element Type | Required ID | Purpose |
|---|---|---|---|
| Signup form | `<form>` | `signup-form` | Contains registration inputs |
| Name input | `<input>` | `signup-name` | Accepts student's name |
| Email input | `<input>` | `signup-email` | Accepts email address |
| Password input | `<input>` | `signup-password` | Accepts account password |
| Confirm password | `<input>` | `signup-confirm-password` | Confirms password |
| Signup button | `<button>` | `btn-signup` | Submits registration |
| Login navigation | `<button>` | `btn-show-login` | Opens login interface |
| Error message | `<div>` | `signup-error` | Displays registration errors |
| Success message | `<div>` | `signup-success` | Displays success feedback |
| Loading state | `<div>` | `signup-loading` | Indicates registration processing |

### Registration Behaviour

- Accept the student's name, email and password.
- Validate all required fields.
- Confirm that both password entries match.
- Submit registration details to the backend.
- Display appropriate success or error feedback.
- Do not provide a public role-selection field.
- Do not send the confirm-password field to the backend.

## 5. React Components

| Component | Responsibility |
|---|---|
| `LoginForm.jsx` | Displays and handles the login form |
| `SignupForm.jsx` | Displays and handles the registration form |
| `AuthPage.jsx` | Organizes the authentication interface |
| `AuthProvider.jsx` | Maintains global authentication state |
| `ProtectedRoute.jsx` | Restricts access to authenticated pages |

`AuthProvider.jsx` and `ProtectedRoute.jsx` belong in their respective global application folders, not inside the authentication feature.

## 6. Form Validation

Frontend validation should use React Hook Form and Zod.

### Registration Validation

| Field | Validation Rule |
|---|---|
| Name | Required and must not be blank |
| Email | Required and must be a valid email address |
| Password | Required and at least 8 characters |
| Confirm Password | Must match the password |

### Login Validation

| Field | Validation Rule |
|---|---|
| Email | Required and valid email format |
| Password | Required |

The backend must independently validate all incoming authentication requests.

Frontend validation improves usability but does not replace backend validation.

## 7. Backend API Endpoints

The following authentication endpoints have been agreed upon.

| Operation | Method | Endpoint |
|---|---|---|
| Register student | POST | `/api/auth/register` |
| Login | POST | `/api/auth/login` |
| Get current user | GET | `/api/auth/me` |
| Logout | POST | `/api/auth/logout` |

### A. Student Registration

**Endpoint:** `POST /api/auth/register`

Request:

```json
{
  "name": "Student Name",
  "email": "student@example.com",
  "password": "password123"
}
```

Important rules:

- Do not send a `role` field.
- Do not send `confirmPassword` to the backend.
- The backend automatically assigns the `STUDENT` role.
- The backend hashes the password before storing it.

### B. Login

**Endpoint:** `POST /api/auth/login`

Request:

```json
{
  "email": "student@example.com",
  "password": "password123"
}
```

The backend verifies the credentials and sets the authentication cookie.

The response should provide user information, not the JWT token.

### C. Get Current User

**Endpoint:** `GET /api/auth/me`

Purpose:

- Retrieve the currently authenticated user's information.
- Check whether the existing session is valid.
- Restore authentication state when the application loads.

The response should contain relevant user information, including the user's role.

### D. Logout

**Endpoint:** `POST /api/auth/logout`

Purpose:

- Request that the backend clear the authentication cookie.
- End the authenticated session.
- Allow the frontend to clear its local authentication state.

The exact response structures and error codes will be finalized in the shared API contract.

## 8. JWT Cookie Handling

EduMesh uses JWT authentication through an HTTP-only cookie.

The frontend must follow these rules:

1. Never read the JWT using JavaScript.
2. Never store the JWT in localStorage.
3. Never store the JWT in sessionStorage.
4. Use Axios with `withCredentials: true` for authenticated requests.
5. Use `/api/auth/me` to retrieve the current user.
6. Allow the browser to send the authentication cookie automatically when configured correctly.
7. Call the logout API to request cookie removal.

The backend is responsible for generating, verifying and clearing the JWT cookie.

Cookie security settings, CORS and CSRF protection must be coordinated during backend implementation and integration.

## 9. Authentication State

The frontend should use React Context and hooks to manage shared authentication state.

The authentication state should provide:

- Current user information.
- Authentication status.
- User role.
- Authentication loading state.
- Login and logout actions.
- Current-user refresh functionality.

The authentication provider should be implemented in:

`src/app/providers/AuthProvider.jsx`

The authentication feature should use the shared authentication context rather than maintaining a separate copy of global authentication state.

## 10. Protected Routes

Authenticated pages must be protected through the application routing system.

Expected behaviour:

- Unauthenticated users attempting to access protected pages should be redirected to `/login`.
- Authenticated students should be able to access authorized student pages.
- Moderators should be able to access authorized moderation pages.
- Unauthorized users should not be allowed to access restricted pages.
- The backend must independently enforce authorization on protected APIs.

Frontend route protection is for navigation and user experience. It is not a replacement for backend security.

## 11. Expected UI States

The authentication interface should handle:

- Initial loading.
- Form validation errors.
- Login processing.
- Registration processing.
- Successful registration.
- Successful login.
- Invalid credentials.
- Duplicate email registration.
- Network errors.
- Authentication session expiration.
- Logout processing.

Error messages should be understandable and should not expose sensitive backend or database information.

## 12. Frontend Routes

| Route | Purpose |
|---|---|
| `/login` | Displays login interface |
| `/signup` | Displays registration interface |

After successful authentication:

- Students should be directed to `/dashboard`.
- Authorized moderators should be directed to `/moderation`.

The routing system is maintained separately inside `src/app/router/`.

## 13. Frontend Testing Checklist

Before marking the Authentication module complete, verify:

- [ ] Login form displays correctly.
- [ ] Registration form displays correctly.
- [ ] All required element IDs are present and unique.
- [ ] Empty fields are validated.
- [ ] Invalid email formats are rejected.
- [ ] Password minimum length is enforced.
- [ ] Confirm-password matching works.
- [ ] Registration sends only name, email and password.
- [ ] Login sends email and password.
- [ ] Successful authentication updates shared state.
- [ ] Authentication state is restored through `/api/auth/me`.
- [ ] JWT is never accessed through JavaScript.
- [ ] JWT is not stored in localStorage or sessionStorage.
- [ ] Authenticated requests use the configured Axios cookie handling.
- [ ] Protected routes work correctly.
- [ ] Role-based navigation works correctly.
- [ ] Logout clears frontend authentication state.
- [ ] Loading, error and success states work correctly.

## 14. Independent Frontend Development

Divya can develop the authentication interface using mock responses while the backend authentication APIs are being implemented.

Mock development should cover:

- Successful login.
- Invalid credentials.
- Successful registration.
- Duplicate email errors.
- Authentication loading.
- Existing authenticated session.
- Logout.

Mock responses must not be treated as proof that real authentication or cookie handling works.

Real cookie behaviour, API authentication and role-based access must be tested during joint frontend-backend integration.

---

**Authentication Module Status:** Core authentication decisions and frontend requirements documented. Detailed cookie security configuration, final response/error contracts and joint integration testing remain to be completed.
