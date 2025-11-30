# Sprint Review and Retrospective Meeting – Sprint 3
**Project:** University Event Registration Portal  
**Meeting Type:** Sprint 3 Review and Retrospective  
**Date:** November 30, 2025  
**Duration:** 29 minutes  
**Platform:** Zoom 

---

## Attendees

| Role | Name |
|------|------|
| Scrum Master | Surya Yousufzai |
| Product Owner | Marwa Paiman |
| Backend Lead Developer | Fariba Mohammadi |
| Frontend Lead Developer | Muneera Aman |
| QA & DevOps Engineer | Gita Rahmany |

---

## Meeting Purpose

This was our Sprint 3 Review and Retrospective, the final demo for our University Event Registration Portal project. The goals were to:
- Demonstrate all admin features completed in Sprint 3
- Get Product Owner acceptance for all user stories
- Review sprint metrics and achievements
- Reflect on what went well and what can be improved
- Officially close Sprint 3 and the entire project

---

## Part 1: Sprint Review

### Opening – by Surya (Scrum Master)

Surya welcomed everyone and confirmed that November 30 is the final day of Sprint 3 and the entire project.

Sprint 3 recap:
- Duration: November 27-30, 2025 (4 days)
- Sprint Goal: Enable administrators to create, manage, and monitor events
- Story points committed: 21 across 4 user stories
- Team successfully delivered all planned features

Meeting agenda:
1. Backend demonstration
2. Frontend demonstration
3. Testing report
4. Product Owner acceptance
5. Sprint metrics review
6. Retrospective discussion

---

### Backend Demo – by Fariba (Backend Lead Developer)

Fariba presented the backend implementation for admin features.

#### Database Enhancements

New stored procedures created:
- `create_event` - Validates date is in future and capacity is positive, automatically sets available seats equal to capacity
- `update_event` - Recalculates available seats when capacity changes while preserving existing registrations
- `delete_event` - Handles cascade deletion of events with all related registrations and payments

#### Seat Recalculation Logic

Fariba explained the complex logic:
- Example: Event has capacity 100, available seats 80 (20 registered)
- If admin increases capacity to 120, new available seats = 100 (80 + 20)
- System maintains the count of already registered users

#### New Queries Implemented

| Query Purpose | Details |
|--------------|---------|
| Dashboard statistics | Total events, total registrations, active events count |
| Event attendees | All registrations for a specific event with user details |
| Event summary view | Events with registration counts and revenue totals |

#### Performance Improvements

New indexes added:
- `idx_events_created_by` - Faster admin event queries
- `idx_events_date` - Better date-based filtering
- `idx_registrations_date` - Improved registration queries

#### Security Enhancement

Created `admin_activity_log` table to track all admin actions for auditing and security monitoring.

#### API Endpoints Demonstrated

| Endpoint | Method | Purpose |
|----------|--------|---------|
| /api/admin/dashboard | GET | Get statistics |
| /api/admin/events | POST | Create event |
| /api/admin/events | GET | List all events |
| /api/admin/events/:id | PUT | Update event |
| /api/admin/events/:id | DELETE | Delete event |
| /api/admin/events/:id/attendees | GET | View attendees |
| /api/admin/events/:id/attendees/export | GET | Export CSV |

All endpoints tested and fully documented.

---

### Frontend Demo – by Muneera (Frontend Lead Developer)

Muneera provided a live walkthrough of the admin interface.

#### Admin Login
- Logged in using credentials: admin@university.edu / admin123
- System correctly identified admin role and redirected to admin dashboard
- Regular users cannot access admin pages

#### Admin Dashboard

Statistics cards displayed:
- Total Events: 6
- Total Registrations: 12
- Active Events: 5

Action cards:
- Create Event (purple card with plus icon)
- Manage Events (purple card with list icon)

Real-time data updates when events or registrations change.

#### Create Event Page

