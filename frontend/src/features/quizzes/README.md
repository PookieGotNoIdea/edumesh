# Quiz and Practice System — Frontend

## 1. Module Overview

The Quiz and Practice System allows NST students to practise concepts, test their understanding and identify areas that need improvement.

The system supports different question formats, quiz configurations and attempt types.

Students should be able to:

- Discover available quizzes.
- Practise questions from a particular topic.
- Attempt quizzes covering multiple topics.
- Answer multiple-choice questions (MCQ).
- Answer fill-in-the-blank questions.
- Answer code-output questions.
- Attempt timed and untimed quizzes.
- Receive immediate feedback or feedback after submission.
- View quiz results and answer explanations where available.
- Review previous attempts.
- Retry incorrect questions.
- Bookmark questions.
- Create custom quizzes using available options.

The frontend is responsible for presenting quiz interfaces, collecting answers and displaying backend-provided results.

The backend is responsible for question storage, answer validation, scoring, attempt management and result calculation.

## 2. Planned Folder Structure

```text
quizzes/
│
├── README.md
│
├── components/
│   ├── QuizCard.jsx
│   ├── QuizFilters.jsx
│   ├── QuizQuestion.jsx
│   ├── MCQQuestion.jsx
│   ├── FillBlankQuestion.jsx
│   ├── CodeOutputQuestion.jsx
│   ├── QuizTimer.jsx
│   ├── QuizNavigation.jsx
│   ├── QuizSummary.jsx
│   ├── QuestionExplanation.jsx
│   └── AttemptHistoryCard.jsx
│
├── pages/
│   ├── QuizListPage.jsx
│   ├── QuizAttemptPage.jsx
│   ├── QuizResultPage.jsx
│   └── QuizHistoryPage.jsx
│
├── services/
│   └── quizService.js
│
└── hooks/
    ├── useQuizAttempt.js
    └── useQuizTimer.js
```

This is the proposed structure. Additional files can be introduced when implementation requires them.

## 3. Quiz Discovery

Students should be able to discover available quizzes before starting an attempt.

### Required Element IDs

| Element | Required ID | Purpose |
|---|---|---|
| Quiz list page | `quiz-list-page` | Main quiz discovery interface |
| Quiz list | `quiz-list` | Displays available quizzes |
| Quiz search | `quiz-search` | Searches available quizzes |
| Subject filter | `quiz-subject-filter` | Filters quizzes by subject |
| Topic filter | `quiz-topic-filter` | Filters quizzes by topic |
| Difficulty filter | `quiz-difficulty-filter` | Filters by difficulty |
| Quiz type filter | `quiz-type-filter` | Filters by quiz type |
| Apply filters | `btn-apply-quiz-filters` | Applies selected filters |
| Clear filters | `btn-clear-quiz-filters` | Resets filters |
| Loading state | `quiz-list-loading` | Displays loading feedback |
| Empty state | `quiz-list-empty` | Displays when no quizzes match |
| Error state | `quiz-list-error` | Displays loading errors |

### Quiz Card

Each quiz card should provide relevant information, such as:

- Quiz title.
- Subject and topic.
- Difficulty level.
- Number of questions.
- Estimated duration, if available.
- Quiz type.
- Start or continue action, depending on the supported attempt flow.

Suggested element IDs:

| Element | ID Pattern |
|---|---|
| Quiz card | `quiz-card-{quizId}` |
| Quiz title | `quiz-title-{quizId}` |
| Quiz difficulty | `quiz-difficulty-{quizId}` |
| Question count | `quiz-question-count-{quizId}` |
| Start button | `btn-start-quiz-{quizId}` |

## 4. Supported Question Types

The system should initially support three question formats.

### A. Multiple-Choice Questions (MCQ)

Students select an answer from the available options.

Expected behaviour:

- Display the question.
- Display available answer options.
- Allow the student to select an answer.
- Clearly indicate the selected option.
- Preserve the answer while navigating between questions, according to the attempt flow.
- Submit the answer through the agreed backend API.

Suggested element IDs:

- `mcq-question-{questionId}`
- `mcq-option-{questionId}-{optionId}`
- `mcq-answer-{questionId}`

### B. Fill-in-the-Blank Questions

Students enter an answer into a text field.

Expected behaviour:

- Display the question with the required blank.
- Provide an appropriate answer input.
- Validate required input before submission where applicable.
- Send the answer to the backend.
- Display backend-provided correctness feedback.

