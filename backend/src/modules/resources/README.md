# Resource Management Module — resources

## 1. Overview

The `resources/` module manages educational resource contribution and retrieval functionality in the EduMesh application.

It allows students to contribute useful learning materials and makes approved resources available to other students through the Learning Hub.

The module is responsible for managing resource records, submission information, contributor associations and resource-related operations.

## 2. Responsibilities

The `resources/` module is responsible for:

- Accepting educational resource submissions.
- Managing resource information.
- Retrieving approved learning resources.
- Managing contributor-related resource information.
- Updating permitted resource details.
- Associating resources with subjects and topics.
- Managing resource submission status.
- Supporting resource discovery.
- Providing resource information to other application modules.

## 3. Planned Folder Structure

```text
resources/
│
├── README.md
├── resources.routes.js
├── resources.controller.js
├── resources.service.js
└── resources.validation.js
```

### File Responsibilities

| File | Responsibility |
|---|---|
| `README.md` | Documents resource management architecture |
| `resources.routes.js` | Defines resource-related API endpoints |
| `resources.controller.js` | Handles resource HTTP requests and responses |
| `resources.service.js` | Implements resource management business logic |
| `resources.validation.js` | Validates resource submission and update data |

Additional files may be introduced if specialized resource functionality requires them.

## 4. Resource Management Features

### 4.1 Resource Contribution

Allows authenticated students to contribute educational materials.

Potential resource types include:

- Study notes.
- YouTube educational videos.
- External tutorials.
- Other approved educational materials.

A resource submission may contain:

- Resource title.
- Description.
- Resource type.
- Resource URL or supported file reference.
- Associated subject.
- Associated topic.
- Contributor information.

The exact submission fields and supported resource types will be finalized during API and database design.

### 4.2 Resource Retrieval

Allows students to retrieve approved educational resources.

Responsibilities include:

- Retrieving resources associated with subjects.
- Retrieving resources associated with topics.
- Retrieving individual resource details.
- Filtering resources by supported criteria.
- Providing resource information to the Learning Hub.

Only resources permitted for student access should be returned through public learning interfaces.

### 4.3 Resource Management

Allows contributors to manage their own submissions where permitted.

Potential operations include:

- Viewing contributed resources.
- Updating permitted resource details.
- Viewing submission status.
- Managing resources according to their moderation status.

Changes to already approved resources may require renewed moderation.

### 4.4 Resource Status Management

Resources may pass through a moderation workflow.

Proposed statuses include:

- `PENDING`
- `APPROVED`
- `REJECTED`
- `NEEDS_CHANGES`

The final status names and allowed transitions will be coordinated with the reviews module and database schema.

The resources module manages resource records, while moderation decisions belong to the reviews module.

## 5. Proposed API Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/api/resources` | Submit a new resource |
| GET | `/api/resources` | Retrieve approved resources with supported filters |
| GET | `/api/resources/:resourceId` | Retrieve resource details |
| GET | `/api/resources/my-resources` | Retrieve the authenticated user's contributions |
| PATCH | `/api/resources/:resourceId` | Update permitted resource information |
| DELETE | `/api/resources/:resourceId` | Delete or withdraw a resource where permitted |

These are proposed endpoints and must be finalized during frontend-backend API contract coordination.

Deletion and withdrawal policies must be established before implementation.

## 6. Database Integration

The resources module interacts with database models defined in the Prisma schema.

Potential database entities include:

- Resource.
- User.
- Subject.
- Topic.

### Planned Relationships

- A user can contribute multiple resources.
- Each resource has an associated contributor.
- A resource may be associated with a subject.
- A resource may be associated with a topic.
- A resource may have associated moderation records.
- A resource may receive multiple ratings.

The exact relationships, optional fields and referential actions will be finalized during database schema design.

Database operations will be implemented through Prisma Client inside the resources service.

## 7. Authentication and Authorization

Resource operations must follow backend authentication and authorization rules.

### Access Rules

- Students must authenticate before submitting resources.
- Contributors may view their own submissions.
- Contributors may update only resources they are permitted to manage.
- Only authorized users may perform moderation-related operations.
- Students may retrieve resources approved for general access.
- Unauthorized users must not modify another contributor's resources.

All permissions must be enforced by the backend.

## 8. Integration with Other Modules

### Learning Hub

Provides resource information for subjects and topics.

### Reviews

Coordinates resource moderation and approval decisions.

### Ratings

Provides resource information required for rating and feedback operations.

### Users

Associates resource contributions with their respective contributors.

Cross-module communication should maintain clear boundaries and avoid duplicating business logic.

## 9. Validation

The proposed validation library is Zod.

Resource-related requests will be validated for:

- Required fields.
- Resource title and description.
- Supported resource types.
- Valid resource URLs or file references.
- Subject identifiers.
- Topic identifiers.
- Resource ownership.
- Permitted update fields.

The backend must verify resource ownership and permissions rather than trusting information supplied by the frontend.

## 10. Error Handling

The resources module must handle errors such as:

- Missing required submission fields.
- Invalid resource URLs.
- Unsupported resource types.
- Subject or topic not found.
- Resource not found.
- Unauthorized resource modification.
- Invalid resource status transitions.
- Database operation failures.

Error responses must follow centralized backend error-handling conventions.

## 11. Frontend Integration

The resources module communicates with the React frontend through REST APIs.

Frontend responsibilities include:

- Resource submission forms.
- Resource listing and detail interfaces.
- Contributor resource management.
- Submission status displays.
- Loading, success and error states.

Backend responsibilities include:

- Validating resource submissions.
- Managing resource records.
- Checking contributor permissions.
- Retrieving approved resources.
- Coordinating moderation status.
- Returning consistent JSON responses.

Authenticated Axios requests must use `withCredentials: true`.

## 12. Development Workflow

Resource management implementation will follow these steps:

1. Identify supported resource types.
2. Define the Resource database model.
3. Establish relationships with users, subjects and topics.
4. Coordinate submission fields with the frontend developer.
5. Define resource validation requirements.
6. Implement resource submission.
7. Implement resource retrieval.
8. Implement contributor-specific resource listing.
9. Implement permitted resource updates.
10. Coordinate moderation operations with the reviews module.
11. Test resource ownership and authorization.
12. Test resource retrieval and filtering.
13. Update documentation when necessary.

## 13. Security and Development Rules

- Require authentication for resource contribution.
- Verify resource ownership before modification.
- Validate submitted URLs and supported resource types.
- Prevent unauthorized changes to moderation decisions.
- Keep moderation logic within the reviews module.
- Return only resources permitted for the requesting user.
- Avoid exposing unnecessary contributor information.
- Validate all incoming request data.
- Use Prisma Client for database operations.
- Coordinate resource status changes with the reviews module.

---

**EduMesh Resource Management Module**

Community contributions. Organized educational materials. Accessible learning resources.
