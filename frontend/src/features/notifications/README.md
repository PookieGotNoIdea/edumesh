# Notifications Module — Frontend

## 1. Module Overview

The Notifications module allows EduMesh students to stay informed about important updates and activities on the platform.

Notifications may inform students about events such as:

- Resource submission status updates.
- Resource approval or rejection.
- Replies or updates related to submitted content.
- Quiz and learning activity updates.
- Progress-related reminders.
- Other important platform announcements.

The frontend should provide a notification system that is easy to access without interrupting the student's learning experience.

The agreed notification approach is **toast-first notifications with a persistent notification history**.

The notification system should include:

- Toast notifications for new events.
- A notification bell in the application header.
- An unread notification count.
- A notification history panel or page.
- Read and unread notification states.
- Controls to mark notifications as read.
- A control to mark all notifications as read.

The backend is responsible for generating, storing and delivering notification records.

The frontend is responsible for retrieving, displaying and managing the user's notification interface.

## 2. Planned Folder Structure

```text
notifications/
│
├── README.md
│
├── components/
│   ├── NotificationBell.jsx
│   ├── NotificationBadge.jsx
│   ├── NotificationToast.jsx
│   ├── NotificationList.jsx
│   ├── NotificationCard.jsx
│   └── NotificationEmptyState.jsx
│
├── pages/
│   └── NotificationsPage.jsx
│
├── services/
│   └── notificationService.js
│
└── hooks/
    └── useNotifications.js
```

This is the proposed folder structure. Additional files may be introduced when implementation requires them.

## 3. Notification Bell

The notification bell should be available in the shared application header.

It provides quick access to a student's notifications.

### Required Element IDs

| Element | Required ID | Purpose |
|---|---|---|
| Notification bell | `notification-bell` | Opens the notification interface |
| Notification badge | `notification-badge` | Displays unread count |
| Notification panel | `notification-panel` | Displays recent notifications |
| View all button | `btn-view-all-notifications` | Opens notification history |

### Expected Behaviour

- Display a notification bell in the application header.
- Display the unread notification count.
- Open a notification panel when the bell is selected.
- Display recent notifications in the panel.
- Provide access to the complete notification history.
- Update the unread count after notification state changes.

The notification bell should be reusable across the relevant authenticated application layouts.

## 4. Unread Notification Count

Students should be able to identify how many notifications they have not yet read.

### Required Element IDs

| Element | Required ID | Purpose |
|---|---|---|
| Unread count | `notification-unread-count` | Displays unread count |
| Notification badge | `notification-badge` | Visually indicates unread notifications |

### Expected Behaviour

- Retrieve the unread notification count from the backend.
- Display the count near the notification bell.
- Update the count when notifications are marked as read.
- Handle zero unread notifications.
- Handle loading and API errors.

The backend should provide the authoritative unread count.

The frontend should not independently calculate the official count from incomplete notification data.

## 5. Toast Notifications

Toast notifications provide immediate feedback when a new notification is received.

They should be visible without forcing students to leave their current page.

### Required Element IDs

| Element | Required ID | Purpose |
|---|---|---|
| Toast container | `notification-toast-container` | Contains active notification toasts |
| Toast item | `notification-toast-{notificationId}` | Displays an individual notification |
| Toast title | `notification-toast-title-{notificationId}` | Displays notification title |
| Toast message | `notification-toast-message-{notificationId}` | Displays notification message |
| Toast close button | `btn-close-notification-toast-{notificationId}` | Dismisses a toast |

### Expected Behaviour

- Display a toast when a new notification is received.
- Show a short title and message.
- Allow the toast to be dismissed.
- Avoid displaying the same incoming notification repeatedly.
- Provide navigation to the relevant content when a valid destination is available.
- Ensure toast notifications do not unnecessarily interrupt the student's work.

Dismissing a toast should not automatically mark the persistent notification record as read unless that behaviour is explicitly agreed with the backend.

## 6. Notification History

Students should be able to access their previous notifications.

The notification history should display notifications retrieved from the backend.

### Required Element IDs