Form demonstrated with all fields:
- Title, Description
- Category dropdown (Music, Tech, Art, Sports)
- Icon selector (emoji options)
- Date picker, Time picker
- Location, Capacity (number), Price (decimal)

Validation testing:
- Past date entry → Error: "Event date must be in the future"
- Negative capacity → Error: "Capacity must be a positive number"
- Missing required fields → Form prevents submission

Successfully created test event "AI Workshop":
- Title: AI Workshop
- Date: December 20, 2025
- Time: 2:00 PM
- Location: Computer Lab
- Capacity: 50
- Price: $20.00

After submission:
- Success message displayed
- Automatic redirect to Manage Events
- Event appeared in the table immediately

#### Manage Events Page

Table columns displayed:
- Title, Date, Location, Capacity, Available, Price, Actions

Action buttons per row:
- View Attendees (blue button)
- Edit (gray button)
- Delete (red button)

#### Edit Event Modal

Clicked Edit on "AI Workshop":
- Modal popup appeared centered on screen
- All form fields pre-filled with current data
- Changed price from $20.00 to $15.00
- Changed capacity from 50 to 60
- Saved changes successfully
- Table updated immediately without page refresh

#### View Attendees Page

Demonstrated with "Tech Innovation Conference" event:
- Event title displayed in header
- Registration count: 2 attendees
- Table showing:
  - Surya Yousufzai, surya@student.edu, Paid, ABCD-1234-EFGH
  - Fariba Mohammadi, fariba@student.edu, Paid, WXYZ-5678-IJKL
- Payment status color-coded (green for Paid, blue for Free)
- Ticket codes displayed in monospace font

#### CSV Export

Clicked Export CSV button:
- File downloaded: Tech_Innovation_Conference_attendees.csv
- Opened file to show format:
  - Headers: Name, Email, Registration Date, Payment Status, Ticket Code
  - Data rows properly formatted
  - Special characters handled correctly

#### Delete Event

Demonstrated delete functionality:
- Clicked Delete button on test event
- Confirmation modal appeared:
  - Warning icon
  - Message: "This will delete all registrations. This action cannot be undone."
  - Cancel and "Yes, Delete" buttons
- Clicked "Yes, Delete"
- Event removed from table
- Success message: "Event and all registrations deleted successfully"

#### Responsive Design

Switched browser to mobile view:
- Dashboard cards stacked vertically
- Form fields single column layout
- Table scrolls horizontally
- All buttons remain accessible
- No layout breaking

Muneera emphasized the entire admin panel is fully responsive and works on all devices.

---

### Testing Report – by Gita (QA & DevOps Engineer)

Gita presented comprehensive testing results for Sprint 3.

#### Test Summary

| Metric | Value |
|--------|-------|
| Test Cases Executed | 15 |
| Passed | 15 |
| Failed | 0 |
| Pass Rate | 100% |

#### Test Cases by Feature

**Admin Authentication (3 test cases)**
1. Admin login with correct credentials - PASSED
2. Admin login with incorrect credentials - PASSED
3. Regular user blocked from admin pages - PASSED

**Create Events (3 test cases)**
1. Create event with valid data - PASSED
2. Create event with past date (validation) - PASSED
3. Create event with negative capacity (validation) - PASSED

**Edit Events (3 test cases)**
1. Edit event title and description - PASSED
2. Edit event capacity (increase) - PASSED
3. Edit event capacity (decrease) - PASSED

**Delete Events (3 test cases)**
1. Delete event with no registrations - PASSED
2. Delete event with registrations (cascade) - PASSED
3. Delete confirmation modal behavior - PASSED

**View Attendees (3 test cases)**
1. View attendees with registrations - PASSED
2. View attendees with no registrations (empty state) - PASSED
3. Export CSV functionality - PASSED

#### Bugs Found and Resolved

