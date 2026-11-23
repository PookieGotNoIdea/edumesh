# API Services — Frontend

## 1. Folder Overview

The `services/` folder contains shared API communication configuration used by the EduMesh frontend.

It provides a centralized way for the React application to communicate with the backend through HTTP requests.

EduMesh uses:

- Axios for HTTP communication.
- REST APIs for frontend-backend communication.
- JSON for request and response data.
- Environment variables for backend configuration.
- HTTP-only cookies for authentication.

The main purpose of this folder is to avoid creating separate Axios configurations in different feature modules.

## 2. Planned Folder Structure

```text
services/
│
├── README.md
│
└── apiClient.js
```

This is the proposed initial structure. Additional shared API configuration files may be introduced when required.

Feature-specific API services should remain inside their respective feature folders.

For example:

```text
features/
├── auth/
│   └── services/
│       └── authService.js
│
├── learning-hub/
│   └── services/
│       └── learningHubService.js
│
├── quizzes/
│   └── services/
│       └── quizService.js
│
└── progress/
    └── services/
        └── progressService.js
```

## 3. Centralized Axios Client

The `apiClient.js` file should contain the shared Axios instance.

All feature-specific services should use this instance instead of creating their own Axios configurations.

### Responsibilities

- Define the backend API base URL.
- Configure JSON request and response handling.
- Enable credential transmission where required.
- Provide consistent HTTP request configuration.
- Support shared request and response interceptors where needed.
- Handle common API communication behaviour.

### Example: apiClient.js

```javascript
import axios from "axios";

const apiClient = axios.create({
  baseURL: import.meta.env.VITE_API_BASE_URL,
  withCredentials: true,
  headers: {
    "Content-Type": "application/json",
  },
});

export default apiClient;
```

This is an illustrative starting configuration. The final configuration should match the backend deployment and security settings.

## 4. Environment Variables

The backend API URL should be configurable through an environment variable.

Proposed variable:

```env
VITE_API_BASE_URL=http://localhost:5000/api
```

The actual backend port and API base URL must match the backend configuration.

### Environment File Rules

- Use `.env` for local development configuration.
- Do not commit private environment values.
- Keep `.env` files excluded through `.gitignore`.
- Provide `.env.example` with placeholder configuration when required.
- Do not store passwords, database credentials, JWT secrets or other private backend secrets in frontend environment variables.

Important: Vite exposes variables prefixed with `VITE_` to frontend code. Therefore, only values safe to expose to the browser should use this prefix.

## 5. HTTP-Only Cookie Authentication

EduMesh uses JWT authentication through HTTP-only cookies.

The frontend must follow these rules:

- Axios requests requiring authentication must send credentials.
- Use `withCredentials: true` in the shared Axios configuration.
- Do not read the JWT directly through JavaScript.
- Do not store JWT tokens in localStorage.
- Do not store JWT tokens in sessionStorage.
- Do not manually attach a JWT from frontend storage.

The browser should automatically handle the HTTP-only authentication cookie according to the backend's cookie and cross-origin configuration.

The backend must configure its cookie, CORS and related security settings appropriately.

## 6. Feature-Specific API Services

Each feature should organize its own API requests inside its feature-level `services/` folder.

Examples:

| Feature | Service File | Responsibility |
|---|---|---|
| Authentication | `authService.js` | Registration, login, logout and current-user requests |
| Learning Hub | `learningHubService.js` | Subjects, topics and learning resources |
| Resources | `resourceService.js` | Resource submission and contributor operations |
| Reviews | `reviewService.js` | Resource moderation operations |
| Ratings | `ratingService.js` | Ratings, comments and feedback |
| Quizzes | `quizService.js` | Quiz discovery and attempts |
| Progress | `progressService.js` | Progress, mistakes and learning goals |
| Notifications | `notificationService.js` | Notification history and read-state operations |

Each feature service should import the centralized Axios client.

### Example: quizService.js

```javascript
import apiClient from "../../../services/apiClient";

export const getQuizzes = async () => {
  const response = await apiClient.get("/quizzes");
  return response.data;
};
```

This is an illustrative example. Actual service functions should follow the agreed backend API contracts.

## 7. Request and Response Handling

The frontend should communicate with the backend using the agreed API contracts.

### Requests

Feature services should:

- Use the correct HTTP method.
- Send the expected request body.
- Include required query parameters.
- Use the correct resource identifiers.
- Allow Axios to send credentials where required.

### Responses

Feature services should return the response data in a consistent way.

Components should receive the data they need without duplicating request configuration.

### Error Handling

The frontend should handle common API errors, including:

- `400 Bad Request` — invalid request data.
- `401 Unauthorized` — authentication is missing or invalid.
- `403 Forbidden` — the user does not have permission.
- `404 Not Found` — the requested resource does not exist.
- `409 Conflict` — the request conflicts with existing data.
- `500 Internal Server Error` — an unexpected backend error occurred.

The frontend should display appropriate user-friendly messages.

It must not expose database details, stack traces or sensitive backend information.

The final error response format should be agreed with the backend developer.

## 8. Axios Interceptors

Axios interceptors may be used for shared request and response handling.

Possible responsibilities include:

- Handling common authentication errors.
- Standardizing error processing.
- Logging development-time request information.
- Handling expired or invalid sessions.
- Supporting consistent response behaviour.

Interceptors should not duplicate feature-specific business logic.

The final interceptor implementation should be coordinated with the authentication flow.

## 9. Loading and Error State Management

API services should remain responsible for communicating with the backend.

Loading, success and error states should generally be managed by the feature components or hooks that use those services.

For example:

- A quiz page manages quiz loading and submission states.
- A progress page manages progress loading and display errors.
- A notification hook manages notification loading and update states.

This keeps API configuration separate from feature presentation and state management.

## 10. Coding Conventions

- Use JavaScript ES Modules.
- Use `import` and `export`.
- Use the centralized Axios instance.
- Keep feature-specific API functions inside their feature folders.
- Use descriptive service function names.
- Use `async/await` for asynchronous requests.
- Avoid duplicating Axios configuration.
- Do not place React components inside the services folder.
- Do not place backend business logic inside frontend services.
- Do not expose private backend credentials.

## 11. Frontend Testing Checklist

Before marking the services folder complete, verify:

- [ ] Centralized Axios client is configured.
- [ ] Backend base URL comes from the environment variable.
- [ ] JSON request configuration works.
- [ ] `withCredentials: true` is configured.
- [ ] Authentication cookies are handled by the browser.
- [ ] JWT tokens are not stored in browser storage.
- [ ] Feature services use the centralized Axios client.
- [ ] API requests use the correct HTTP methods.
- [ ] Request bodies match backend contracts.
- [ ] Query parameters are passed correctly.
- [ ] Common API errors are handled appropriately.
- [ ] Backend details and sensitive information are not exposed.
- [ ] Local environment files are excluded from Git.

## 12. Independent Frontend Development

Divya can create the centralized Axios client and feature service files while the backend APIs are being developed.

During independent development:

- Use mock data where necessary.
- Keep service functions organized by feature.
- Avoid depending on unfinished backend endpoints.
- Record expected request and response structures.
- Coordinate API contracts with the backend developer before integration.

Once the backend endpoints are available, replace mock implementations with actual Axios requests and test each feature independently.

---

**Services Folder Status:** Centralized Axios configuration, environment variables, HTTP-only cookie handling and feature-level API service organization documented. Final API base URL, error response structure, interceptors and backend endpoint contracts require coordination during integration.