| Element | Required ID | Purpose |
|---|---|---|
| Notifications page | `notifications-page` | Main notification history interface |
| Notification list | `notification-list` | Displays notification records |
| Notification filters | `notification-filters` | Contains notification filters |
| All filter | `filter-all-notifications` | Displays all notifications |
| Unread filter | `filter-unread-notifications` | Displays unread notifications |
| Read filter | `filter-read-notifications` | Displays read notifications |
| Mark all read | `btn-mark-all-notifications-read` | Marks all notifications as read |
| Loading state | `notifications-loading` | Displays loading feedback |
| Empty state | `notifications-empty` | Displays when no notifications exist |
| Error state | `notifications-error` | Displays loading errors |

### Expected Behaviour

- Retrieve notification history from the backend.
- Display notification title and message.
- Display the notification date or time.
- Indicate whether a notification is read or unread.
- Allow students to filter notifications where supported.
- Allow navigation to related content where a destination is available.
- Provide loading, empty and error states.

## 7. Individual Notification Card

Each notification should be displayed using a reusable notification card.

### Required Element IDs

| Element | ID Pattern | Purpose |
|---|---|---|
| Notification card | `notification-card-{notificationId}` | Displays one notification |
| Notification title | `notification-title-{notificationId}` | Displays title |
| Notification message | `notification-message-{notificationId}` | Displays message |
| Notification date | `notification-date-{notificationId}` | Displays date or time |
| Read indicator | `notification-read-status-{notificationId}` | Displays read state |
| Mark as read | `btn-mark-notification-read-{notificationId}` | Marks notification as read |

### Expected Behaviour

- Display notification information clearly.
- Visually distinguish read and unread notifications.
- Allow an unread notification to be marked as read.
- Navigate to related content where supported.
- Update the interface after a successful backend response.

## 8. Read and Unread Management

Students should be able to manage their notification read states.

### Individual Read Action

When a student marks a notification as read:

- Send the request to the backend.
- Update the notification's displayed state after success.
- Update the unread count.
- Display an error if the request fails.

### Mark All as Read

Students should also be able to mark all available unread notifications as read.

Expected behaviour:

- Provide a clear action button.
- Send the request to the backend.
- Update the displayed notification states after success.
- Refresh or update the unread count.
- Handle failures appropriately.

The backend must determine how read-state updates are stored and validated.

## 9. Polling and Notification Updates

The agreed initial approach is **polling**.

Polling means that the frontend periodically requests the backend to check whether new notifications are available.

### Expected Behaviour

- Retrieve recent notifications at an agreed interval.
- Update the unread notification count.
- Display new notifications through toast messages.
- Avoid showing duplicate toast messages.
- Stop unnecessary polling when the relevant application session is inactive or unavailable.
- Handle network failures without breaking the application.

The polling interval and response format must be finalized during integration.

WebSockets may be considered as a future enhancement if real-time delivery becomes necessary.

The initial implementation should not require WebSockets.

## 10. React Components

| Component | Responsibility |
|---|---|
| `NotificationBell` | Displays the notification bell and opens the notification panel |
| `NotificationBadge` | Displays the unread notification count |
| `NotificationToast` | Displays an incoming notification |
| `NotificationList` | Displays notification history |
| `NotificationCard` | Displays an individual notification |
| `NotificationEmptyState` | Displays when no notifications are available |

Additional components may be introduced when required.

## 11. Proposed Frontend Route

The current routing plan includes:

| Route | Purpose |
|---|---|
| `/notifications` | Displays notification history |

The notification bell and recent notification panel should also be accessible from the shared authenticated application header.

## 12. Proposed Backend API Endpoints

The following endpoints are proposed for backend coordination. They are not final API contracts.

| Operation | Method | Proposed Endpoint |
|---|---|---|
| Get notifications | GET | `/api/notifications` |
| Get unread count | GET | `/api/notifications/unread-count` |
| Mark notification as read | PATCH | `/api/notifications/:notificationId/read` |
| Mark all as read | PATCH | `/api/notifications/read-all` |

Final endpoint paths, query parameters, response structures and permissions must be confirmed during backend development.

