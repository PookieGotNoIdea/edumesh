# Progress Tracking Module — Frontend

## 1. Module Overview

The Progress Tracking module helps NST students understand their learning performance and identify topics that require additional practice.

It collects and presents learning information based on students' quiz attempts, answers and learning activity.

Students should be able to:

- View their overall learning progress.
- Track performance across different subjects.
- View topic-wise performance.
- Review previous mistakes.
- Identify weak topics.
- Track improvements over time.
- View learning recommendations.
- Set and monitor learning goals.
- Track learning streaks.
- View progress through charts and visual summaries.

The frontend is responsible for displaying progress information and providing interfaces for goals and revision activities.

The backend is responsible for recording learning activity, calculating performance statistics, maintaining mistake history and determining progress statuses and recommendations.

## 2. Planned Folder Structure

```text
progress/
│
├── README.md
│
├── components/
│   ├── ProgressOverview.jsx
│   ├── SubjectProgressCard.jsx
│   ├── TopicProgressCard.jsx
│   ├── ProgressChart.jsx
│   ├── MistakeHistoryList.jsx
│   ├── MistakeCard.jsx
│   ├── WeakTopicsList.jsx
│   ├── RecommendationCard.jsx
│   ├── LearningGoalCard.jsx
│   └── StreakCard.jsx
│
├── pages/
│   ├── ProgressDashboardPage.jsx
│   ├── SubjectProgressPage.jsx
│   ├── MistakeHistoryPage.jsx
│   └── LearningGoalsPage.jsx
│
├── services/
│   └── progressService.js
│
└── hooks/
    └── useProgress.js
```

This is the proposed folder structure. Additional files may be introduced when implementation requires them.

## 3. Progress Dashboard

The Progress Dashboard provides an overview of a student's learning performance.

### Required Element IDs

| Element | Required ID | Purpose |
|---|---|---|
| Progress page | `progress-dashboard-page` | Main progress interface |
| Progress overview | `progress-overview` | Displays overall statistics |
| Overall progress | `overall-progress` | Displays overall progress information |
| Subject progress list | `subject-progress-list` | Displays subject-wise performance |
| Weak topics section | `weak-topics-section` | Displays topics needing attention |
| Recommendations section | `progress-recommendations` | Displays learning recommendations |
| Streak section | `learning-streak-section` | Displays learning streak information |
| Loading state | `progress-loading` | Displays loading feedback |
| Empty state | `progress-empty` | Displays when progress is unavailable |
| Error state | `progress-error` | Displays progress loading errors |

### Expected Information

The dashboard should display relevant statistics, such as:

- Overall quiz performance.
- Subject-wise performance.
- Topic-wise performance summaries.
- Number of completed attempts.
- Weak topics.
- Recent learning activity.
- Learning streak information.
- Recommended topics for revision.

Only statistics supported by the backend response should be displayed.

## 4. Subject-Wise Progress

Students should be able to understand their performance separately for each subject.

### Required Element IDs

| Element | Required ID | Purpose |
|---|---|---|
| Subject progress page | `subject-progress-page` | Displays subject performance |
| Subject title | `progress-subject-title` | Displays selected subject |
| Subject summary | `subject-progress-summary` | Displays subject statistics |
| Topic progress list | `topic-progress-list` | Displays topic performance |
| Subject performance chart | `subject-performance-chart` | Visualizes performance |

### Expected Behaviour

- Display available subjects.
- Show performance information for each subject.
- Display topic-level performance within a subject.
- Allow students to navigate to a subject's progress details.
- Display relevant weak topics and improvement information.

## 5. Topic-Wise Progress

Topic-wise progress helps students identify exactly which concepts need more attention.

### Required Information

- Topic name.
- Performance information.
- Quiz attempt statistics.
- Correct and incorrect answer information, where available.
- Progress status.
- Related recommendations.

### Progress Statuses

The project currently plans to use the following four progress statuses:

| Status | Meaning |
|---|---|
| `NEW` | The student has not established sufficient learning history for the topic |
| `NEEDS_PRACTICE` | The student needs additional practice |
| `IMPROVING` | The student's performance is showing improvement |
| `MASTERED` | The student has demonstrated the required level of performance |

The backend must determine when a topic moves between these statuses.

The frontend should display the status returned by the backend rather than independently assigning it.

Suggested element IDs:

- `topic-progress-card-{topicId}`
- `topic-progress-status-{topicId}`
- `topic-performance-{topicId}`

## 6. Mistake History

The Mistake History feature allows students to review questions they answered incorrectly during previous quiz attempts.

It supports learning through identifying and revisiting mistakes.

### Required Element IDs

| Element | Required ID | Purpose |
|---|---|---|
| Mistake history page | `mistake-history-page` | Main mistake history interface |
| Mistake list | `mistake-history-list` | Displays previous mistakes |
| Subject filter | `mistake-subject-filter` | Filters mistakes by subject |
| Topic filter | `mistake-topic-filter` | Filters mistakes by topic |
| Date filter | `mistake-date-filter` | Filters mistakes by date |
| Status filter | `mistake-status-filter` | Filters by learning status |
| Search field | `mistake-search` | Searches mistake history |
| Empty state | `mistake-history-empty` | Displays when no mistakes exist |
| Loading state | `mistake-history-loading` | Displays loading feedback |
| Error state | `mistake-history-error` | Displays loading errors |