Suggested element IDs:

- `fill-blank-question-{questionId}`
- `fill-blank-input-{questionId}`
- `btn-submit-fill-blank-{questionId}`

### C. Code-Output Questions

Students answer questions that require understanding or predicting the output of a code snippet.

Expected behaviour:

- Display the code snippet clearly.
- Display the associated question.
- Provide an answer input or selection interface according to the question format.
- Submit the student's answer to the backend.
- Display the returned result and explanation where available.

Suggested element IDs:

- `code-output-question-{questionId}`
- `code-output-snippet-{questionId}`
- `code-output-answer-{questionId}`
- `btn-submit-code-output-{questionId}`

The frontend should not independently execute submitted code unless a separate code-execution feature is explicitly designed and approved.

## 5. Quiz Configuration

The system should support different ways of practising.

### Topic-Based Quizzes

Students can attempt quizzes associated with a particular subject or topic.

### Mixed-Topic Quizzes

Students can practise questions from multiple topics.

### Timed and Untimed Quizzes

- Timed quizzes display a countdown.
- Untimed quizzes allow students to practise without a countdown.
- The backend must determine the authoritative attempt timing and submission rules.

### Random and Fixed Questions

- Random quizzes receive questions selected according to backend rules.
- Fixed quizzes use a predetermined question set.

### Practice and Formal Attempts

The system should distinguish between practice attempts and formal attempts.

- Practice attempts support repeated learning and revision.
- Formal attempts may have attempt limits and defined scoring rules.

The exact attempt limits and permissions must be confirmed with the backend.

## 6. Quiz Attempt Interface

The quiz attempt interface is where students answer questions.

### Required Element IDs

| Element | Required ID | Purpose |
|---|---|---|
| Attempt page | `quiz-attempt-page` | Main attempt interface |
| Quiz title | `attempt-quiz-title` | Displays quiz title |
| Question container | `quiz-question-container` | Displays current question |
| Question number | `current-question-number` | Displays current position |
| Total questions | `total-question-count` | Displays total questions |
| Previous button | `btn-previous-question` | Moves to previous question |
| Next button | `btn-next-question` | Moves to next question |
| Submit button | `btn-submit-quiz` | Submits the attempt |
| Question navigator | `quiz-question-navigator` | Displays question navigation |
| Timer | `quiz-timer` | Displays remaining time |
| Submission confirmation | `quiz-submit-confirmation` | Confirms final submission |

### Expected Behaviour

- Display one question or an agreed question layout.
- Allow students to select or enter answers.
- Preserve answers when navigating between questions.
- Allow movement between questions where supported.
- Display question progress.
- Show a timer for timed attempts.
- Provide a submission confirmation step where appropriate.
- Submit the attempt and display the result returned by the backend.

The frontend must handle incomplete answers and submission errors according to the final backend contract.

## 7. Quiz Timer

Timed quizzes should display the remaining time clearly.

Suggested element IDs:

- `quiz-timer`
- `quiz-timer-warning`
- `quiz-time-expired`

Expected behaviour:

- Display the remaining time.
- Update the visible countdown.
- Provide a warning when the remaining time is low, if required.
- Handle time expiration.
- Follow the backend's authoritative timing and submission rules.

The frontend timer is a user-interface aid. It must not be treated as the authoritative source for attempt timing or scoring.

## 8. Quiz Results

After an attempt is submitted and processed, students should be able to view their results.

### Required Element IDs

| Element | Required ID | Purpose |
|---|---|---|
| Result page | `quiz-result-page` | Main result interface |
| Quiz title | `result-quiz-title` | Displays quiz title |
| Score | `quiz-result-score` | Displays obtained score |
| Percentage | `quiz-result-percentage` | Displays percentage |
| Correct count | `correct-answer-count` | Displays correct answers |
| Incorrect count | `incorrect-answer-count` | Displays incorrect answers |
| Unanswered count | `unanswered-question-count` | Displays unanswered questions |
| Result status | `quiz-result-status` | Displays result or pass status |
| Retry button | `btn-retry-quiz` | Starts another attempt where permitted |
| History button | `btn-view-quiz-history` | Opens attempt history |

### Expected Behaviour

Display the result information returned by the backend, including:

- Obtained score.
- Percentage.
- Correct answers.
- Incorrect answers.
- Unanswered questions, if applicable.
- Pass or completion status, if supported.
- Explanations and answer review where permitted.

