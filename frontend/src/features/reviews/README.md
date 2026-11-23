# Resource Reviews and Moderation — Frontend

## 1. Module Overview

The Reviews module provides the frontend interface for reviewing and moderating educational resources submitted to EduMesh.

Authorized moderators should be able to review submitted resources, evaluate their content and decide whether a resource should be approved, rejected or returned to its contributor for changes.

The module is responsible for:

- Displaying the moderator dashboard.
- Showing submitted resources awaiting review.
- Displaying resource information for evaluation.
- Showing the contributor's submitted information.
- Approving suitable resources.
- Rejecting unsuitable resources.
- Requesting changes from contributors.
- Providing review feedback.
- Displaying review status.
- Handling reported or flagged content when that functionality is included in the finalized moderation workflow.

The frontend is responsible for displaying the moderation interface and sending moderator actions to the backend.

The backend is responsible for verifying moderator permissions, enforcing review rules, updating resource status and recording moderation activity.

## 2. Planned Folder Structure

```text
reviews/
│
├── README.md
│
├── components/
│   ├── ModerationQueue.jsx
│   ├── ModerationResourceCard.jsx
│   ├── ResourceReviewDetails.jsx
│   ├── ReviewStatusBadge.jsx
│   └── ReviewFeedbackForm.jsx
│
├── pages/
│   ├── ModeratorDashboardPage.jsx
│   └── ResourceReviewPage.jsx
│
├── services/
│   └── reviewService.js
│
└── hooks/
```

This is the proposed organization. Additional files may be introduced when required.

## 3. Moderator Dashboard

The Moderator Dashboard is the main page for authorized moderators.

It provides an overview of resources requiring moderation and allows moderators to open individual submissions for review.

### Required Element IDs

| Category | Element Type | Required ID | Purpose |
|---|---|---|---|
| Page container | `<main>` | `moderation-dashboard-page` | Main moderator dashboard |
| Page heading | `<h1>` | `moderation-dashboard-title` | Displays dashboard title |
| Pending section | `<section>` | `pending-resources-section` | Contains pending submissions |
| Review queue | `<div>` | `moderation-queue` | Displays resources awaiting review |
| Status filter | `<select>` | `moderation-status-filter` | Filters resources by status |
| Loading state | `<div>` | `moderation-loading` | Displays while data loads |
| Error state | `<div>` | `moderation-error` | Displays loading errors |
| Empty state | `<div>` | `moderation-empty` | Displays when no resources require review |

### Expected Behaviour

- Retrieve resources that the moderator is authorized to review.
- Display relevant resource information.
- Allow filtering using supported review statuses.
- Allow moderators to open individual submissions.
- Display loading, error and empty states.

Additional dashboard information, such as moderation statistics or reported-content summaries, may be added if included in the finalized requirements.

## 4. Moderation Queue

The moderation queue displays resource submissions requiring moderator attention.

### Required Element IDs

| Element | ID Pattern | Purpose |
|---|---|---|
| Queue resource card | `moderation-resource-card-{resourceId}` | Displays one submission |
| Resource title | `moderation-resource-title-{resourceId}` | Displays resource title |
| Resource type | `moderation-resource-type-{resourceId}` | Displays resource category |
| Contributor name | `resource-contributor-{resourceId}` | Displays contributor information |
| Submission date | `resource-submission-date-{resourceId}` | Displays submission date |
| Review status | `moderation-resource-status-{resourceId}` | Displays current status |
| Review button | `btn-review-resource-{resourceId}` | Opens review details |

### Expected Information

Each queue card may display:

- Resource title.
- Resource type.
- Subject and topic.
- Contributor information where permitted.
- Submission date.
- Current review status.

The frontend must display information supplied by the backend.

## 5. Resource Review Details Page

The Resource Review Details page allows a moderator to inspect an individual resource before taking action.

### Required Element IDs