### Individual Mistake Information

Each mistake entry should display available information such as:

- Question.
- Subject and topic.
- Student's submitted answer.
- Correct answer, where permitted.
- Associated quiz attempt.
- Date of the attempt.
- Explanation, where available.
- Current progress status.

Suggested IDs:

- `mistake-card-{mistakeId}`
- `mistake-question-{mistakeId}`
- `mistake-topic-{mistakeId}`
- `mistake-status-{mistakeId}`
- `btn-review-mistake-{mistakeId}`

### Expected Behaviour

- Display mistakes from previous attempts.
- Allow filtering by subject, topic, date and status.
- Allow students to review the original question.
- Display explanations where available.
- Provide access to a supported retry or practice flow.

The backend must determine which answers qualify as mistakes and how repeated mistakes are recorded.

## 7. Weak Topics

The Weak Topics section highlights topics where students may need additional practice.

### Expected Behaviour

- Display topics identified as requiring improvement.
- Show relevant performance information.
- Display the current progress status.
- Provide access to the relevant Learning Hub topic or practice quiz.
- Refresh information when new progress data becomes available.

Suggested element IDs:

- `weak-topics-section`
- `weak-topic-card-{topicId}`
- `weak-topic-performance-{topicId}`
- `btn-practice-weak-topic-{topicId}`

The backend must determine which topics qualify as weak topics.

## 8. Progress Charts and Visualizations

Charts should help students understand their performance over time.

The frontend will use **Recharts** for progress visualizations.

Possible charts include:

### A. Subject Performance Chart

Displays performance across different subjects.

### B. Topic Performance Chart

Displays performance across topics within a subject.

### C. Performance Trend Chart

Shows changes in quiz performance over time.

### D. Mistake Trend Chart

Shows changes in mistakes across available time periods.

### Expected Behaviour

- Display charts using backend-provided data.
- Use clear labels and legends.
- Display tooltips where useful.
- Handle empty datasets.
- Adapt to different screen sizes.
- Avoid misleading visual representations.

The frontend should not invent missing historical data or independently calculate official performance statistics.

## 9. Learning Recommendations

The system should provide recommendations that help students decide what to study next.

Recommendations may include:

- Revisiting weak topics.
- Practising questions from topics with low performance.
- Reviewing previous mistakes.
- Continuing with topics where improvement is needed.

The initial project approach uses rule-based recommendations rather than requiring AI.

The backend should determine the recommendation logic and return the relevant recommendations.

### Required Element IDs

| Element | Required ID | Purpose |
|---|---|---|
| Recommendation section | `recommendations-section` | Contains recommendations |
| Recommendation list | `recommendations-list` | Displays recommendations |
| Recommendation card | `recommendation-card-{recommendationId}` | Displays one recommendation |
| Recommendation action | `btn-recommendation-action-{recommendationId}` | Opens the suggested activity |

The frontend should display the recommendations and navigate to their associated learning or practice interfaces.

## 10. Learning Goals

Students should be able to set and monitor personal learning goals.

Examples of possible goals include:

- Completing a target number of quiz attempts.
- Practising a particular topic.
- Improving performance in a subject.
- Completing a defined learning activity.

### Required Element IDs

| Element | Required ID | Purpose |
|---|---|---|
| Goals page | `learning-goals-page` | Main learning goals interface |
| Goal list | `learning-goals-list` | Displays existing goals |
| Goal form | `learning-goal-form` | Creates or edits a goal |
| Goal title | `learning-goal-title` | Accepts goal title |
| Goal type | `learning-goal-type` | Selects goal category |
| Goal target | `learning-goal-target` | Defines target value |
| Goal deadline | `learning-goal-deadline` | Defines deadline where supported |
| Save button | `btn-save-learning-goal` | Saves the goal |
| Empty state | `learning-goals-empty` | Displays when no goals exist |

### Expected Behaviour

- Display existing learning goals.
- Allow students to create goals.
- Allow students to update goals where supported.
- Display goal progress.
- Display completion status.
- Allow students to remove goals where supported.

The backend must define goal types, validation, progress calculation and completion rules.

## 11. Learning Streaks

Learning streaks encourage students to maintain consistent learning activity.

### Expected Information

- Current streak.
- Longest streak.
- Relevant activity history, where available.

Suggested element IDs:

- `learning-streak-card`
- `current-learning-streak`
- `longest-learning-streak`

The backend must determine what activity qualifies for a streak and how consecutive days are calculated.

The frontend should only display the values returned by the backend.

## 12. React Components

