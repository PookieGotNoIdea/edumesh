# Ratings and Feedback Module — Frontend

## 1. Module Overview

The Ratings and Feedback module allows authenticated NST students to share their opinions about educational resources available on EduMesh.

It helps students identify useful learning materials through ratings and feedback submitted by other users.

Students should be able to:

- Give a resource a rating from 1 to 5 stars.
- Update their existing rating.
- View the average rating of a resource.
- View the total number of ratings.
- View rating distributions.
- Submit comments about resources.
- View comments submitted by other students.
- Mark comments as helpful.
- Report inappropriate or misleading content.
- View resource ranking information where available.

The frontend is responsible for displaying rating and feedback interfaces and sending user interactions to the backend.

The backend is responsible for storing ratings, enforcing rating permissions, calculating rating statistics, managing comments and reports, and determining resource rankings.

## 2. Planned Folder Structure

```text
ratings/
│
├── README.md
│
├── components/
│   ├── RatingStars.jsx
│   ├── RatingSummary.jsx
│   ├── RatingDistribution.jsx
│   ├── CommentForm.jsx
│   ├── CommentList.jsx
│   ├── CommentCard.jsx
│   └── ReportForm.jsx
│
├── pages/
│
├── services/
│   └── ratingService.js
│
└── hooks/
```

This is the proposed organization. Additional files may be introduced when required.

Rating and feedback components will mainly be displayed within the Learning Hub and Resource Details interfaces. Separate rating pages are not required in the initial page plan.

## 3. Star Rating Interface

Students should be able to rate an educational resource using a 1–5 star rating system.

### Required Element IDs

| Category | Element Type | Required ID | Purpose |
|---|---|---|---|
| Rating section | `<section>` | `resource-rating-section` | Contains rating information |
| Rating form | `<form>` | `resource-rating-form` | Handles rating submission |
| Star 1 | Interactive element | `rating-star-1` | Selects one star |
| Star 2 | Interactive element | `rating-star-2` | Selects two stars |
| Star 3 | Interactive element | `rating-star-3` | Selects three stars |
| Star 4 | Interactive element | `rating-star-4` | Selects four stars |
| Star 5 | Interactive element | `rating-star-5` | Selects five stars |
| Submit button | `<button>` | `btn-submit-rating` | Submits the rating |
| Error message | `<div>` | `rating-error` | Displays rating errors |
| Success message | `<div>` | `rating-success` | Displays success feedback |

### Rating Behaviour

- Allow authenticated NST students to select a rating from 1 to 5.
- Display the selected rating clearly.
- Submit the rating to the backend.
- Allow a student to update their existing rating.
- Display appropriate success and error feedback.
- Prevent repeated submission while processing.

Each student should have one current rating per resource. A new rating should replace the student's previous rating rather than create another independent rating.

Students do not need verified usage of a resource to submit a rating, according to the agreed project requirements.

## 4. Rating Summary

The rating summary displays the overall rating information for a resource.

### Required Element IDs

| Element | Required ID | Purpose |
|---|---|---|
| Rating summary | `rating-summary` | Contains rating statistics |
| Average rating | `average-resource-rating` | Displays average rating |
| Total rating count | `total-resource-ratings` | Displays number of ratings |
| Rating distribution | `rating-distribution` | Contains rating breakdown |
| Five-star count | `rating-count-5` | Displays five-star rating count |
| Four-star count | `rating-count-4` | Displays four-star rating count |
| Three-star count | `rating-count-3` | Displays three-star rating count |
| Two-star count | `rating-count-2` | Displays two-star rating count |
| One-star count | `rating-count-1` | Displays one-star rating count |

### Expected Behaviour

Display:

- Average rating.
- Total number of ratings.
- Rating distribution from one to five stars.

All official rating statistics must come from the backend.

The frontend should not independently calculate official rating summaries.

## 5. Weighted Rating and Resource Ranking

EduMesh uses a proposed weighted rating approach to reduce the influence of resources with very few ratings.

The agreed formula is:

\[
WR=\frac{v}{v+m}R+\frac{m}{v+m}C
\]

Where:

| Symbol | Meaning |
|---|---|
| `WR` | Weighted rating |
| `R` | Resource's average rating |
| `v` | Number of ratings received by the resource |
| `m` | Minimum rating threshold |
| `C` | Overall average rating across eligible resources |

