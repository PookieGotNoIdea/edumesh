# EduMesh — Frontend & Backend Contracts

## 1. Purpose

This document defines the shared frontend and backend implementation contracts for EduMesh.

It ensures that both developers follow consistent element IDs, component names, data structures, API endpoints, request formats, response formats, and validation rules.

The frontend and backend will be developed independently. These contracts will act as an agreement between both sides and help reduce integration errors.

Before implementing a module, both developers should refer to and follow its corresponding contract in this document.

## 2. General Conventions

### 2.1 Frontend Technology

- Framework: React + Vite.
- Language: JavaScript.
- React components use `.jsx` files.
- Normal JavaScript files use `.js` files.
- Routing: React Router.
- State management: React Context and hooks.
- API communication: Axios.
- Styling: Tailwind CSS and Vanilla CSS.

### 2.2 Naming Conventions

| Item | Convention | Example |
|---|---|---|
| HTML element ID | kebab-case | `login-email` |
| CSS class | kebab-case | `login-button` |
| React component | PascalCase | `LoginForm` |
| JavaScript function | camelCase | `handleLogin` |
| React prop | camelCase | `isLoading` |
| API endpoint | lowercase | `/api/auth/login` |
| JSON property | camelCase | `firstName` |

### 2.3 React and JSX Rules

- Use `className` instead of `class` in JSX.
- Use `htmlFor` instead of `for` in labels.
- Use camelCase event handlers such as `onClick` and `onChange`.
- Use reusable React components for repeated UI elements.
- Use React state and props to manage dynamic UI behaviour.
- Avoid direct DOM manipulation as the primary way of controlling the interface.
- Important interactive elements must have stable IDs wherever specified in their module contracts.

### 2.4 Element ID Rules

- Every important interactive element should have a clear and descriptive ID.
- IDs must be unique within the rendered page.
- Use lowercase words separated by hyphens.
- Use `btn-` for important action buttons wherever appropriate.
- Give forms and their inputs separate IDs.
- Once an ID is agreed upon, it should not be changed without updating this document and informing the other developer.

Examples:

- `login-form`
- `login-email`
- `btn-login`
- `resource-search`
- `subject-grid`

### 2.5 CSS Class Rules

- CSS classes are mainly used for styling.
- Use descriptive class names.
- Classes should not be treated as the main frontend-backend integration contract.
- A CSS class can be changed during UI design without changing the API contract.

## 3. Common HTML / JSX Element Reference

This section explains the common HTML elements that may be used while developing EduMesh.

| Element | Purpose | Common Usage |
|---|---|---|
| `<div>` | General-purpose container | Layout and grouping |
| `<section>` | Groups related content | Learning Hub sections |
| `<header>` | Introductory or navigation area | Page header |
| `<footer>` | Footer content | Page footer |
| `<h1>` | Main page heading | Dashboard title |
| `<h2>` | Section heading | Subject heading |
| `<h3>` | Subsection heading | Topic heading |
| `<p>` | Displays paragraph text | Descriptions and messages |
| `<span>` | Inline text container | Status labels |
| `<strong>` | Highlights important text | Important information |
| `<form>` | Groups form inputs and handles submission | Login and signup |
| `<label>` | Describes an input field | Email label |
| `<input>` | Accepts user input | Email and password |
| `<textarea>` | Accepts longer text | Resource description |
| `<select>` | Provides selectable options | Subject selection |
| `<option>` | Defines an option inside a select | Subject choices |
| `<button>` | Triggers an action | Submit and logout |
| `<a>` | Navigates to another page or URL | Learning resource link |
| `<img>` | Displays an image | Profile or resource image |
| `<ul>` | Displays an unordered list | Topic list |
| `<ol>` | Displays an ordered list | Numbered instructions |
| `<li>` | Represents an individual list item | Individual topic |
| `<table>` | Displays tabular information | Performance breakdown |

Only elements needed by a particular module should be introduced into its implementation. This reference can be expanded as the project develops.

## 4. React Component and Props Conventions

React components are reusable building blocks of the frontend.

Examples:

- `LoginForm`
- `SignupForm`
- `SubjectCard`
- `ResourceCard`
- `QuizCard`

