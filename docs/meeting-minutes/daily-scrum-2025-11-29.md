# Daily Scrum Meeting - November 29, 2025

**Sprint:** Sprint 3 (Day 3 of 4)  
**Date:** Friday, November 29, 2025  
**Time:** 10:00 AM  
**Duration:** 6 minutes  
**Location:** Google Meet

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

Day 3 of Sprint 3. Yesterday we completed the Create Event feature. Today we're building Edit and Delete functionality.

---

## Team Updates

### Fariba (Backend Lead)

**What she did yesterday:**
- Completed Create Event API
- Accepts all event fields and validates them
- Saves new events to database
- Tested in Postman with valid and invalid data
- Everything working correctly

**What she's doing today:**
- Building Edit Event API (PUT /api/admin/events/:id)
- Building Delete Event API (DELETE /api/admin/events/:id)
- Edit API will validate fields same as Create
- Delete API will remove event and cascade delete related registrations
- Goal: Complete both APIs by end of day

**Blockers:** None

---

### Muneera (Frontend Lead)

**What she did yesterday:**
- Completed Create Event form with all fields
- Added validation for required fields and data types
- Connected form to Fariba's API
- Tested creating events - working perfectly
- Form looks professional and is easy to use

**What she's doing today:**
- Building Manage Events page with list of all events
- Show events in table format with Edit and Delete buttons
- Building Edit Event form (will pre-fill with current data)
- Building Delete confirmation modal
- Connect Edit and Delete to backend APIs
- Goal: Complete all three components today

**Blockers:** None

---

### Gita (QA Engineer)

**What she did yesterday:**
- Tested Admin Login API - TC-023 PASSED, TC-024 PASSED
- Tested Admin Login UI - working correctly
- Tested Create Event API - TC-025 PASSED
- Tested Create Event UI - TC-026 PASSED, TC-027 PASSED
- All tests passed, no bugs found

**What she's doing today:**
- Write test cases for Edit and Delete (TC-028, TC-029, TC-030)
- Test Edit Event feature when ready
- Test Delete Event feature when ready
- Start preparing test results document for Sprint 3
- Verify events list updates correctly after edit/delete

**Blockers:** None

---

### Marwa (Product Owner)

**What she did yesterday:**
- Tested Create Event feature myself
- Created several test events successfully
- Form is intuitive and validation works well

**What she's doing today:**
- Available for questions about Edit and Delete features
- Will test Edit and Delete when ready
- Making sure delete confirmation is clear (important safety feature)

**Blockers:** None

---

## Sprint Progress

**Day 3 of 4**

**Completed:**
- Admin Login (backend and frontend) - 100%
- Admin Dashboard (frontend) - 100%
- Create Event (backend and frontend) - 100%
- All testing for above features - PASSED

**In Progress:**
- Edit Event API and UI (Fariba and Muneera working today)
- Delete Event API and UI (Fariba and Muneera working today)

**Not Started:**
- View Attendees (planned for tomorrow, Day 4)

**Status:** On schedule. Almost done with Sprint 3!

---

## Blockers

None reported.

---

## Recording

(https://drive.google.com/file/d/1KZ66nooW22zP6Xab2odz0a1bdju9_OGp/view?usp=sharing)

---

## Action Items

- Fariba: Complete Edit and Delete APIs by end of day
- Muneera: Complete Manage Events page, Edit form, and Delete modal by end of day
- Gita: Test Edit and Delete features today
- All: Prepare for final day tomorrow

---

## Reminder

Tomorrow (Nov 30) schedule:
- Morning: Daily Scrum
- During day: Complete View Attendees, final testing, documentation
- Afternoon: Sprint Review meeting
- Evening: Sprint Retrospective meeting

---

## Next Meeting

**Date:** November 30, 2025  
**Time:** 10:00 AM  
**Platform:** Google Meet

---

**Notes by:** Surya Yousufzai (Scrum Master)  
**Date:** November 29, 2025
