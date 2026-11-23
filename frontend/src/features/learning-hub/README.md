# Learning Hub Module — Frontend

## 1. Module Overview

The Learning Hub is the main educational resource discovery module of EduMesh.

It allows NST students to explore their syllabus, browse subjects and topics, and access learning materials from different sources.

The module should help students find relevant learning resources without having to search across multiple platforms independently.

Students should be able to:

- Browse available NST subjects.
- Explore topics within each subject.
- View learning resources associated with topics.
- Access notes and study materials.
- Watch relevant YouTube videos.
- Access external tutorials and learning websites.
- Search for learning resources.
- Filter resources using available categories.
- View the top three eligible YouTube videos for each topic.
- Open individual resource details.
- View resource ratings and feedback where available.

The frontend is responsible for displaying and organizing learning content.

The backend is responsible for retrieving approved resources, associating resources with subjects and topics, and determining resource rankings.

## 2. Planned Folder Structure

```text
learning-hub/
│
├── README.md
│
├── components/
│   ├── SubjectCard.jsx
│   ├── TopicCard.jsx
│   ├── ResourceCard.jsx
│   ├── SearchBar.jsx
│   └── ResourceFilters.jsx
│
├── pages/
│   ├── LearningHubPage.jsx
│   ├── SubjectDetailsPage.jsx
│   ├── TopicDetailsPage.jsx
│   └── ResourceDetailsPage.jsx
│
├── services/
│   └── learningHubService.js
│
└── hooks/
```

This is the proposed organization. Additional files may be introduced when required.

## 3. Learning Hub Main Page

The Learning Hub main page allows students to explore available subjects.

### Required Element IDs

| Category | Element Type | Required ID | Purpose |
|---|---|---|---|
| Page container | `<main>` | `learning-hub-page` | Main Learning Hub page |
| Page heading | `<h1>` | `learning-hub-title` | Displays page title |
| Subject section | `<section>` | `subject-section` | Contains available subjects |
| Subject list | `<div>` | `subject-grid` | Displays subject cards |
| Search input | `<input>` | `learning-search-input` | Accepts search keywords |
| Search button | `<button>` | `btn-learning-search` | Starts a search |
| Filter section | `<section>` | `resource-filter-section` | Contains resource filters |
| Loading state | `<div>` | `learning-hub-loading` | Displays loading information |
| Error state | `<div>` | `learning-hub-error` | Displays loading errors |
| Empty state | `<div>` | `learning-hub-empty` | Displays when no content is available |

### Subject Card IDs

| Element | ID Pattern | Purpose |
|---|---|---|
| Subject card | `subject-card-{subjectId}` | Displays one subject |
| Subject name | `subject-name-{subjectId}` | Displays subject name |
| Subject description | `subject-description-{subjectId}` | Displays subject description |
| Subject button | `btn-view-subject-{subjectId}` | Opens subject details |

### Expected Behaviour

- Retrieve available subjects from the backend.
- Display subjects in a clear layout.
- Allow students to open individual subjects.
- Display appropriate loading, error and empty states.
- Use backend-provided subject information.

## 4. Subject Details Page

The Subject Details page displays information about a selected subject and its associated topics.

### Required Element IDs

| Category | Element Type | Required ID | Purpose |
|---|---|---|---|
| Page container | `<main>` | `subject-details-page` | Main subject details page |
| Subject title | `<h1>` | `subject-details-title` | Displays subject name |
| Subject description | `<p>` | `subject-details-description` | Displays subject description |
| Topic section | `<section>` | `subject-topics-section` | Contains subject topics |
| Topic list | `<div>` | `subject-topic-list` | Displays available topics |
| Loading state | `<div>` | `subject-details-loading` | Displays while loading |
| Error state | `<div>` | `subject-details-error` | Displays loading errors |

### Topic Card IDs

| Element | ID Pattern | Purpose |
|---|---|---|
| Topic card | `topic-card-{topicId}` | Displays one topic |
| Topic name | `topic-name-{topicId}` | Displays topic name |
| Topic description | `topic-description-{topicId}` | Displays topic description |
| Topic button | `btn-view-topic-{topicId}` | Opens topic details |

### Expected Behaviour

- Display the selected subject's information.
- Retrieve topics associated with the subject.
- Allow students to open individual topics.
- Handle subjects with no available topics.

## 5. Topic Details Page

The Topic Details page displays learning resources associated with a selected topic.

### Required Element IDs