Props are values or functions passed from one React component to another.

Example:

`<ResourceCard resource={resource} onRate={handleRate} />`

| Prop | Purpose |
|---|---|
| `resource` | Supplies resource information |
| `onRate` | Handles a rating action |
| `isLoading` | Indicates whether something is loading |
| `onSubmit` | Handles form submission |

Each module will document its actual component names, props, and expected behaviour before implementation.

## 5. UI State Conventions

The frontend should handle the following states wherever they are relevant.

| State | Meaning |
|---|---|
| Loading | Data or an action is being processed |
| Success | An operation completed successfully |
| Error | An operation failed |
| Empty | No data is available to display |
| Disabled | An action is temporarily unavailable |

For example, when a student opens the Learning Hub:

- Loading: Subjects are being fetched.
- Success: Subjects are displayed.
- Empty: No subjects are available.
- Error: Subjects could not be loaded.

## 6. Module-wise Contracts

The following modules will have their own detailed frontend and backend contracts.

### 6.1 Authentication

**Status:** Pending contract finalization.

Will cover:

- Student registration
- Login and logout
- Current-user information
- Authentication state
- Form fields and their IDs
- Authentication API endpoints
- Request and response formats
- Validation and error handling
  
**Authentication contract status:** Core decisions finalized.

**Agreed decisions:**
- JWT storage: HTTP-only cookie.
- Public registration: Students only.
- Minimum password length: 8 characters.
- Password hashing: bcrypt.
- Authentication: JWT.
- Authorization: RBAC.

**Remaining:** Finalize detailed endpoint response formats, cookie expiration, CSRF configuration and implementation-specific validation before coding.

### 6.2 Learning Hub

**Status:** Pending contract finalization.

Will cover:

- Subjects and topics
- Resource search
- Notes, videos, and tutorials
- Resource display and filtering
- Learning Hub API endpoints

### 6.3 Resource Contribution and Review

**Status:** Pending contract finalization.

Will cover:

- Resource submission forms
- Subject and topic selection
- Resource review and moderation
- Approve, reject, and request-changes actions
- Resource management APIs

### 6.4 Ratings and Feedback

**Status:** Pending contract finalization.

Will cover:

- Star ratings
- Comments and feedback
- Helpful votes
- Resource reports
- Rating and feedback APIs

### 6.5 Practice and Quiz System

**Status:** Pending contract finalization.

Will cover:

- Quiz selection
- Question display
- Answer submission
- Quiz results and analysis
- Quiz history and APIs

### 6.6 Progress Tracking

**Status:** Pending contract finalization.

Will cover:

- Student performance
- Mistake history
- Weak topics
- Progress charts
- Learning recommendations
- Progress tracking APIs

### 6.7 What Each Module Contract Must Contain

Before implementing a module, its section must document:

1. Frontend element IDs and their purposes.
2. HTML element types and expected data.
3. React component names and their props.
4. User interactions and expected behaviour.
5. Backend API endpoints and HTTP methods.
6. Request JSON structures.
7. Response JSON structures.
8. Validation rules.
9. Error messages and HTTP status codes.
10. Independent testing expectations.
11. Frontend-backend integration notes.

## 7. Shared Integration Conventions

- Both developers must follow the latest agreed module contracts.
- The frontend must send data in the request format defined in the contract.
- The backend must return data in the response format defined in the contract.
- API endpoint names and JSON field names must remain consistent.
- Changes to agreed IDs, component props, endpoints, or data fields must be updated in this document.
- Both developers will test their own modules independently.
- Joint integration testing will be performed when the corresponding frontend and backend modules are ready.
- Neither developer should assume undocumented API behaviour or field names.

## 8. Contract Change Policy

- Discuss changes that affect both frontend and backend before implementing them.
- Update the relevant module contract whenever an agreed detail changes.
- Inform the other developer about changes that affect their work.
- Use the latest version of this document as the shared reference.

---

**Document Status:** Initial Draft — Module-specific contracts pending.

**Project:** EduMesh — NST Learning Hub

**Purpose:** Shared frontend and backend development reference.
