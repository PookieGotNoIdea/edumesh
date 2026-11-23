# Resource Contribution Module — Frontend

## 1. Module Overview

The Resource Contribution module allows authorized users to contribute educational resources to EduMesh.

Students and other authorized contributors should be able to submit learning materials that can help NST students understand their syllabus and study more effectively.

The module is responsible for the frontend interface used to:

- Submit new learning resources.
- Associate resources with subjects and topics.
- Provide resource titles and descriptions.
- Submit resource links and supported files.
- View personally submitted resources.
- Check resource submission and review status.
- Edit permitted resource information.
- Remove resources when permitted.
- View feedback when changes are requested.

The frontend is responsible for collecting and displaying resource information.

The backend is responsible for validating submissions, storing resource information, managing permissions and controlling resource review status.

Resource moderation and approval interfaces belong to the separate Reviews feature.

## 2. Planned Folder Structure

```text
resources/
│
├── README.md
│
├── components/
│   ├── ResourceSubmissionForm.jsx
│   ├── ResourceFormFields.jsx
│   ├── MyResourceCard.jsx
│   └── ResourceStatusBadge.jsx
│
├── pages/
│   ├── ResourceSubmissionPage.jsx
│   └── MyResourcesPage.jsx
│
├── services/
│   └── resourceService.js
│
└── hooks/
```

This is the proposed organization. Additional files may be introduced when required.

## 3. Resource Submission Page

The Resource Submission page allows an authorized user to submit a new educational resource.

### Required Element IDs

| Category | Element Type | Required ID | Purpose |
|---|---|---|---|
| Page container | `<main>` | `resource-submission-page` | Main submission page |
| Page heading | `<h1>` | `resource-submission-title` | Displays page title |
| Submission form | `<form>` | `resource-submission-form` | Contains submission fields |
| Resource title | `<input>` | `resource-title` | Accepts resource title |
| Resource description | `<textarea>` | `resource-description` | Accepts resource description |
| Resource type | `<select>` | `resource-type` | Selects resource category |
| Subject selection | `<select>` | `resource-subject` | Selects associated subject |
| Topic selection | `<select>` | `resource-topic` | Selects associated topic |
| Resource URL | `<input>` | `resource-url` | Accepts external resource URL |
| File upload | `<input type="file">` | `resource-file` | Selects a supported file |
| Submit button | `<button>` | `btn-submit-resource` | Submits the resource |
| Error message | `<div>` | `resource-submission-error` | Displays submission errors |
| Success message | `<div>` | `resource-submission-success` | Displays success feedback |
| Loading state | `<div>` | `resource-submission-loading` | Indicates submission processing |

The URL and file fields should be shown according to the selected resource type and the final backend requirements.

### Submission Behaviour

The form should:

- Accept the resource title.
- Accept a description.
- Allow selection of an available subject.
- Allow selection of a topic associated with the selected subject.
- Allow selection of a supported resource type.
- Accept an external URL or supported uploaded file where applicable.
- Validate required fields.
- Display appropriate validation errors.
- Prevent repeated submission while processing.
- Display the submission result.

The final supported resource types and submission rules must be confirmed with the backend.

## 4. Resource Types

EduMesh may support the following educational resource categories:

| Resource Type | Description |
|---|---|
| NOTES | Study notes and educational documents |
| YOUTUBE_VIDEO | Educational YouTube videos |
| EXTERNAL_TUTORIAL | External learning websites and tutorials |
| OTHER | Other approved educational materials |

These are proposed frontend categories. The final enum values and supported formats must match the backend implementation.

## 5. My Resources Page

The My Resources page allows users to view resources they have submitted.

### Required Element IDs

| Category | Element Type | Required ID | Purpose |
|---|---|---|---|
| Page container | `<main>` | `my-resources-page` | Main resource management page |
| Page heading | `<h1>` | `my-resources-title` | Displays page title |
| Resource list | `<div>` | `my-resources-list` | Displays submitted resources |
| Status filter | `<select>` | `my-resource-status-filter` | Filters by review status |
| Loading state | `<div>` | `my-resources-loading` | Displays while loading |
| Error state | `<div>` | `my-resources-error` | Displays errors |
| Empty state | `<div>` | `my-resources-empty` | Displays when no submissions exist |

### Individual Resource Card IDs

| Element | ID Pattern | Purpose |
|---|---|---|
| Resource card | `my-resource-card-{resourceId}` | Displays one submitted resource |
| Resource title | `my-resource-title-{resourceId}` | Displays resource title |
| Resource status | `my-resource-status-{resourceId}` | Displays current review status |
| Edit button | `btn-edit-resource-{resourceId}` | Opens resource editing |
| Delete button | `btn-delete-resource-{resourceId}` | Requests resource removal |
| View button | `btn-view-my-resource-{resourceId}` | Opens resource details |

### Expected Behaviour

- Retrieve resources submitted by the authenticated user.
- Display resource information.
- Display the current review status.
- Allow filtering by available status values.
- Provide permitted editing and removal actions.
- Display empty and error states appropriately.

The backend must ensure users can only access and manage resources they are authorized to manage.

## 6. Resource Editing

Users may need to correct or update their submitted resources.

### Expected Behaviour

- Allow editing of permitted resource fields.
- Display the existing resource information in the form.
- Validate updated information.
- Submit changes to the backend.
- Display success or error feedback.
- Refresh the displayed resource information after a successful update.

The backend must determine which resource statuses permit editing.

The frontend must not assume that every resource can be edited at every stage of moderation.

A separate edit page is not necessarily required. The editing interface may be implemented as a page, form view or modal depending on the final UI design.

## 7. Resource Removal

