# Layouts — Frontend

## 1. Folder Overview

The `layouts/` folder contains reusable layout components that define the overall structure of EduMesh pages.

A layout provides a consistent arrangement of common interface elements such as:

- Header.
- Navigation bar.
- Sidebar.
- Main content area.
- Footer.
- Page-level containers.

Layouts help maintain a consistent user experience across different pages.

Instead of recreating the same page structure in every feature, pages can use an appropriate shared layout.

## 2. Planned Folder Structure

```text
layouts/
│
├── README.md
│
├── AuthLayout.jsx
├── StudentLayout.jsx
└── ModeratorLayout.jsx
```

This is the proposed initial structure. Additional layouts can be introduced if required.

## 3. Layout Components

### A. AuthLayout.jsx

Purpose: Provides the common layout for authentication pages.

It may be used by:

- Login page.
- Registration page.

Expected responsibilities:

- Display the EduMesh logo or branding.
- Provide a clean authentication content area.
- Maintain consistent spacing and alignment.
- Support responsive layouts.
- Display authentication-related content through React Router's nested route outlet where appropriate.

Authentication forms and validation logic belong to the Authentication feature, not this layout.

### B. StudentLayout.jsx

Purpose: Provides the main application layout for authenticated students.

Expected responsibilities:

- Display the shared application header.
- Display student navigation.
- Provide a main content area.
- Provide access to the notification bell.
- Display navigation links to relevant student features.
- Maintain consistent page spacing and responsiveness.

Possible navigation destinations include:

- Dashboard.
- Learning Hub.
- Quizzes.
- Progress.
- Notifications.
- Profile.

The exact navigation items should follow the final route and access-control configuration.

### C. ModeratorLayout.jsx

Purpose: Provides the common application layout for moderator-facing pages.

Expected responsibilities:

- Display the shared application header.
- Provide moderator navigation.
- Provide a main content area.
- Display moderator-specific navigation options.
- Maintain consistent layout and responsive behaviour.

Moderator-specific business logic and moderation interfaces belong to their respective feature modules.

## 4. Shared Layout Responsibilities

Layouts should handle:

- Overall page structure.
- Common navigation placement.
- Header and sidebar positioning.
- Main content positioning.
- Responsive page structure.
- Consistent spacing.
- Shared page-level styling.
- Nested route rendering where appropriate.

Layouts should not contain feature-specific business logic.

## 5. React Router Integration

Layouts should work with React Router.

Where nested routes are used, React Router's `Outlet` component can render the child page inside the selected layout.

Example:

```jsx
import { Outlet } from "react-router-dom";

function StudentLayout() {
  return (
    <div className="student-layout">
      <header>
        {/* Shared application header */}
      </header>

      <main>
        <Outlet />
      </main>
    </div>
  );
}

export default StudentLayout;
```

This is an illustrative example. The actual header, navigation and styling should be implemented using the shared components and agreed application structure.

## 6. Layout and Component Separation

Layouts should reuse shared components from:

`src/components/`

For example:

- Application header.
- Sidebar.
- Navigation menu.
- Footer.
- Notification bell.

The layout should arrange these components rather than duplicate their internal implementation.

## 7. Authentication and Access Control

Layouts are not a replacement for route-level authentication and authorization.

The application should use the agreed authentication provider and route protection approach.

Expected behaviour:

- Unauthenticated users should not access protected application areas.
- Student pages should follow student access rules.
- Moderator pages should follow moderator access rules.
- Unauthorized users should be redirected or shown an appropriate access-denied interface.

The final access-control implementation must follow the backend's role-based authorization rules.

## 8. Responsive Design

All layouts should support different screen sizes.

Expected behaviour:

- Desktop layouts should use the available screen space effectively.
- Tablet layouts should adapt navigation and content spacing.
- Mobile layouts should provide accessible navigation.
- Sidebars may collapse or use a mobile navigation pattern.
- Main content should remain readable without horizontal overflow.

## 9. Coding Conventions

- Use React functional components.
- Use `.jsx` for React component files.
- Use consistent component naming in PascalCase.
- Keep each layout focused on page structure.
- Reuse shared components instead of duplicating them.
- Keep feature-specific logic inside the corresponding feature folder.
- Keep styling consistent with the project's Tailwind CSS and Vanilla CSS approach.

## 10. Frontend Testing Checklist

Before marking the layouts folder complete, verify:

- [ ] Authentication pages render inside `AuthLayout`.
- [ ] Student pages render inside `StudentLayout`.
- [ ] Moderator pages render inside `ModeratorLayout`.
- [ ] Nested routes render correctly.
- [ ] Shared header and navigation display correctly.
- [ ] Notification bell appears in the appropriate authenticated layout.
- [ ] Protected pages follow authentication rules.
- [ ] Role-specific pages follow authorization rules.
- [ ] Layouts work on desktop, tablet and mobile.
- [ ] No feature-specific business logic is unnecessarily placed inside layouts.

---

**Layouts Folder Status:** Initial layout responsibilities and proposed components documented. Final navigation structure, shared header implementation and route access rules must be coordinated with the application routing and authentication setup.