### Frontend Responsibilities

- Display the average rating supplied by the backend.
- Display the number of ratings.
- Preserve the ranking order returned by the backend.
- Display ranking information where required.

The backend must calculate the weighted rating and determine the resource ranking.

The minimum threshold `m` is not finalized and must be confirmed during backend development.

## 6. Comments and Feedback

Students should be able to provide written feedback about educational resources.

### Required Element IDs

| Category | Element Type | Required ID | Purpose |
|---|---|---|---|
| Comments section | `<section>` | `resource-comments-section` | Contains comments |
| Comment form | `<form>` | `resource-comment-form` | Submits a comment |
| Comment input | `<textarea>` | `resource-comment-input` | Accepts comment text |
| Submit button | `<button>` | `btn-submit-comment` | Submits the comment |
| Comment list | `<div>` | `resource-comment-list` | Displays comments |
| Loading state | `<div>` | `comments-loading` | Indicates comment loading |
| Error state | `<div>` | `comments-error` | Displays comment errors |
| Empty state | `<div>` | `comments-empty` | Displays when no comments exist |

### Individual Comment IDs

| Element | ID Pattern | Purpose |
|---|---|---|
| Comment card | `comment-card-{commentId}` | Displays one comment |
| Comment author | `comment-author-{commentId}` | Displays author information |
| Comment text | `comment-text-{commentId}` | Displays comment content |
| Comment date | `comment-date-{commentId}` | Displays submission date |
| Helpful count | `comment-helpful-count-{commentId}` | Displays helpful votes |
| Helpful button | `btn-helpful-comment-{commentId}` | Marks a comment helpful |

### Expected Behaviour

- Allow authenticated students to submit comments.
- Display available comments.
- Display author and submission information where permitted.
- Display helpful vote counts.
- Allow students to mark comments as helpful.
- Display loading, error and empty states.

Comment length limits, editing rules, deletion rules and moderation requirements must be confirmed with the backend.

## 7. Helpful Votes

Students should be able to indicate whether a comment was helpful.

### Required Element IDs

| Element | ID Pattern | Purpose |
|---|---|---|
| Helpful button | `btn-helpful-comment-{commentId}` | Submits a helpful vote |
| Helpful count | `comment-helpful-count-{commentId}` | Displays helpful vote count |

### Expected Behaviour

- Allow an authenticated student to mark a comment as helpful.
- Display the updated helpful count.
- Prevent duplicate votes according to backend rules.
- Display the user's existing vote state when available.
- Handle API errors appropriately.

The backend must enforce the helpful-voting rules.

## 8. Reporting Resources and Comments

Students should be able to report inappropriate, misleading or otherwise problematic educational content.

### Required Element IDs

| Category | Element Type | Required ID | Purpose |
|---|---|---|---|
| Report button | `<button>` | `btn-report-resource` | Opens resource report form |
| Report form | `<form>` | `resource-report-form` | Submits a report |
| Report category | `<select>` | `resource-report-category` | Selects report reason |
| Report description | `<textarea>` | `resource-report-description` | Provides additional details |
| Submit button | `<button>` | `btn-submit-resource-report` | Submits report |
| Error message | `<div>` | `resource-report-error` | Displays report errors |
| Success message | `<div>` | `resource-report-success` | Displays submission feedback |

### Expected Behaviour

- Allow authenticated students to report eligible content.
- Display available report categories.
- Allow additional details where supported.
- Submit the report to the backend.
- Display success or error feedback.

The final report categories, duplicate-report rules and moderation workflow must be confirmed during backend development.

## 9. React Components

| Component | Responsibility |
|---|---|
| `RatingStars` | Displays and collects star ratings |
| `RatingSummary` | Displays average rating and count |
| `RatingDistribution` | Displays the distribution of ratings |
| `CommentForm` | Handles comment submission |
| `CommentList` | Displays available comments |
| `CommentCard` | Displays an individual comment |
| `ReportForm` | Handles content reports |

Additional components may be introduced when required.

## 10. Frontend Integration Points

Ratings and Feedback should be integrated into existing EduMesh interfaces.

| Existing Page | Integration |
|---|---|
| Learning Hub | Displays rating information on resource cards where appropriate |
| Topic Details | Displays resource ratings and ranking information |
| Resource Details | Provides the main rating, comment and reporting interface |
| Moderator Dashboard | May display relevant reports if included in the moderation workflow |