| Category | Element Type | Required ID | Purpose |
|---|---|---|---|
| Page container | `<main>` | `topic-details-page` | Main topic details page |
| Topic title | `<h1>` | `topic-details-title` | Displays topic name |
| Topic description | `<p>` | `topic-details-description` | Displays topic description |
| Resource section | `<section>` | `topic-resources-section` | Contains learning resources |
| Resource list | `<div>` | `topic-resource-list` | Displays resources |
| Video section | `<section>` | `top-videos-section` | Contains top YouTube videos |
| Loading state | `<div>` | `topic-details-loading` | Displays while loading |
| Error state | `<div>` | `topic-details-error` | Displays errors |
| Empty state | `<div>` | `topic-details-empty` | Displays when no resources exist |

### Expected Behaviour

- Display the selected topic's information.
- Retrieve approved learning resources associated with the topic.
- Organize resources by their type.
- Display eligible YouTube videos.
- Allow students to open resource details.
- Handle topics without available resources.

## 6. Learning Resource Cards

Resource cards display individual learning materials.

### Supported Resource Categories

- Notes and study materials.
- YouTube videos.
- External tutorials.
- Other approved educational resources.

### Required Element IDs

| Element | ID Pattern | Purpose |
|---|---|---|
| Resource card | `resource-card-{resourceId}` | Displays one resource |
| Resource title | `resource-title-{resourceId}` | Displays resource title |
| Resource type | `resource-type-{resourceId}` | Displays resource category |
| Resource description | `resource-description-{resourceId}` | Displays resource description |
| Resource rating | `resource-rating-{resourceId}` | Displays average rating |
| Rating count | `resource-rating-count-{resourceId}` | Displays number of ratings |
| Open resource button | `btn-open-resource-{resourceId}` | Opens resource details or destination |

### Expected Information

Each resource card may display:

- Resource title.
- Resource description.
- Resource type.
- Source or provider.
- Average rating.
- Number of ratings.
- Relevant thumbnail where available.

The frontend must display the resource information supplied by the backend.

## 7. Search and Filtering

The Learning Hub should help students find relevant learning materials efficiently.

### Search Functionality

Students should be able to search using relevant keywords.

Search may cover:

- Subject names.
- Topic names.
- Resource titles.
- Resource descriptions.

### Required Element IDs

| Element | Required ID | Purpose |
|---|---|---|
| Search input | `learning-search-input` | Accepts search keywords |
| Search button | `btn-learning-search` | Executes search |
| Clear search button | `btn-clear-learning-search` | Clears search input |
| Resource type filter | `resource-type-filter` | Filters by resource type |
| Subject filter | `resource-subject-filter` | Filters by subject |
| Topic filter | `resource-topic-filter` | Filters by topic |
| Sort selection | `resource-sort-select` | Selects available sorting order |
| Search results | `learning-search-results` | Displays matching results |

### Expected Behaviour

- Allow students to search using keywords.
- Display matching results.
- Support available subject and topic filters.
- Support resource type filtering.
- Support agreed sorting options.
- Display a suitable empty state when no results match.
- Preserve relevant search and filter selections when practical.

The supported filters, sorting options and query parameters must follow the final backend API contract.

## 8. Top Three YouTube Videos

EduMesh should display the top three eligible YouTube videos associated with each topic.

The backend is responsible for calculating the ranking using the agreed resource rating methodology.

### Required Element IDs

| Element | ID Pattern | Purpose |
|---|---|---|
| Top videos section | `top-videos-section` | Contains top videos |
| Video card | `top-video-card-{resourceId}` | Displays one ranked video |
| Video title | `top-video-title-{resourceId}` | Displays video title |
| Video rank | `top-video-rank-{resourceId}` | Displays ranking position |
| Video rating | `top-video-rating-{resourceId}` | Displays average rating |
| Video rating count | `top-video-rating-count-{resourceId}` | Displays rating count |
| Watch button | `btn-watch-video-{resourceId}` | Opens the video |

### Expected Behaviour

- Retrieve the top three eligible videos for the selected topic.
- Display their ranking order.
- Show average ratings and rating counts when provided.
- Allow students to open or watch the videos.
- Display fewer than three videos if fewer eligible videos exist.
- Handle topics without eligible videos.

The frontend must not independently calculate the official ranking.

The backend determines which videos qualify and their ranking order.

## 9. Resource Details Page

The Resource Details page provides more information about an individual learning resource.

It may display:

- Resource title.
- Full description.
- Resource type.
- External source information.
- Resource link or viewing option.
- Subject and topic association.
- Average rating.
- Number of ratings.
- Available feedback and comments.

