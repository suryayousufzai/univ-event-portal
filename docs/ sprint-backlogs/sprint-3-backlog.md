# Sprint 3 Backlog

**Project:** University Event Registration Portal  
**Sprint:** Sprint 3  
**Duration:** November 27-30, 2025 (4 days)  
**Sprint Goal:** Enable administrators to create, manage, and monitor events

---

## Sprint Overview

In Sprint 3, we're building the admin side of the portal. University staff need to be able to create events, edit them, delete them, and see who registered. Right now we have sample events in the database, but admins need a way to manage events themselves through the website.

---

## Sprint Backlog Items

| ID | User Story | Story Points | Status | Assigned To |
|----|------------|--------------|--------|-------------|
| US-011 | Admin Login & Dashboard | 3 | Not Started | Fariba + Muneera + Gita |
| US-012 | Create Events | 8 | Not Started | Fariba + Muneera + Gita |
| US-013 | Edit/Delete Events | 5 | Not Started | Fariba + Muneera + Gita |
| US-014 | View Attendees | 5 | Not Started | Fariba + Muneera + Gita |

**Total Story Points:** 21

---

## Task Breakdown by Feature

---

### US-011: Admin Login & Dashboard (3 points)

**What it does:**
Admins can log in with special admin credentials and access an admin dashboard with management options.

**Acceptance Criteria:**
- Admin can login with admin email and password
- System verifies admin role from database
- Admin dashboard shows after login
- Dashboard has menu options: Create Event, Manage Events, View Attendees
- Regular users cannot access admin pages
- Admin can logout

**Backend Tasks (Fariba):**
- [ ] Create admin login API endpoint
  - Verify admin role in database
  - Return JWT token with admin flag
  - Handle invalid credentials
- [ ] Create admin dashboard data API
  - Return total events count
  - Return total registrations count
  - Return recent activity
- [ ] Add admin role check middleware for protected routes

**Frontend Tasks (Muneera):**
- [ ] Build Admin Login page
  - Email and password fields
  - Login button
  - Error messages
  - Redirect to dashboard on success
- [ ] Build Admin Dashboard page
  - Navigation sidebar
  - Menu items: Create Event, Manage Events, View Attendees
  - Display summary stats (total events, registrations)
  - Logout button

**QA Tasks (Gita):**
- [ ] Write test cases TC-023, TC-024
- [ ] Test admin login with valid credentials
- [ ] Test admin login with wrong credentials
- [ ] Test that regular users cannot access admin pages
- [ ] Test dashboard displays correctly

---

### US-012: Create Events (8 points)

**What it does:**
Admins can create new events by filling out a form with all event details.

**Acceptance Criteria:**
- Admin can access Create Event page from dashboard
- Form has fields: title, description, category, date, time, location, capacity, price
- All required fields validated
- Event saved to database
- Event appears in events list immediately
- Success message shown
- Admin redirected to Manage Events page

**Backend Tasks (Fariba):**
- [ ] Create Event API endpoint: POST /api/admin/events
  - Accept all event fields
  - Validate required fields (title, date, location, capacity)
  - Validate date is in the future
  - Validate capacity is positive number
  - Save event to database
  - Return created event with ID
- [ ] Add error handling for validation failures

**Frontend Tasks (Muneera):**
- [ ] Build Create Event form page
  - Input fields: title, description, category dropdown, date picker, time picker, location, capacity, price
  - Mark required fields with asterisk
  - Add form validation (required fields, valid date, positive numbers)
  - "Create Event" button
  - "Cancel" button (go back to dashboard)
- [ ] Connect form to Create Event API
  - Show loading state during submission
  - Show success message on completion
  - Redirect to Manage Events page
  - Show error messages if validation fails

**QA Tasks (Gita):**
- [ ] Write test cases TC-025, TC-026, TC-027
- [ ] Test creating event with all valid data
- [ ] Test creating event with missing required fields
- [ ] Test creating event with past date (should fail)
- [ ] Test creating event with negative capacity (should fail)
- [ ] Verify event appears in events list after creation

---

### US-013: Edit/Delete Events (5 points)

**What it does:**
Admins can edit existing events or delete cancelled events.

**Acceptance Criteria:**
- Admin can see list of all events in Manage Events page
- Each event has Edit and Delete buttons
- Clicking Edit opens edit form pre-filled with current data
- Admin can update any field
- Changes saved to database
- Clicking Delete shows confirmation popup
- Confirmed deletion removes event from database
- Success messages shown

**Backend Tasks (Fariba):**
- [ ] Edit Event API: PUT /api/admin/events/:id
  - Accept all event fields
  - Validate fields same as create
  - Update event in database
  - Return updated event
- [ ] Delete Event API: DELETE /api/admin/events/:id
  - Remove event from database
  - Also remove related registrations (cascade delete)
  - Return success confirmation

**Frontend Tasks (Muneera):**
- [ ] Build Manage Events page
  - Show table/list of all events
  - Display: title, date, location, capacity, available seats
  - Edit button for each event
  - Delete button for each event
