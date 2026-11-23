# Providers Folder — Frontend

## 1. Folder Overview

The `providers/` folder contains React Context providers responsible for managing application-wide state and making shared functionality accessible throughout the EduMesh frontend.

Providers allow multiple components to access common information without unnecessarily passing props through several component levels.

Only state and functionality that genuinely need to be shared across the application should be placed here.

## 2. Planned Folder Structure

```text
providers/
│
├── README.md
│
├── AuthProvider.jsx
└── ThemeProvider.jsx
```

The actual provider files will be created during frontend initialization.

| File | Responsibility |
|---|---|
| `AuthProvider.jsx` | Manages shared authentication state and current user information |
| `ThemeProvider.jsx` | Manages application theme state if theme switching is implemented |

## 3. Authentication Provider

`AuthProvider.jsx` is responsible for making authentication information available throughout the application.

It should manage:

- Whether a user is authenticated.
- Current authenticated user information.
- Current user's role.
- Authentication loading state.
- Authentication-related errors where appropriate.
- Updating authentication state after login.
- Clearing authentication state after logout.
- Checking the current session when the application loads.

### Expected Authentication Information

The authentication context should expose information similar to:

| Property / Function | Purpose |
|---|---|
| `user` | Stores the current authenticated user's information |
| `isAuthenticated` | Indicates whether the user is authenticated |
| `isLoading` | Indicates whether authentication status is being checked |
| `authError` | Stores relevant authentication errors |
| `login()` | Updates authentication state after successful login |
| `logout()` | Clears authentication state after successful logout |
| `refreshUser()` | Retrieves the current authenticated user's information |

The exact context interface may be refined during implementation.

## 4. JWT Cookie Handling

EduMesh uses JWT authentication with an HTTP-only cookie.

The backend is responsible for:

- Generating the JWT.
- Setting the authentication cookie.
- Verifying the JWT.
- Clearing the cookie during logout.
- Enforcing authentication and authorization on protected API endpoints.

The frontend must follow these rules:

1. Never read the JWT using JavaScript.
2. Never store the JWT in localStorage.
3. Never store the JWT in sessionStorage.
4. Use Axios requests with `withCredentials: true` where authentication cookies are required.
5. Use the `/api/auth/me` endpoint to retrieve the current authenticated user's information.
6. Use the login endpoint to establish the authenticated session.
7. Use the logout endpoint to request that the backend clear the authentication cookie.

The frontend should manage the user's authentication state, not the JWT itself.

## 5. Application Authentication Flow

The authentication provider should support the following flow.

### A. When the Application Loads

1. The provider initializes its authentication state.
2. It checks the current session using `GET /api/auth/me`.
3. The browser automatically includes the authentication cookie when the request is configured correctly.
4. If the session is valid, the provider stores the returned user information.
5. If the session is invalid or absent, the provider sets the user to an unauthenticated state.
6. The provider finishes its loading state.

### B. After Successful Login

1. The user submits the login form.
2. The frontend sends the email and password to the backend.
3. The backend verifies the credentials.
4. The backend sets the HTTP-only authentication cookie.
5. The frontend receives the user information in the response.
6. The authentication provider updates the current user and authentication state.
7. The router redirects the user to the appropriate dashboard.

### C. After Logout

1. The frontend calls `POST /api/auth/logout`.
2. The backend clears the authentication cookie.
3. The authentication provider clears the current user information.
4. The user is redirected to `/login`.

## 6. Other Global Providers

Additional providers may be introduced when application-wide functionality requires shared state.

For example, `ThemeProvider.jsx` may manage:

- Current application theme.
- Light and dark mode selection.
- Theme preferences.

Do not create providers for functionality that can be handled locally inside an individual feature.

## 7. Development Guidelines

1. Use React Context API for shared application state.
2. Keep global providers inside `providers/`.
3. Keep authentication state management inside `AuthProvider.jsx`.
4. Do not place page components or route definitions here.
5. Do not store authentication tokens in frontend-accessible storage.
6. Do not read the HTTP-only cookie using JavaScript.
7. Keep feature-specific state inside the relevant feature when possible.
8. Avoid unnecessary global state.
9. Use the agreed Axios configuration for authenticated requests.
10. Follow the authentication requirements in Section 5 of the EduMesh Frontend Guide.

## 8. Important Note

This folder defines the planned global state management architecture.

The actual React Context providers will be implemented during frontend development.

Authentication security, JWT generation, cookie configuration and backend session verification remain backend responsibilities.

The presence of this README does not mean authentication has already been implemented.