### A. Get Notifications

**Endpoint:** `GET /api/notifications`

Purpose: Retrieve the authenticated student's notification history.

Possible query parameters:

- `page`
- `limit`
- `status`

The final pagination and filtering contract must be agreed with the backend.

### B. Get Unread Count

**Endpoint:** `GET /api/notifications/unread-count`

Purpose: Retrieve the number of unread notifications for the authenticated student.

### C. Mark Notification as Read

**Endpoint:** `PATCH /api/notifications/:notificationId/read`

Purpose: Mark a specific notification as read.

### D. Mark All Notifications as Read

**Endpoint:** `PATCH /api/notifications/read-all`

Purpose: Mark all applicable unread notifications as read.

## 13. Frontend Service Layer

All notification-related API requests should be organized in:

`services/notificationService.js`

The service should contain functions for:

- Fetching notification history.
- Fetching unread notification count.
- Marking an individual notification as read.
- Marking all notifications as read.

Components should use the service layer through the agreed feature hooks or event handlers rather than embedding API request logic directly.

## 14. Notification State Management

The `useNotifications.js` hook should manage notification-related frontend state where appropriate.

Possible state includes:

- Notification list.
- Unread count.
- Loading status.
- Error status.
- Selected notification filter.
- Notification panel visibility.

The notification state should remain consistent when:

- A new notification is received.
- A notification is marked as read.
- All notifications are marked as read.
- The notification history is refreshed.

The shared application header should be able to access the notification interface without duplicating notification logic across pages.

## 15. Notifications and Activity Logs

EduMesh distinguishes between notifications and activity logs.

**Notifications** inform users about events that require their attention or may be relevant to them.

**Activity logs** record actions performed within the platform for tracking and administrative purposes.

These are separate concepts and should not be treated as the same database record or frontend feature.

The notification interface should display notification records, not a complete history of every platform activity.

## 16. Expected UI States

The frontend should handle:

- Notification loading.
- New notification received.
- No notifications available.
- Unread notifications available.
- No unread notifications.
- Notification panel open and closed.
- Toast displayed.
- Toast dismissed.
- Individual notification marked as read.
- All notifications marked as read.
- Notification update failure.
- Polling request failure.
- Notification history loading failure.

## 17. Frontend Testing Checklist

Before marking the module complete, verify:

- [ ] Notification bell displays in the authenticated application header.
- [ ] Notification panel opens and closes.
- [ ] Unread count displays correctly.
- [ ] Notification history displays correctly.
- [ ] Read and unread notifications look different.
- [ ] Notifications can be filtered where supported.
- [ ] Individual notifications can be marked as read.
- [ ] All notifications can be marked as read.
- [ ] Unread count updates after successful actions.
- [ ] Toast notifications display correctly.
- [ ] Toasts can be dismissed.
- [ ] Duplicate toast notifications are avoided.
- [ ] Polling retrieves updated notification information.
- [ ] Related notification links navigate correctly where available.
- [ ] Loading, empty and error states work.
- [ ] All agreed element IDs are present and unique.

## 18. Independent Frontend Development

Divya can develop the Notifications interface using mock data while the backend notification APIs are being implemented.

Mock data should cover:

- No notifications.
- Multiple unread notifications.
- Multiple read notifications.
- Different notification categories.
- Recent and older notifications.
- Notifications with and without navigation destinations.
- New notifications received during polling.
- Successful read-state updates.
- Failed notification requests.

During development:

- Keep notification API requests inside `notificationService.js`.
- Use mock data for independent frontend testing.
- Keep notification state management inside the feature hook or agreed shared provider.
- Do not generate persistent notification records in the frontend.
- Do not treat toast dismissal as a read-state update automatically.
- Keep activity logs separate from notification history.
- Implement polling initially.
- Keep notification components reusable in the shared application header.

Joint integration should begin after the backend notification endpoints and polling response contract are ready.

---

**Notifications Module Status:** Core notification bell, unread count, toast messages, notification history, read-state management and polling requirements documented. Final polling interval, notification categories, response structure and API contracts require backend confirmation.