| Bug ID | Description | Severity | Status | Resolution Date |
|--------|-------------|----------|--------|-----------------|
| BUG-001 | Edit modal date field showed incorrect format | Medium | FIXED | Nov 28 |
| BUG-002 | Delete modal cancel button didn't close modal | Low | FIXED | Nov 29 |

Both bugs identified during testing and resolved before review.

#### Performance Testing Results

| Operation | Target | Actual | Status |
|-----------|--------|--------|--------|
| Admin dashboard load | < 2s | 0.8s | PASSED |
| Create event response | < 1s | 0.5s | PASSED |
| Load 100 events table | < 2s | 1.2s | PASSED |
| Export CSV (500 records) | < 3s | 2.0s | PASSED |

All performance targets exceeded.

#### Security Testing

Tests performed:
- Admin role verification on all endpoints - PASSED
- Regular users blocked from admin API calls - PASSED
- SQL injection attempts on create event - BLOCKED
- XSS attempts on event description - SANITIZED
- Date validation bypass attempts - BLOCKED

All security measures working correctly.

#### Browser Compatibility

Tested on:
- Chrome 120 - All features working
- Firefox 121 - All features working
- Safari 17 - All features working
- Edge 120 - All features working

Mobile testing:
- iOS Safari - Responsive design perfect
- Android Chrome - Responsive design perfect

No compatibility issues found.

Gita confirmed Sprint 3 deliverables meet all quality standards and are production-ready.

---

### Product Owner Acceptance – by Marwa

Marwa reviewed each user story against acceptance criteria.

#### US-011: Admin Login & Dashboard (3 story points)

Acceptance Criteria:
- Admin can login with special credentials - VERIFIED
- Admin redirected to dashboard after login - VERIFIED
- Dashboard displays total events count - VERIFIED
- Dashboard displays total registrations count - VERIFIED
- Dashboard displays active events count - VERIFIED
- Statistics update in real-time - VERIFIED
- Admin menu provides navigation options - VERIFIED

**Status: ACCEPTED**

#### US-012: Create Events (8 story points)

Acceptance Criteria:
- Admin can access event creation form - VERIFIED
- Form includes all required fields - VERIFIED
- Date validation (future dates only) - VERIFIED
- Capacity validation (positive numbers) - VERIFIED
- Event created successfully with valid data - VERIFIED
- Event appears in manage events list - VERIFIED
- Success message displayed - VERIFIED
- Redirect to manage events after creation - VERIFIED

**Status: ACCEPTED**

#### US-013: Edit/Delete Events (5 story points)

Acceptance Criteria:
- Admin can edit any event field - VERIFIED
- Edit modal pre-fills with current data - VERIFIED
- Seat availability recalculates correctly - VERIFIED
- Changes save and update immediately - VERIFIED
- Admin can delete events - VERIFIED
- Confirmation required before deletion - VERIFIED
- Cascade delete removes registrations - VERIFIED
- Success message after deletion - VERIFIED

**Status: ACCEPTED**

#### US-014: View Attendees (5 story points)

Acceptance Criteria:
- Admin can view list of event attendees - VERIFIED
- Attendee details include name, email, date - VERIFIED
- Payment status displayed and color-coded - VERIFIED
- Ticket codes shown - VERIFIED
- Empty state when no attendees - VERIFIED
- CSV export functionality works - VERIFIED
- CSV format is correct - VERIFIED

**Status: ACCEPTED**

#### Final Acceptance Decision

All 4 user stories accepted.
All 21 story points accepted.
Sprint 3 goal fully achieved.

Marwa's feedback:
"The admin features are exactly what we needed. I'm particularly impressed with the seat recalculation logic and the CSV export feature. The interface is clean, professional, and intuitive. The team has delivered an excellent product. Well done everyone."

Sprint 3 officially accepted and complete.

---

### Sprint 3 Metrics – by Surya (Scrum Master)

#### Story Points Metrics

| Metric | Value |
|--------|-------|
| Story Points Planned | 21 |
| Story Points Completed | 21 |
| Story Points Accepted | 21 |
| Completion Rate | 100% |
| Acceptance Rate | 100% |

