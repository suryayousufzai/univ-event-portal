# Daily Scrum Meeting - November 28, 2025

**Sprint:** Sprint 3 (Day 2 of 4)  
**Date:** November 28, 2025  
**Time:** 10:00 AM  
**Duration:**  minutes  
**Location:** Zoom

---

## Attendees

- Surya Yousufzai - Scrum Master
- Marwa Paiman - Product Owner
- Fariba Mohammadi - Backend Lead
- Muneera Aman - Frontend Lead
- Gita Rahmany - QA Engineer

All present.

---

## Meeting Summary

Day 2 of Sprint 3. Yesterday we started building admin features. Today we're working on the Create Event functionality.

---

## Team Updates

### Fariba (Backend Lead)

**What she did yesterday:**
- Completed Admin Login API
- API verifies admin role in database
- Returns JWT token with admin flag
- Tested in Postman - all working correctly

**What she's doing today:**
- Building Create Event API
- Endpoint: POST /api/admin/events
- Will accept all event fields (title, description, category, date, time, location, capacity, price)
- Add validation for required fields
- Save event to database
- Goal: Complete by end of day

**Blockers:** None

---

### Muneera (Frontend Lead)

**What she did yesterday:**
- Built Admin Login page with email and password fields
- Built Admin Dashboard page
- Dashboard has navigation menu with three options: Create Event, Manage Events, View Attendees
- Both pages are responsive and look professional

**What she's doing today:**
- Building Create Event form page
- Add input fields for all event data
- Add form validation (required fields, date validation, positive numbers)
- Connect form to Fariba's Create Event API when ready
- Goal: Complete form by end of day

**Blockers:** None

---

### Gita (QA Engineer)

**What she did yesterday:**
- Wrote test cases for admin login (TC-023, TC-024)
- Prepared admin test data in database
- Set up Postman collection for admin APIs

**What she's doing today:**
- Test Admin Login API with valid and invalid credentials
- Test Admin Login UI
- Write test cases for Create Event (TC-025, TC-026, TC-027)
- Start testing Create Event feature if API is ready
- Document test results

**Blockers:** None

---

### Marwa (Product Owner)

**What she did yesterday:**
- Reviewed admin login design
- Confirmed it matches requirements

**What she's doing today:**
- Available for questions about Create Event form fields
- Will review Create Event feature when ready
- Ready to clarify any requirements

**Blockers:** None

---

## Sprint Progress

**Day 2 of 4**

**Completed:**
- Admin Login API (backend)
- Admin Login page (frontend)
- Admin Dashboard (frontend)
- Test cases for admin login written

**In Progress:**
- Create Event API (Fariba working today)
- Create Event form (Muneera working today)
- Testing admin login (Gita working today)

**Not Started:**
- Edit/Delete Events (planned for Day 3)
- View Attendees (planned for Day 4)

**Status:** On track

---

## Blockers

None reported.


---

## Action Items

- Fariba: Complete Create Event API by end of day
- Muneera: Complete Create Event form by end of day
- Gita: Test admin login today, prepare for testing Create Event tomorrow
- Marwa: Be available for questions

---
## Recording
(https://drive.google.com/file/d/1lbc-WpJtndtb1kahP7jJauAsrEn8SEvA/view?usp=drive_link)

---
## Next Meeting

**Date:** November 29, 2025  
**Time:** 10:00 AM  
**Platform:** Google Meet

---

**Notes by:** Surya Yousufzai (Scrum Master)  
**Date:** November 28, 2025