The frontend must not independently determine the official score or pass status.

## 9. Answer Feedback and Explanations

The system should support two feedback modes.

### Immediate Feedback

The student receives feedback after answering an individual question.

### End-of-Quiz Feedback

The student receives feedback after submitting the complete quiz.

Where permitted, the interface should display:

- Correct or incorrect status.
- Correct answer.
- Student's submitted answer.
- Explanation of the answer.

The backend must determine whether explanations and correct answers are available during an attempt or only after submission.

## 10. Quiz History

Students should be able to view their previous quiz attempts.

### Required Element IDs

| Element | Required ID | Purpose |
|---|---|---|
| History page | `quiz-history-page` | Main history interface |
| History list | `quiz-history-list` | Displays previous attempts |
| Subject filter | `history-subject-filter` | Filters history by subject |
| Topic filter | `history-topic-filter` | Filters history by topic |
| Date filter | `history-date-filter` | Filters history by date |
| Empty state | `quiz-history-empty` | Displays when no attempts exist |
| Loading state | `quiz-history-loading` | Displays loading feedback |

Each attempt card should display available information such as:

- Quiz title.
- Attempt date.
- Score.
- Percentage.
- Completion status.
- Link to attempt results.

Suggested IDs:

- `attempt-card-{attemptId}`
- `attempt-score-{attemptId}`
- `attempt-date-{attemptId}`
- `btn-view-attempt-{attemptId}`

## 11. Retry Incorrect Questions

Students should be able to revisit questions they previously answered incorrectly.

Expected behaviour:

- Identify incorrect questions using backend-provided attempt results.
- Display the relevant question and available explanation.
- Allow retrying incorrect questions through a supported practice flow.
- Display feedback for the retry.

The backend must determine how retry sessions are created and how repeated answers are recorded.

## 12. Bookmarked Questions

Students should be able to bookmark questions for later revision.

Expected behaviour:

- Add a question to bookmarks.
- Remove a question from bookmarks.
- Display bookmark state.
- Access bookmarked questions through the agreed interface.

Suggested element IDs:

- `btn-bookmark-question-{questionId}`
- `bookmarked-question-{questionId}`

The backend must persist bookmark information and enforce the relevant user permissions.

## 13. Custom Quizzes

The system should support custom quiz creation using available options.

Students may be able to select:

- Subject.
- Topic or topics.
- Difficulty.
- Number of questions.
- Question selection mode.
- Timed or untimed mode.

Suggested element IDs:

- `custom-quiz-form`
- `custom-quiz-subject`
- `custom-quiz-topics`
- `custom-quiz-difficulty`
- `custom-quiz-question-count`
- `custom-quiz-timer-mode`
- `btn-create-custom-quiz`

The final set of configuration options and quiz-generation rules must be confirmed with the backend.

## 14. Question Contribution and Moderation

Authorized contributors should be able to submit practice questions for review.

The frontend should support the relevant question submission interface and display submission status where included in the agreed workflow.

Question submission and moderation should follow the resource contribution and review architecture.

This README covers the student quiz and practice experience. The detailed contributor and moderator interfaces should be documented and implemented with their respective feature workflows.

## 15. React Components

| Component | Responsibility |
|---|---|
| `QuizCard` | Displays a quiz in discovery lists |
| `QuizFilters` | Handles quiz filtering |
| `QuizQuestion` | Provides the shared question container |
| `MCQQuestion` | Displays multiple-choice questions |
| `FillBlankQuestion` | Displays fill-in-the-blank questions |
| `CodeOutputQuestion` | Displays code-output questions |
| `QuizTimer` | Displays the attempt countdown |
| `QuizNavigation` | Handles question navigation |
| `QuizSummary` | Displays quiz result information |
| `QuestionExplanation` | Displays answer explanations |
| `AttemptHistoryCard` | Displays a previous attempt |

Additional components may be introduced when required.

## 16. Proposed Frontend Routes

The following routes are part of the current frontend routing plan:

| Route | Purpose |
|---|---|
| `/quizzes` | Quiz discovery |
| `/quizzes/:quizId` | Quiz details |
| `/quizzes/:quizId/attempt` | Quiz attempt interface |
| `/quizzes/results/:attemptId` | Attempt result |
| `/quiz-history` | Previous attempts |