| Component | Responsibility |
|---|---|
| `ProgressOverview` | Displays overall learning statistics |
| `SubjectProgressCard` | Displays subject-wise performance |
| `TopicProgressCard` | Displays topic-level progress |
| `ProgressChart` | Displays performance visualizations |
| `MistakeHistoryList` | Displays previous mistakes |
| `MistakeCard` | Displays an individual mistake |
| `WeakTopicsList` | Displays topics requiring practice |
| `RecommendationCard` | Displays a learning recommendation |
| `LearningGoalCard` | Displays an individual learning goal |
| `StreakCard` | Displays learning streak information |

Additional components may be introduced when required.

## 13. Proposed Frontend Routes

The current routing plan includes:

| Route | Purpose |
|---|---|
| `/progress` | Main progress dashboard |
| `/progress/subjects/:subjectId` | Subject-specific progress |
| `/progress/mistakes` | Mistake history |
| `/progress/goals` | Learning goals |

These routes should be accessible according to the agreed authentication and authorization rules.

## 14. Proposed Backend API Endpoints

The following endpoints are proposed for backend coordination. They are not final API contracts.

| Operation | Method | Proposed Endpoint |
|---|---|---|
| Get progress overview | GET | `/api/progress/overview` |
| Get subject progress | GET | `/api/progress/subjects` |
| Get specific subject progress | GET | `/api/progress/subjects/:subjectId` |
| Get topic progress | GET | `/api/progress/topics/:topicId` |
| Get mistake history | GET | `/api/progress/mistakes` |
| Get weak topics | GET | `/api/progress/weak-topics` |
| Get recommendations | GET | `/api/progress/recommendations` |
| Get learning goals | GET | `/api/progress/goals` |
| Create learning goal | POST | `/api/progress/goals` |
| Update learning goal | PATCH | `/api/progress/goals/:goalId` |
| Delete learning goal | DELETE | `/api/progress/goals/:goalId` |
| Get learning streak | GET | `/api/progress/streak` |

Final endpoint paths, query parameters, request bodies, response structures and permissions must be confirmed during backend development.

## 15. Frontend Service Layer

All progress-related API requests should be organized in:

`services/progressService.js`

The service should contain functions for:

- Fetching the progress overview.
- Fetching subject progress.
- Fetching topic progress.
- Fetching mistake history.
- Fetching weak topics.
- Fetching recommendations.
- Fetching learning goals.
- Creating learning goals.
- Updating learning goals.
- Deleting learning goals.
- Fetching learning streak information.

Components should use the service layer through the agreed feature hooks or event handlers rather than embedding API request logic directly.

## 16. Expected UI States

The frontend should handle:

- Progress dashboard loading.
- No progress data available.
- Subject progress loading.
- Topic progress loading.
- Mistake history loading.
- No mistakes available.
- Weak topics loading.
- No weak topics identified.
- Recommendations loading.
- No recommendations available.
- Goal creation and update.
- Goal validation errors.
- Goal deletion confirmation.
- Streak information loading.
- API errors.

## 17. Frontend Testing Checklist

Before marking the module complete, verify:

- [ ] Progress dashboard displays correctly.
- [ ] Overall progress information is displayed.
- [ ] Subject-wise performance displays correctly.
- [ ] Topic-wise performance displays correctly.
- [ ] All four progress statuses display correctly.
- [ ] Mistake history displays previous mistakes.
- [ ] Mistake filters work.
- [ ] Mistake details display correctly.
- [ ] Weak topics display correctly.
- [ ] Learning recommendations display correctly.
- [ ] Progress charts render correctly.
- [ ] Charts handle empty datasets.
- [ ] Learning goals can be created with mock responses.
- [ ] Learning goals can be updated with mock responses.
- [ ] Learning goals can be deleted with mock responses.
- [ ] Goal progress and completion status display correctly.
- [ ] Learning streak information displays correctly.
- [ ] Loading, empty and error states work.
- [ ] All agreed element IDs are present and unique.

## 18. Independent Frontend Development

Divya can develop the Progress Tracking interface using mock data while the backend progress calculations and APIs are being implemented.

Mock data should cover:

- Students with no quiz history.
- Students with completed quiz attempts.
- Different subject performance values.
- Different topic performance values.
- All four progress statuses.
- Students with multiple mistakes.
- Students with no mistakes.
- Weak topics.
- Different learning recommendations.
- Learning goals in progress and completed states.
- Different streak values.
- Historical performance data for charts.

During development:

- Keep progress API requests inside `progressService.js`.
- Use mock data for independent frontend testing.
- Use Recharts for visualizations.
- Do not calculate official progress statuses in the frontend.
- Do not independently determine weak topics.
- Do not independently calculate recommendations or streaks.
- Follow backend-provided progress information.
- Keep progress components inside the progress feature.

Notification display and notification management belong to the separate Notifications feature.

Joint integration should begin after the backend progress and learning-goal contracts are ready.

---

**Progress Tracking Module Status:** Core dashboard, subject and topic performance, mistake history, progress statuses, weak topics, charts, recommendations, goals and streak requirements documented. Final calculation rules, thresholds, goal logic and API contracts require backend confirmation.