| Category | Element Type | Required ID | Purpose |
|---|---|---|---|
| Page container | `<main>` | `resource-review-page` | Main review page |
| Page heading | `<h1>` | `resource-review-title` | Displays review page title |
| Resource title | `<h2>` | `review-resource-name` | Displays resource name |
| Resource description | `<p>` | `review-resource-description` | Displays description |
| Resource type | `<span>` | `review-resource-type` | Displays category |
| Subject | `<span>` | `review-resource-subject` | Displays associated subject |
| Topic | `<span>` | `review-resource-topic` | Displays associated topic |
| Resource link | `<a>` | `review-resource-link` | Opens submitted resource |
| Contributor details | `<section>` | `review-contributor-details` | Displays contributor information |
| Review status | `<span>` | `review-current-status` | Displays current review status |

### Expected Behaviour

- Display the selected resource's information.
- Allow the moderator to inspect the submitted content.
- Display contributor and submission information where permitted.
- Display the current review status.
- Provide available moderation actions.
- Display reviewer feedback when available.

## 6. Moderation Actions

Authorized moderators should be able to perform the following actions.

### A. Approve Resource

Approving a resource marks it as accepted according to the backend review workflow.

| Element | Required ID | Purpose |
|---|---|---|
| Approve button | `btn-approve-resource` | Approves the resource |

Expected behaviour:

- Allow the moderator to initiate approval.
- Submit the approval action to the backend.
- Display success or error feedback.
- Refresh the displayed review status after success.

### B. Reject Resource

Rejecting a resource marks it as unsuitable for publication according to the review rules.

| Element | Required ID | Purpose |
|---|---|---|
| Reject button | `btn-reject-resource` | Rejects the resource |
| Rejection reason | `reject-resource-reason` | Accepts rejection feedback |
| Rejection confirmation | `btn-confirm-rejection` | Confirms rejection |

Expected behaviour:

- Allow the moderator to provide a rejection reason where required.
- Submit the rejection action.
- Display the result.
- Update the resource status after successful processing.

### C. Request Changes

Requesting changes allows a moderator to send feedback to the contributor so that the resource can be corrected.

| Element | Required ID | Purpose |
|---|---|---|
| Request changes button | `btn-request-resource-changes` | Starts change request |
| Feedback field | `review-feedback` | Accepts reviewer feedback |
| Submit feedback button | `btn-submit-review-feedback` | Sends feedback |

Expected behaviour:

- Allow the moderator to enter clear feedback.
- Submit the requested changes.
- Display the result.
- Update the review status after success.

The exact mandatory fields and review transition rules must be confirmed with the backend.

## 7. Review Status

The moderation interface should display the status returned by the backend.

The proposed status categories are:

| Status | Meaning |
|---|---|
| `PENDING` | Resource is awaiting review |
| `UNDER_REVIEW` | Resource is currently being reviewed |
| `APPROVED` | Resource has been approved |
| `REJECTED` | Resource has been rejected |
| `CHANGES_REQUESTED` | Contributor must make requested changes |

### Required Element IDs

| Element | ID Pattern | Purpose |
|---|---|---|
| Status badge | `review-status-{resourceId}` | Displays current review status |
| Feedback display | `review-feedback-{resourceId}` | Displays available reviewer feedback |

### Status Behaviour

- Display the current status supplied by the backend.
- Use consistent styling for each status.
- Update the displayed status after successful moderation actions.
- Do not independently determine or change review status in the frontend.

The backend controls valid status transitions.

## 8. Reported Content

EduMesh may include moderation functionality for resources reported by users.

If included in the finalized scope, the moderation interface may provide:

- A list of reported resources.
- Report reasons.
- Report counts or relevant report information.
- Resource details.
- Available moderator actions.

The exact reporting workflow, categories, permissions and endpoints must be confirmed with backend development.

Reported-content handling should not be treated as a fully finalized feature until those requirements are agreed.

## 9. React Components