The final route access rules must follow the authentication and authorization requirements.

## 17. Proposed Backend API Endpoints

The following endpoints are proposed for backend coordination. They are not final API contracts.

| Operation | Method | Proposed Endpoint |
|---|---|---|
| Get available quizzes | GET | `/api/quizzes` |
| Get quiz details | GET | `/api/quizzes/:quizId` |
| Start an attempt | POST | `/api/quizzes/:quizId/attempts` |
| Submit an answer | POST | `/api/attempts/:attemptId/answers` |
| Submit an attempt | POST | `/api/attempts/:attemptId/submit` |
| Get attempt result | GET | `/api/attempts/:attemptId/result` |
| Get quiz history | GET | `/api/attempts/history` |
| Get incorrect questions | GET | `/api/attempts/:attemptId/incorrect-questions` |
| Get bookmarked questions | GET | `/api/questions/bookmarks` |
| Bookmark a question | POST | `/api/questions/:questionId/bookmark` |
| Remove bookmark | DELETE | `/api/questions/:questionId/bookmark` |
| Create custom quiz | POST | `/api/quizzes/custom` |

Final request bodies, response structures, validation rules and endpoint paths must be agreed with the backend developer before integration.

## 18. Frontend Service Layer

All quiz-related API requests should be organized in:

`services/quizService.js`

The service should contain functions for:

- Fetching available quizzes.
- Fetching quiz details.
- Starting attempts.
- Submitting answers.
- Submitting completed attempts.
- Fetching attempt results.
- Fetching quiz history.
- Fetching incorrect questions.
- Managing question bookmarks.
- Creating custom quizzes.

Components should call service functions through the agreed feature hooks or event handlers instead of directly embedding API request logic.

## 19. Expected UI States

The frontend should handle:

- Quiz list loading.
- No quizzes available.
- Quiz details loading.
- Attempt creation.
- Question loading.
- Answer submission.
- Answer submission errors.
- Timer warnings.
- Time expiration.
- Attempt submission.
- Submission confirmation.
- Result loading.
- Result unavailable.
- Quiz history loading.
- Empty attempt history.
- Bookmark success and failure.
- Custom quiz validation and creation errors.

## 20. Frontend Testing Checklist

Before marking the module complete, verify:

- [ ] Quiz discovery displays available quizzes.
- [ ] Search and filters work.
- [ ] Quiz cards display correct information.
- [ ] All three question formats render correctly.
- [ ] Students can select MCQ answers.
- [ ] Students can enter fill-in-the-blank answers.
- [ ] Code-output questions display correctly.
- [ ] Answers remain available while navigating questions.
- [ ] Previous and next navigation work.
- [ ] Timed and untimed interfaces work.
- [ ] Timer states display correctly.
- [ ] Attempt submission works with mock responses.
- [ ] Quiz results display backend-provided values.
- [ ] Immediate and end-of-quiz feedback states work.
- [ ] Quiz history displays previous attempts.
- [ ] Incorrect-question retry flow works with mock responses.
- [ ] Bookmark interactions work with mock responses.
- [ ] Custom quiz configuration works with mock responses.
- [ ] Loading, empty and error states work.
- [ ] All agreed element IDs are present and unique.

## 21. Independent Frontend Development

Divya can develop the quiz interface using mock data while the backend question, quiz and attempt APIs are being implemented.

Mock data should cover:

- Different quiz subjects and topics.
- Different difficulty levels.
- MCQ questions.
- Fill-in-the-blank questions.
- Code-output questions.
- Timed and untimed quizzes.
- Random and fixed question sets.
- Practice and formal attempts.
- Correct and incorrect answers.
- Completed and incomplete attempts.
- Quiz results and explanations.
- Previous attempt history.
- Bookmarked questions.

During development:

- Keep quiz API requests inside `quizService.js`.
- Use mock data for independent frontend testing.
- Do not calculate official scores in the frontend.
- Do not decide attempt limits independently.
- Do not treat the browser timer as authoritative.
- Follow backend-provided answer validation and result information.
- Keep quiz components within the quizzes feature.

Joint integration should begin when the backend quiz, question and attempt contracts are ready.

---

**Quiz and Practice System Status:** Core quiz discovery, question formats, attempts, feedback, results, history, bookmarks and custom quiz requirements documented. Scoring rules, attempt limits, timer enforcement, question schemas and final API contracts require backend confirmation.