- [ ] Build Edit Event form
  - Pre-fill form with current event data
  - Same fields as Create Event form
  - "Save Changes" button
  - "Cancel" button
- [ ] Add Delete confirmation modal
  - Warning message: "Are you sure? This will delete the event and all registrations!"
  - "Yes, Delete" button (red)
  - "Cancel" button
- [ ] Connect Edit and Delete to APIs
  - Show loading states
  - Show success/error messages
  - Refresh event list after changes

**QA Tasks (Gita):**
- [ ] Write test cases TC-028, TC-029, TC-030
- [ ] Test editing event with valid data
- [ ] Test editing event with invalid data (should show errors)
- [ ] Test deleting event
- [ ] Verify event is removed from list after deletion
- [ ] Verify registrations are also deleted

---

### US-014: View Attendees (5 points)

**What it does:**
Admins can see who registered for each event and export the list.

**Acceptance Criteria:**
- Admin can click "View Attendees" button on any event
- Shows list of all registered users for that event
- Displays: user name, email, registration date, payment status
- Shows total number of registrations
- Admin can export list as CSV file
- Empty state if no one registered yet

**Backend Tasks (Fariba):**
- [ ] Get Attendees API: GET /api/admin/events/:id/attendees
  - Return all registrations for the event
  - Include user name, email, registration date, payment status
  - Sort by registration date (newest first)
- [ ] CSV Export functionality
  - Format attendee data as CSV
  - Include headers: Name, Email, Registration Date, Payment Status
  - Return downloadable CSV file

**Frontend Tasks (Muneera):**
- [ ] Build View Attendees page
  - Show event name at top
  - Display attendees in table format
  - Columns: Name, Email, Registration Date, Payment Status
  - Show total count: "X people registered"
  - "Export as CSV" button
  - "Back to Manage Events" button
- [ ] Add "View Attendees" button to each event in Manage Events page
- [ ] Show empty state if no registrations
  - Message: "No one has registered for this event yet"

**QA Tasks (Gita):**
- [ ] Write test cases TC-031, TC-032
- [ ] Test viewing attendees for event with registrations
- [ ] Test viewing attendees for event with no registrations (empty state)
- [ ] Test CSV export functionality
- [ ] Verify CSV file contains correct data with proper formatting

---

## Definition of Done (Sprint 3)

A feature is "Done" when:
- [ ] Backend API is complete and tested in Postman
- [ ] Frontend UI is complete and responsive
- [ ] Backend and frontend are integrated
- [ ] All test cases passed
- [ ] No bugs remaining
- [ ] Code pushed to GitHub
- [ ] Documentation updated
- [ ] Product Owner has reviewed and accepted

---

## Sprint 3 Schedule

**Day 1 (Nov 27):**
- Sprint Planning meeting
- Start building admin login
- Write test cases

**Day 2 (Nov 28):**
- Complete admin login
- Build create event feature
- Start testing admin login

**Day 3 (Nov 29):**
- Complete create event
- Build edit/delete features
- Test create event

**Day 4 (Nov 30):**
- Complete view attendees
- Final testing all features
- Write documentation
- Sprint Review meeting
- Sprint Retrospective meeting

---

## Technical Notes

**Admin Authentication:**
- Admin users have role = 'admin' in database
- JWT token includes admin flag
- Frontend checks admin flag to show/hide admin pages
- Backend middleware verifies admin role on protected routes

**Database Changes:**
- No new tables needed
- Use existing events table
- Use existing users table (with role field)
- Use existing registrations table

**Security:**
- Only users with admin role can access admin APIs
- Regular users get 403 Forbidden if they try to access admin endpoints
- All admin actions logged for audit trail

---

## Team Capacity

**Sprint Duration:** 4 days

**Team Velocity:**
- Sprint 1: 16 points
- Sprint 2: 19 points
- Sprint 3 Estimate: 21 points (slightly higher but achievable)

**Available Time:**
- Each team member working full days
- No holidays or absences expected
- Team is experienced now (3rd sprint)

---

## Risks & Mitigations

**Risk:** 21 points is slightly more than Sprint 2's 19 points
**Mitigation:** Team is more experienced now, admin features are less complex than payment integration

**Risk:** Admin features might need more polish for usability
**Mitigation:** Muneera will focus on clean, intuitive UI design

**Risk:** Testing might find issues late
**Mitigation:** Gita will test features as they're completed, not wait until end

---

## Success Criteria

Sprint 3 is successful if:
- ✅ Admins can create new events
- ✅ Admins can edit existing events
- ✅ Admins can delete events
- ✅ Admins can see who registered for events
- ✅ All features tested and working
- ✅ Zero critical bugs
- ✅ Product Owner accepts all features

---

**Prepared by:** Surya Yousufzai (Scrum Master)  
**Approved by:** Marwa Paiman (Product Owner)  
**Date:** November 27, 2025  