| Component | Responsibility |
|---|---|
| `ModeratorDashboardPage` | Displays the moderation dashboard |
| `ModerationQueue` | Displays submissions requiring review |
| `ModerationResourceCard` | Displays one resource in the queue |
| `ResourceReviewPage` | Displays individual resource review details |
| `ResourceReviewDetails` | Displays resource information for evaluation |
| `ReviewStatusBadge` | Displays the current review status |
| `ReviewFeedbackForm` | Collects moderator feedback |

Additional components may be introduced when required.

## 10. Proposed Frontend Routes

| Route | Purpose |
|---|---|
| `/moderation` | Displays the moderator dashboard |
| `/moderation/resources/:resourceId` | Displays individual resource review details |

Both routes must be protected using the application authentication and role-based routing system.

The moderator dashboard and review details page are separate views.

## 11. Proposed Backend API Endpoints

The following endpoints are proposed for backend coordination.

| Operation | Method | Proposed Endpoint |
|---|---|---|
| Get moderation queue | GET | `/api/moderation/resources` |
| Approve resource | PATCH | `/api/moderation/resources/:resourceId/approve` |
| Reject resource | PATCH | `/api/moderation/resources/:resourceId/reject` |
| Request changes | PATCH | `/api/moderation/resources/:resourceId/request-changes` |

These endpoint paths are proposed and must be confirmed during backend implementation.

### A. Get Moderation Queue

**Endpoint:** `GET /api/moderation/resources`

Purpose: Retrieve resources that the authenticated moderator is authorized to review.

Suggested query parameters:

- `status`
- `page`
- `limit`

### B. Approve Resource

**Endpoint:** `PATCH /api/moderation/resources/:resourceId/approve`

Purpose: Submit an approval action for a selected resource.

### C. Reject Resource

**Endpoint:** `PATCH /api/moderation/resources/:resourceId/reject`

Purpose: Submit a rejection action and the required rejection information.

### D. Request Changes

**Endpoint:** `PATCH /api/moderation/resources/:resourceId/request-changes`

Purpose: Send reviewer feedback and request corrections from the contributor.

Final request bodies, response formats and permission rules must be documented in the shared API contract.

## 12. Expected UI States

The frontend should handle:

- Moderation dashboard loading.
- Empty review queue.
- Moderation queue errors.
- Individual resource loading.
- Resource unavailable or inaccessible.
- Approval processing.
- Rejection processing.
- Change request processing.
- Successful moderation action.
- Failed moderation action.
- Permission errors.
- Existing review feedback.

## 13. Frontend Testing Checklist

Before marking the Reviews module complete, verify:

- [ ] Moderator dashboard displays correctly.
- [ ] Only authorized users can access moderation routes.
- [ ] Moderation queue loads correctly.
- [ ] Resource information displays correctly.
- [ ] Review status displays correctly.
- [ ] Individual resource review page works.
- [ ] Approve action works with mock responses.
- [ ] Reject action works with mock responses.
- [ ] Rejection feedback is handled correctly.
- [ ] Request-changes action works with mock responses.
- [ ] Reviewer feedback displays correctly.
- [ ] Status updates display correctly after actions.
- [ ] Loading, error and empty states work correctly.
- [ ] All agreed element IDs are present and unique.

## 14. Independent Frontend Development

Divya can develop the moderation interface using mock submissions while backend moderation APIs are being implemented.

Mock data should include:

- Pending resources.
- Resources under review.
- Approved resources.
- Rejected resources.
- Resources with requested changes.
- Contributor information.
- Reviewer feedback.

During development:

- Keep API requests inside `reviewService.js`.
- Use mock data for independent frontend testing.
- Do not independently determine review status transitions.
- Do not assume a user has moderator permissions based only on frontend state.
- Follow the backend authorization rules and API contracts during integration.

Joint integration should happen when the backend moderation endpoints and review workflow are ready.

---

**Reviews and Moderation Module Status:** Core moderator interface and review actions documented. Final moderator permissions, status transitions, rejection requirements, reported-content workflow and API contracts require backend confirmation.