#### User Stories Metrics

| Metric | Value |
|--------|-------|
| User Stories Planned | 4 |
| User Stories Completed | 4 |
| User Stories Accepted | 4 |

#### Quality Metrics

| Metric | Value |
|--------|-------|
| Test Cases Executed | 15 |
| Test Cases Passed | 15 |
| Test Pass Rate | 100% |
| Bugs Found | 2 |
| Bugs Fixed | 2 |
| Bugs Remaining | 0 |

#### Sprint Goal Achievement

Sprint Goal: Enable administrators to create, manage, and monitor events

**Status: FULLY ACHIEVED**

#### Deliverables Completed

Sprint 3 delivered:
- Complete admin authentication system
- Admin dashboard with real-time statistics
- Event creation with comprehensive validation
- Event editing with intelligent seat recalculation
- Event deletion with cascade functionality
- Attendee management and viewing
- CSV export for attendee data
- 7 new admin API endpoints
- Database stored procedures and triggers
- Admin activity logging
- Complete documentation

#### Overall Project Metrics

| Sprint | Story Points | Status |
|--------|-------------|--------|
| Sprint 1 | 16 | COMPLETED |
| Sprint 2 | 19 | COMPLETED |
| Sprint 3 | 21 | COMPLETED |
| **Total** | **56** | **COMPLETED** |

#### Project Completion

The University Event Registration Portal is now complete with:
- User registration and authentication
- Event browsing with search and filters
- Event registration for users
- Payment processing integration
- Ticket generation and management
- Complete admin panel for event management
- Attendee tracking and reporting
- Full API documentation
- Comprehensive database design
- 100% test coverage

Project delivered on time with all features implemented and accepted.

---

## Part 2: Sprint Retrospective

### Opening – by Surya (Scrum Master)

Surya transitioned to the retrospective portion, explaining this is our opportunity to reflect on Sprint 3 and identify improvements for future projects.

Focus areas:
- What went well
- What didn't go well
- Action items for improvement

---

### What Went Well

#### Fariba's Feedback
"The backend work went smoothly this sprint. Using stored procedures made the code much cleaner and easier to test. The database design from Sprint 1 really paid off because adding admin features was straightforward. Communication with Muneera on API integration was excellent - we had zero misunderstandings about request and response formats."

#### Muneera's Feedback
"Team communication was outstanding. When I had questions about API responses, Fariba answered immediately. The design patterns we established in Sprint 1 made building the admin UI much faster. Everything just fit together nicely. The modals and forms reused a lot of existing components."

#### Gita's Feedback
"Testing was easier this sprint because everyone documented their work properly. When I found bugs, they were fixed within hours. The code review process we started in Sprint 2 caught issues early. The team really takes quality seriously."

#### Marwa's Feedback
"From a product perspective, the admin features exceeded my expectations. The CSV export was a nice touch that wasn't explicitly in the requirements but adds real value. The team understood user needs without me having to explain every detail. Very mature development process."

#### Surya's Feedback
"I'm proud of how the team handled the tight timeline. We delivered 21 points in just 4 days. Everyone stayed focused and helped each other when needed. The daily standups kept us aligned and caught issues early."

---

### What Didn't Go Well

#### Surya's Observations
"We had a very aggressive timeline - only 4 days for 21 story points. That was risky. We also had some initial confusion about how seat recalculation should work when editing capacity. That discussion took longer than expected and delayed Fariba's work."

#### Fariba's Challenges
"Date formatting was confusing at first. Converting between display format like 'December 15, 2025' and input format like '2025-12-15' took me longer than expected. I also underestimated the complexity of the cascade delete procedure. Testing it required careful setup."

#### Muneera's Challenges
"The modal styling took more time than planned. Getting the modal to center properly on all screen sizes was tricky. The responsive table for manage events wasn't scrolling correctly on mobile initially - that took extra debugging time."

