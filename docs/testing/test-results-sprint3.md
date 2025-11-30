# Test Results - Sprint 3

**Tested by:** Gita Rahmany (QA Engineer)
**Sprint:** Sprint 3 (November 27–30, 2025)
**Test Period:** November 28–30, 2025
**Report Date:** November 30, 2025

---

## Summary
I tested all admin features delivered in Sprint 3, and everything worked as expected. No bugs were found.

**Total Test Cases:** 9  
**Passed:** 9  
**Failed:** 0  
**Pass Rate:** 100%

---

## What I Tested
Sprint 3 focused on building and refining admin functionality. I tested four major areas:

1. Admin Login and Dashboard
2. Create Events
3. Edit and Delete Events
4. View Attendees

For each feature, I tested both backend API behavior and the frontend UI. I also checked how everything worked across different browsers and devices.

---

## Test Environment

**Backend:**
- Node.js (Express)
- PostgreSQL
- API tested with Postman

**Frontend:**
- React application
- Tested on Chrome, Firefox, and Safari
- Tested on Windows laptop and MacBook
- Tested on iPhone and Android

**Test Data Used:**
- 2 admin test accounts
- 5 student test accounts
- 15 events
- 30 registrations

---

## Detailed Test Results

### Feature 1: Admin Login and Dashboard

**Test Case ID:** TC-023  
**Test Name:** Admin can log in with valid credentials  
**Date Tested:** November 28, 2025

**What I did:**
1. Opened the admin login page.  
2. Entered the admin email: `admin@university.edu`.  
3. Entered the password: `Admin123!`.  
4. Clicked the Login button.  

**Expected Result:**
- Admin credentials should be validated.  
- User should be redirected to the dashboard.  
- Dashboard menu options should be visible.  

**Actual Result:**  
Everything worked as expected. The dashboard loaded and displayed the correct options and summary cards.

**Status:** PASSED

---

**Test Case ID:** TC-024  
**Test Name:** Non-admin users cannot access admin pages  
**Date Tested:** November 28, 2025

**What I did:**
1. Logged in with a student account.  
2. Typed the admin dashboard URL manually.  
3. Tried opening different admin pages.  

**Expected Result:**
- Access should be blocked.  
- A clear error message or redirect should occur.  

**Actual Result:**  
Access was correctly blocked with a 403 Forbidden error.

**Status:** PASSED

---

### Feature 2: Create Events

**Test Case ID:** TC-025  
**Test Name:** Admin can create an event with valid data  
**Date Tested:** November 28, 2025

**What I did:**
1. Logged in as admin.  
2. Opened the Create Event page.  
3. Filled out all required fields, including title, description, category, date, time, location, capacity, and price.  
4. Clicked "Create Event".  

**Expected Result:**
- Event should be saved.  
- A success message should appear.  
- Admin should be redirected to Manage Events.  

**Actual Result:**  
The event was created successfully and appeared in the list with accurate data.

**Status:** PASSED

---

**Test Case ID:** TC-026  
**Test Name:** Cannot create event with missing required fields  
**Date Tested:** November 28, 2025

**What I did:**  
Tested the form by leaving out required fields (title, date, location, capacity).

**Expected Result:**  
The form should show validation errors and prevent submission.

**Actual Result:**  
Validation worked correctly for every scenario.

**Status:** PASSED

---

**Test Case ID:** TC-027  
**Test Name:** Cannot create event with invalid data  
**Date Tested:** November 28, 2025

**What I did:**  
Tested invalid inputs such as past dates, negative or zero capacity, and negative price.

**Expected Result:**  
Invalid data should be rejected with clear error messages.

**Actual Result:**  
All invalid inputs were handled correctly.

**Status:** PASSED

---

### Feature 3: Edit and Delete Events

**Test Case ID:** TC-028  
**Test Name:** Admin can edit an existing event  
**Date Tested:** November 29, 2025

**What I did:**
1. Opened Manage Events.  
2. Selected an event.  
3. Opened the edit form.  
4. Updated the title, capacity, and price.  
5. Saved changes.  

**Expected Result:**  
The updated event should save and appear correctly.

**Actual Result:**  
The edits saved successfully and displayed properly.

**Status:** PASSED

---

**Test Case ID:** TC-029  
**Test Name:** Cannot edit event with invalid data  
**Date Tested:** November 29, 2025

**What I did:**  
Tried editing an event using past dates, negative capacity, and blank titles.

**Expected Result:**  
Invalid updates should not save.

**Actual Result:**  
Validation worked as expected and prevented invalid changes.

**Status:** PASSED

---

**Test Case ID:** TC-030  
**Test Name:** Admin can delete an event  
**Date Tested:** November 29, 2025

**What I did:**
1. Created a test event with registrations.  
2. Opened Manage Events.  
3. Clicked Delete.  
4. Confirmed deletion.  

**Expected Result:**  
Event and its related registrations should be removed.

**Actual Result:**  
Deletion worked correctly, and all data was removed.

**Status:** PASSED

---

### Feature 4: View Attendees

**Test Case ID:** TC-031  
**Test Name:** Admin can view attendees  
**Date Tested:** November 30, 2025

**What I did:**
1. Opened Manage Events.  
2. Selected an event with registrations.  
3. Clicked View Attendees.  

**Expected Result:**  
A table should display all attendee information.

**Actual Result:**  
The attendee list displayed correctly and matched database entries.

**Status:** PASSED

---

**Test Case ID:** TC-032  
**Test Name:** Empty state displays correctly and CSV export works  
**Date Tested:** November 30, 2025

**Part 1 – Empty State**

**What I did:**  
Opened attendees for an event with zero registrations.

**Expected Result:**  
A clear "no registrations" message should appear.

**Actual Result:**  
The empty state message displayed correctly.

**Status:** PASSED

**Part 2 – CSV Export**

**What I did:**  
Tested CSV export on an event with five registrations.

**Expected Result:**  
CSV file should download with correct headers and data.

**Actual Result:**  
The file downloaded correctly and displayed accurate, well-formatted data.

**Status:** PASSED

---

## Browser and Device Testing
All features worked correctly across all tested platforms.

**Desktop:** Chrome, Firefox, Safari  
**Mobile:** iPhone (Safari), Samsung Galaxy (Chrome)

The admin panel displayed and performed well on all devices.

---

## Performance Testing
All main operations (login, event creation, editing, deletion, viewing attendees, and CSV export) loaded within acceptable time ranges.

---

## Security Testing
Security checks all passed, including:
- Blocking non-admin access  
- Handling expired tokens  
- Preventing SQL injection  
- Preventing XSS scripts  

---

## Regression Testing
All features from Sprints 1 and 2 continue to function correctly.

---

## Bugs Found
None.

---

## Things I Liked
- Strong validation  
- Clear and safe delete confirmation  
- Clean CSV output  
- Helpful empty state messaging  
- Responsive design  
- Clean, easy-to-follow UI  

---

## Suggestions for Future Improvements
These are enhancement ideas, not bugs:
- Add search on Manage Events  
- Add a print option for attendee lists  
- Add sorting options  
- Provide better separation between upcoming and future

---

Gita Rahmany
QA Engineer
November 30, 2025