Users may be allowed to request or perform removal of their submitted resources.

### Expected Behaviour

- Display a removal action when permitted.
- Ask for confirmation before removal.
- Send the removal request to the backend.
- Display the result of the operation.
- Refresh the resource list after successful removal.

The backend determines whether removal is allowed based on ownership, permissions and resource status.

## 8. Resource Review Status

The frontend should display the review status returned by the backend.

The following statuses are proposed:

| Status | Meaning |
|---|---|
| `PENDING` | Resource has been submitted and is awaiting review |
| `UNDER_REVIEW` | Resource is currently being reviewed |
| `APPROVED` | Resource has been approved |
| `REJECTED` | Resource has been rejected |
| `CHANGES_REQUESTED` | Contributor must make requested changes |

### Required Element IDs

| Element | ID Pattern | Purpose |
|---|---|---|
| Status badge | `resource-status-{resourceId}` | Displays current status |
| Review feedback | `resource-feedback-{resourceId}` | Displays reviewer feedback |

### Status Behaviour

- Display the status supplied by the backend.
- Use consistent visual styling for each status.
- Display reviewer feedback when available.
- Show editing actions only when permitted.
- Do not independently determine resource approval status in the frontend.

The final status values and transition rules must be confirmed with backend development.

## 9. React Components

| Component | Responsibility |
|---|---|
| `ResourceSubmissionForm` | Handles new resource submissions |
| `ResourceFormFields` | Organizes resource input fields |
| `MyResourceCard` | Displays one submitted resource |
| `ResourceStatusBadge` | Displays resource review status |

Additional components may be introduced when required.

## 10. Proposed Frontend Routes

| Route | Purpose |
|---|---|
| `/resources/submit` | Displays the resource submission form |
| `/my-resources` | Displays the user's submitted resources |
| `/my-resources/:resourceId/edit` | Proposed resource editing view |

The editing route is optional. The editing interface may instead be displayed within the My Resources page.

The moderator review routes belong to the separate Reviews feature.

## 11. Proposed Backend API Endpoints

The following endpoints are proposed for backend coordination.

| Operation | Method | Proposed Endpoint |
|---|---|---|
| Submit resource | POST | `/api/resources` |
| Get my resources | GET | `/api/resources/my` |
| Get resource details | GET | `/api/resources/:resourceId` |
| Update resource | PATCH | `/api/resources/:resourceId` |
| Delete resource | DELETE | `/api/resources/:resourceId` |

The final endpoint paths, request schemas, permissions and response structures must be confirmed during backend implementation.

### A. Submit Resource

**Endpoint:** `POST /api/resources`

Purpose: Submit a new educational resource for review.

The request may contain:

- Resource title.
- Resource description.
- Resource type.
- Subject ID.
- Topic ID.
- Resource URL or uploaded file, depending on the selected type.

For file submissions, the final request format and multipart upload requirements must be confirmed with the backend.

### B. Get My Resources

**Endpoint:** `GET /api/resources/my`

Purpose: Retrieve resources submitted by the authenticated user.

Suggested query parameters:

- `status`
- `page`
- `limit`

### C. Get Resource Details

**Endpoint:** `GET /api/resources/:resourceId`

Purpose: Retrieve details of a selected resource, subject to access permissions.

### D. Update Resource

**Endpoint:** `PATCH /api/resources/:resourceId`

Purpose: Update permitted information belonging to a submitted resource.

The backend determines which fields can be changed and when editing is allowed.

### E. Delete Resource

**Endpoint:** `DELETE /api/resources/:resourceId`

Purpose: Request removal of a resource when the user is authorized to perform that action.

The exact removal behaviour must be confirmed during backend development.

## 12. Expected UI States

The frontend should handle:

- Initial loading.
- Submission form validation errors.
- Resource submission processing.
- Successful resource submission.
- Failed resource submission.
- File upload processing where applicable.
- My Resources loading.
- Empty submission list.
- Resource editing.
- Resource removal confirmation.
- Successful resource updates.
- Resource review status changes.
- Reviewer feedback display.
- API errors and permission errors.

## 13. Frontend Testing Checklist

Before marking Resource Contribution complete, verify:

- [ ] Resource submission page displays correctly.
- [ ] All agreed element IDs are present and unique.
- [ ] Required fields are validated.
- [ ] Subject selection works.
- [ ] Topic selection corresponds to the selected subject.
- [ ] Resource type selection works.
- [ ] URL submission works for supported resource types.
- [ ] File selection works for supported file types.
- [ ] Submission feedback displays correctly.
- [ ] My Resources loads the authenticated user's submissions.
- [ ] Resource status displays correctly.
- [ ] Status filtering works.
- [ ] Permitted resource editing works.
- [ ] Removal confirmation works.
- [ ] Unauthorized actions are handled correctly.
- [ ] Loading, error and empty states work correctly.

## 14. Independent Frontend Development

Divya can develop the Resource Contribution interface using mock resource data while the backend APIs are being implemented.

Mock data should include:

- Different resource types.
- Different subjects and topics.
- Resources with different review statuses.
- Resources with reviewer feedback.
- Resources that can be edited.
- Resources that cannot currently be edited.

During development:

- Keep API requests inside `resourceService.js`.
- Use mock data for independent frontend testing.
- Do not independently decide review status transitions.
- Do not assume all users can submit or remove every resource.
- Follow the backend permissions and API contracts during integration.

The Reviews feature will handle the moderator's review and approval interface separately.

---

**Resource Contribution Module Status:** Core submission and management requirements documented. Final resource types, file restrictions, editing permissions, removal behaviour, status transitions and API contracts require backend confirmation.