#### Gita's Challenges
"Testing the CSV export was difficult because I needed realistic test data. Setting up scenarios with multiple registrations was time-consuming. Testing cascade deletes also required careful data preparation to verify everything deleted correctly."

---

### Action Items for Future Projects

Surya led the team in identifying concrete action items:

#### 1. Time Estimation Improvement
**Issue:** Underestimated complexity of some features
**Action:** Add 20% buffer to story point estimates for features involving complex logic like seat recalculation or cascade operations
**Owner:** Entire team during planning

#### 2. Continue Documentation Practices
**Issue:** Documentation saved significant time in Sprint 3
**Action:** Maintain practice of documenting as we develop, not at the end
**Owner:** All developers

#### 3. Create Reusable Test Data Scripts
**Issue:** Setting up test data for QA was time-consuming
**Action:** Create SQL scripts and API scripts to quickly populate test scenarios
**Owner:** Gita with input from Fariba

#### 4. Maintain Code Review Process
**Issue:** Code reviews caught bugs early
**Action:** Continue mandatory code reviews for all features before merging
**Owner:** Surya to enforce, all developers to participate

#### 5. Technical Discussion Documentation
**Issue:** Seat recalculation logic discussion wasn't documented initially
**Action:** Document technical decisions and logic in comments and documentation
**Owner:** Fariba and Muneera

Team consensus: All action items approved and will be applied to future projects.

---

### Team Appreciation

Each team member shared appreciation for others:

**Fariba:** "Thanks to Muneera for being so responsive on API questions. Thanks to Gita for thorough testing."

**Muneera:** "Thanks to Fariba for clean API design. Thanks to Surya for keeping us organized."

**Gita:** "Thanks to everyone for taking quality seriously. Makes my job easier when code is already good."

**Marwa:** "Thanks to Surya for excellent scrum mastering. Thanks to the whole team for professionalism."

**Surya:** "Thanks to everyone for dedication and teamwork. This project turned out great because of all of you."

---

## Closing Remarks

### Final Thoughts by Team Members

| Team Member | Closing Statement |
|-------------|-------------------|
| Fariba | "Great sprint. Enjoyed the technical challenges. Proud of what we built." |
| Muneera | "Team support was amazing. Love how the UI turned out." |
| Gita | "Impressed with the quality. This is a portfolio-worthy project." |
| Marwa | "This is how Scrum should work. Excellent collaboration and results." |
| Surya | "Sprint 3 complete. Project complete. Thank you everyone." |

---

## Key Decisions

- Sprint 3 completed and fully accepted
- All 56 story points across 3 sprints delivered successfully
- University Event Registration Portal project officially complete
- Action items documented for future projects
- Team demonstrated excellent Scrum practices

---

## Challenges Overcome

| Challenge | Resolution |
|-----------|------------|
| Tight 4-day timeline | Team focus and daily coordination |
| Complex seat recalculation logic | Technical discussion and iteration |
| Date format conversion | Helper functions created |
| Modal responsive design | Extra time invested in CSS |
| CSV export testing | Created test data setup |

---

## Project Summary

**Total Duration:** November 15-30, 2025 (16 days across 3 sprints)

**Final Deliverables:**
- Fully functional web application
- Complete admin panel
- User registration and authentication
- Event management system
- Payment processing
- Ticket generation
- Attendee tracking
- Database with triggers and procedures
- Complete API documentation
- Test coverage: 100%

**Final Metrics:**
- Total Story Points: 56
- Completion Rate: 100%
- Test Pass Rate: 100%
- Code Quality: Production-ready

---

**Recording Link:* https://drive.google.com/file/d/1gx7cd6OuI-Kg1QTXH0Z8aknuLXpimYFv/view?usp=drive_link* 

**Document Prepared By:** Surya Yousufzai (Scrum Master)  
**Date Completed:** November 30, 2025