Ratings and Feedback interactions are implemented through the separate Ratings feature.

### Required Element IDs

| Element | Required ID | Purpose |
|---|---|---|
| Page container | `resource-details-page` | Main resource details page |
| Resource title | `resource-details-title` | Displays resource title |
| Resource description | `resource-details-description` | Displays full description |
| Resource type | `resource-details-type` | Displays resource category |
| Resource link | `resource-external-link` | Opens external resource |
| Resource rating | `resource-details-rating` | Displays average rating |
| Rating count | `resource-details-rating-count` | Displays number of ratings |

## 10. React Components

| Component | Responsibility |
|---|---|
| `LearningHubPage` | Displays available subjects |
| `SubjectDetailsPage` | Displays subject information and topics |
| `TopicDetailsPage` | Displays topic information and resources |
| `ResourceDetailsPage` | Displays individual resource information |
| `SubjectCard` | Displays one subject |
| `TopicCard` | Displays one topic |
| `ResourceCard` | Displays one learning resource |
| `SearchBar` | Handles search input |
| `ResourceFilters` | Displays available resource filters |

Additional components may be introduced when required.

## 11. Proposed Frontend Routes

| Route | Purpose |
|---|---|
| `/learning-hub` | Displays available subjects |
| `/learning-hub/subjects/:subjectId` | Displays subject details and topics |
| `/learning-hub/topics/:topicId` | Displays topic details and resources |
| `/resources/:resourceId` | Displays individual resource details |

These routes are part of the proposed frontend routing plan and should remain consistent with the application router.

## 12. Proposed Backend API Endpoints

The following endpoints are proposed for backend coordination.

| Operation | Method | Proposed Endpoint |
|---|---|---|
| Get subjects | GET | `/api/subjects` |
| Get subject topics | GET | `/api/subjects/:subjectId/topics` |
| Get learning resources | GET | `/api/resources` |
| Get resource details | GET | `/api/resources/:resourceId` |
| Get top YouTube videos | GET | `/api/topics/:topicId/top-videos` |

The final endpoint paths, filters, query parameters and response structures must be confirmed during backend implementation.

### A. Get Subjects

**Endpoint:** `GET /api/subjects`

Purpose: Retrieve the available subjects that students can browse.

### B. Get Subject Topics

**Endpoint:** `GET /api/subjects/:subjectId/topics`

Purpose: Retrieve topics associated with a selected subject.

### C. Get Learning Resources

**Endpoint:** `GET /api/resources`

Suggested query parameters:

- `subjectId`
- `topicId`
- `type`
- `search`
- `sort`
- `page`
- `limit`

Purpose: Retrieve approved learning resources using the supported search and filter options.

### D. Get Resource Details

**Endpoint:** `GET /api/resources/:resourceId`

Purpose: Retrieve detailed information about a selected approved resource.

### E. Get Top YouTube Videos

**Endpoint:** `GET /api/topics/:topicId/top-videos`

Purpose: Retrieve the top three eligible YouTube videos associated with a topic, in backend-determined ranking order.

## 13. Expected UI States

The frontend should handle:

- Loading subjects.
- Loading subject topics.
- Loading topic resources.
- Loading resource details.
- Loading top videos.
- Successful content display.
- API errors.
- Empty subject lists.
- Topics without resources.
- No matching search results.
- Fewer than three eligible videos.
- Unavailable external resources.

## 14. Frontend Testing Checklist

Before marking Learning Hub complete, verify:

- [ ] Learning Hub page displays correctly.
- [ ] Subjects load from the backend.
- [ ] Subject cards display correctly.
- [ ] Subject details load correctly.
- [ ] Topics display under the correct subjects.
- [ ] Topic details load correctly.
- [ ] Approved learning resources display correctly.
- [ ] Resource cards display the correct information.
- [ ] Search functionality works.
- [ ] Subject filters work.
- [ ] Topic filters work.
- [ ] Resource type filters work.
- [ ] Sorting works according to the agreed contract.
- [ ] Resource details display correctly.
- [ ] Top three eligible YouTube videos display correctly.
- [ ] Backend ranking order is preserved.
- [ ] Resource links open correctly.
- [ ] Loading, error and empty states work.
- [ ] All agreed element IDs are present and unique.

## 15. Independent Frontend Development

Divya can develop the Learning Hub interface using mock subject, topic and resource data while the backend APIs are being implemented.

Mock data should include:

- Multiple subjects.
- Multiple topics per subject.
- Different resource types.
- Approved learning resources.
- YouTube