A separate primary Ratings page is not required in the initial page plan.

The Ratings feature should maintain its own components and services even when its UI appears inside another module's page.

## 11. Proposed Backend API Endpoints

The following endpoints are proposed for backend coordination.

| Operation | Method | Proposed Endpoint |
|---|---|---|
| Get resource ratings | GET | `/api/resources/:resourceId/ratings` |
| Submit or update rating | PUT | `/api/resources/:resourceId/ratings` |
| Get resource comments | GET | `/api/resources/:resourceId/comments` |
| Submit comment | POST | `/api/resources/:resourceId/comments` |
| Mark comment helpful | POST | `/api/comments/:commentId/helpful` |
| Report resource | POST | `/api/resources/:resourceId/reports` |
| Get resource rankings | GET | `/api/resources/rankings` |

The final endpoint paths, request bodies, response structures and permissions must be confirmed during backend implementation.

### A. Get Resource Ratings

**Endpoint:** `GET /api/resources/:resourceId/ratings`

Purpose: Retrieve average rating, total rating count and rating distribution.

### B. Submit or Update Rating

**Endpoint:** `PUT /api/resources/:resourceId/ratings`

Purpose: Submit a student's rating or replace their existing rating for that resource.

The rating value must be between 1 and 5.

### C. Get Resource Comments

**Endpoint:** `GET /api/resources/:resourceId/comments`

Suggested query parameters:

- `page`
- `limit`
- `sort`

Purpose: Retrieve comments associated with a resource.

### D. Submit Comment

**Endpoint:** `POST /api/resources/:resourceId/comments`

Purpose: Submit written feedback about a resource.

### E. Mark Comment Helpful

**Endpoint:** `POST /api/comments/:commentId/helpful`

Purpose: Submit a helpful vote for a comment.

### F. Report Resource

**Endpoint:** `POST /api/resources/:resourceId/reports`

Purpose: Report an educational resource for moderation.

### G. Get Resource Rankings

**Endpoint:** `GET /api/resources/rankings`

Purpose: Retrieve resources in backend-determined ranking order.

The exact filters and ranking scope must be finalized.

## 12. Expected UI States

The frontend should handle:

- Rating submission.
- Rating update.
- Rating loading.
- Rating submission errors.
- No ratings available.
- Comment submission.
- Comment loading.
- No comments available.
- Helpful vote processing.
- Report submission.
- Report submission success.
- Report submission errors.
- Insufficient rating data.
- Resource ranking loading and empty states.

## 13. Frontend Testing Checklist

Before marking Ratings and Feedback complete, verify:

- [ ] Star rating interface displays correctly.
- [ ] Ratings from 1 to 5 can be selected.
- [ ] Rating submission works with mock responses.
- [ ] Existing ratings can be updated.
- [ ] Average rating displays correctly.
- [ ] Rating count displays correctly.
- [ ] Rating distribution displays correctly.
- [ ] Weighted ranking order is displayed correctly.
- [ ] Comments can be submitted.
- [ ] Comments display correctly.
- [ ] Helpful votes work with mock responses.
- [ ] Duplicate helpful votes are handled according to backend rules.
- [ ] Resource reporting works with mock responses.
- [ ] Report categories display correctly.
- [ ] Loading, error and empty states work.
- [ ] All agreed element IDs are present and unique.

## 14. Independent Frontend Development

Divya can develop the Ratings and Feedback interface using mock data while the backend rating and feedback APIs are being implemented.

Mock data should include:

- Resources with different average ratings.
- Different rating counts.
- Rating distributions.
- Resources with insufficient rating data.
- Multiple comments.
- Comments with different helpful counts.
- Existing student ratings.
- Available report categories.
- Different resource ranking positions.

During development:

- Keep API requests inside `ratingService.js`.
- Use mock data for independent frontend testing.
- Do not calculate official weighted ratings in the frontend.
- Do not independently decide duplicate-vote or reporting rules.
- Preserve backend-provided ranking order.
- Integrate rating components into the relevant existing pages.

Joint integration should happen after the backend rating, comment, helpful-vote and reporting contracts are ready.

---

**Ratings and Feedback Module Status:** Core rating, comment, helpful-vote, reporting and ranking display requirements documented. Minimum rating threshold, comment rules, helpful-vote rules, report categories and final API contracts require backend confirmation.
