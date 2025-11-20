# Daily Scrum Meeting – November 19, 2025  
Sprint 1 – Day 4  
Time: 10:00 AM  

## Attendees
- Surya – Scrum Master  
- Marwa – Product Owner  
- Fariba – Backend Lead  
- Muneera – Frontend Lead  
- Gita – QA & DevOps  

---

## Meeting Summary
This meeting covered updates from each team member based on what they completed yesterday, what they are doing today, and whether they have any blockers. The team is progressing well, and the workflow for Sprint 1 is on track.

---

## Backend Update – Fariba

### What was done yesterday
- Completed the Login API (`POST /api/login`).
- Added email and password validation.
- Implemented JWT token generation (24-hour validity).
- Returned user details on success (ID, name, email, role).
- Added clear error messages for incorrect credentials.
- Tested the API in Postman and confirmed expected responses.
- Shared the Postman collection with Gita.
- Started working on the Events List API.

### What will be done today
- Finish the Events List API (`GET /api/events`).
  - Include category filtering (e.g., workshop, conference).
  - Add keyword-based search.
  - Add pagination if time allows.
- Write documentation for the new API.
- Assist in backend–frontend integration once the frontend is ready.

### Blockers
None.

---

## Frontend Update – Muneera

### What was done yesterday
- Completed the Registration Page UI.
- Added all required fields: full name, email, password, confirm password, student ID.
- Implemented form validation and password strength indicator.
- Added a success message and automatic redirect to the login page.
- Styled the page using Tailwind and made it responsive.
- Pushed the work to `feature/registration-UI`.
- Started basic structure for the Events List Page.

### What will be done today
- Complete the Events List Page:
  - Event cards with image, title, date, location, and price.
  - “Free” badge for events with no cost.
- Add search bar and category filter.
- Improve responsiveness.
- Prepare for backend integration for registration and login pages.

### Blockers
None.

---

## QA & DevOps Update – Gita

### What was done yesterday
Completed the following test cases:
- TC-001: Valid registration — Passed  
- TC-002: Login with correct credentials — Passed  
- TC-003: Wrong password — Passed  
- TC-004: Duplicate email — Failed  

### Bug Report
**BUG-001**  
- Issue: Duplicate email returns a 500 server error.  
- Expected: A user-friendly message such as “Email already registered.”  
- Reported to Fariba.  
- Severity: Major but simple to fix.

### What will be done today
- Retest TC-004 after the bug fix.
- Continue executing test cases:
  - Browse events
  - Password validation
  - Email format checks
  - Additional login scenarios

### Blockers
Waiting for Fariba to finish the fix for BUG-001.

---

## Product Owner Update – Marwa
- Tested both the registration and login pages personally.
- Confirmed that both pages match the Figma design.
- Reviewed BUG-001 and agreed that duplicate email should not throw a server error.
- Clarified display for free events: it should show “Free” instead of “$0.00”.
- No updates needed for the backlog today.

### Blockers
None.

---

## Team Discussion
- Gita explained the duplicate email bug and how it affects the registration flow.
- Fariba confirmed that the fix will take about 30 minutes:
  - Check for existing email before inserting the user.
  - Return a 400 error with a clear message.
- Gita will retest immediately after the fix.
- Frontend and backend integration can start tomorrow morning.
- Overall progress is ahead of schedule.

---

## Action Items

### Fariba
- Fix BUG-001 in the morning.  
- Notify the team once fixed.  
- Complete Events List API.  
- Write API documentation.  

### Gita
- Retest TC-004 after the bug fix.  
- Continue executing remaining test cases.  

### Muneera
- Complete Events List UI.  
- Prepare for integration tomorrow.  

---

## Blockers
- Only temporary blocker: Gita waiting for bug fix.  
- No other blockers reported.

---

## Next Meeting
Daily Scrum  
Date: November 20, 2025  
Time: 10:00 AM  
Platform: Zoom  

---

## Recording
(https://drive.google.com/file/d/1fSvvbHTv0_RzvSE51HUUdNJf18VcaC4n/view?usp=drive_link
https://drive.google.com/file/d/1TgIvY7RRNDRTFTYYRHto0JZIcUZOsEtF/view?usp=drive_link)

---

**Prepared by:** Surya (Scrum Master)  
**Date:** November 19, 2025
