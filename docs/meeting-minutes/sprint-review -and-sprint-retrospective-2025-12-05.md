# Sprint Review and Retrospective Meeting – Sprint 5

**Project:** University Event Registration Portal  
**Meeting Type:** Sprint 5 Review and Retrospective  
**Date:** December 5, 2025  
**Duration:** 35 minutes  
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

This was our Sprint 5 Review and Retrospective, the final meeting for the entire project. The goals were to:
- Demonstrate all features completed in Sprint 5
- Get Product Owner acceptance for all user stories
- Review sprint metrics and overall project achievements
- Reflect on what we learned throughout the project
- Officially close Sprint 5 and celebrate project completion

---

## Part 1: Sprint Review

### Opening – by Surya (Scrum Master)

Surya welcomed everyone to the final sprint review.

Sprint 5 recap:
- Duration: December 3-5, 2025 (3 days)
- Sprint Goal: Complete final features and prepare system for production
- Story points committed: 24 across 5 user stories
- This is the final sprint of the entire project

Meeting agenda:
1. Feature demonstrations
2. Testing results
3. Product Owner acceptance
4. Sprint and project metrics
5. Retrospective discussion

---

### Feature Demonstrations

#### Feature 1: Profile Management – by Fariba & Muneera

**Fariba (Backend):**

Created 3 API endpoints for profile management:
- GET /api/users/:id/profile - Returns user's current info
- PUT /api/users/:id/profile - Updates name, email, student ID
- PUT /api/users/:id/password - Changes password securely

Password change security:
- Verifies old password before allowing new one
- Uses bcrypt hashing for all passwords
- Returns clear error messages

All tested in Postman. Response times under 200ms.

**Muneera (Frontend):**

Built clean profile page:
- Added "Profile" link to navigation menu
- Form pre-fills with current user data
- Users can edit name, email, student ID
- Separate "Change Password" section with 3 fields
- Form validation before submission
- Green success messages or red error messages
- Fully responsive on mobile

Demo showed updating profile and changing password successfully.

**Status:** Complete and working perfectly.

---

#### Feature 2: Advanced Search & Filters – by Fariba & Muneera

**Fariba (Backend):**

Updated GET /api/events endpoint with query parameters:
- Search by keyword (searches title and description)
- Filter by category (tech, sports, cultural, academic)
- Filter by date range (dateFrom and dateTo)
- Filter by price (free, paid, all)

All filtering in SQL using WHERE clauses for efficiency.  
Added database indexes for faster searches.  
Tested with different filter combinations - all working.

**Muneera (Frontend):**

Added search and filter UI to Events page:
- Search bar with 500ms debounce (smooth searching as you type)
- Category dropdown
- Two date pickers for date range
- Checkboxes for price filters
- "Clear Filters" button
- Shows result count: "12 events found"
- Empty state if no results

Demo showed searching for "tech", filtering by date and price - instant results.

**Status:** Works smoothly and intuitively.

---

#### Feature 3: Cancel Registration – by Fariba & Muneera

**Fariba (Backend):**

Created DELETE /api/registrations/:id endpoint:
- Verifies registration belongs to logged-in user (security)
- Deletes registration from database
- Increases available_seats by 1
- Marks as refunded if paid event (simulated)
- Triggers cancellation email
- All in one database transaction

**Muneera (Frontend):**

Added to My Events page:
- Red "Cancel Registration" button (only for upcoming events)
- Confirmation modal with warning: "You can't undo this"
- Loading spinner during cancellation
- Event removed from list after success
- Success message displayed

Demo showed cancelling an event - seat became available again immediately.

**Status:** Complete with security and email notification.

---

### Testing Report – by Gita (QA & DevOps Engineer)

#### Test Summary

| Metric | Value |
|--------|-------|
| Test Cases Created | 18 |
| Test Cases Executed | 18 |
| Passed | 18 |
| Failed | 0 |
| Pass Rate | 100% |

#### Test Cases by Feature

**Profile Management (6 test cases)**
- Update profile with valid data - PASSED
- Update with invalid data - PASSED
- Change password correctly - PASSED
- Change password with wrong old password - PASSED
- Change to weak password - PASSED
- Empty fields validation - PASSED

**Search & Filters (7 test cases)**
- Search by keyword - PASSED
- Filter by category - PASSED
- Filter by date range - PASSED
- Filter by price - PASSED
- Combine all filters - PASSED
- Clear filters - PASSED
- Special characters in search - PASSED

**Cancel Registration (5 test cases)**
- Cancel free event - PASSED
- Cancel paid event - PASSED
- Seat becomes available - PASSED
- Can't cancel others' registrations - PASSED
- Cancellation email sent - PASSED

#### Browser Compatibility Testing

Tested on:
- Chrome 120 - All features working ✅
- Firefox 121 - All features working ✅
- Edge 120 - All features working ✅

Note: Found small CSS issue on Edge on Day 1, Muneera fixed it within an hour.

#### Sprint 5 Quality

- Zero bugs found in final testing
- All features work on all browsers
- Everything responsive on mobile
- Code documented and clean

**Conclusion:** Sprint 5 is production-ready.

---

### Product Owner Acceptance – by Marwa

Marwa reviewed each user story.

#### US-003: User Profile Management (3 points)

All acceptance criteria met:
- Profile page accessible ✅
- Can edit name, email, student ID ✅
- Can change password ✅
- Old password verified ✅
- Success messages work ✅
- Form validation works ✅

**Status: ACCEPTED**

#### US-005: Advanced Search & Filters (8 points)

All acceptance criteria met:
- Search by keyword ✅
- Filter by category ✅
- Filter by date range ✅
- Filter by price ✅
- Results update in real-time ✅
- Clear filters button ✅
- Shows result count ✅
- Empty state when no results ✅

**Status: ACCEPTED**

#### US-010: Cancel Registration (5 points)

All acceptance criteria met:
- Cancel button on My Events ✅
- Confirmation modal ✅
- Registration deleted ✅
- Seat becomes available ✅
- Refund simulated ✅
- Email notification sent ✅

**Status: ACCEPTED**

#### NFR-005: Browser Compatibility (3 points)

All tested and working:
- Chrome ✅
- Firefox ✅
- Edge ✅
- All features tested ✅

**Status: ACCEPTED**

#### NFR-008: Code Documentation (5 points)

All completed:
- Backend comments ✅
- Frontend comments ✅
- README files ✅
- API documentation ✅

**Status: ACCEPTED**

**Final Decision:** All 24 story points ACCEPTED. Sprint 5 goal fully achieved.

Marwa's feedback: "These final features complete the portal perfectly. Search makes it usable with many events. Profile management is essential. Cancel registration gives users flexibility. The quality is excellent. Well done team!"

---

### Sprint 5 Metrics – by Surya

#### Story Points

| Metric | Value |
|--------|-------|
| Planned | 24 |
| Completed | 24 |
| Accepted | 24 |
| Completion Rate | 100% |

#### Quality Metrics

| Metric | Value |
|--------|-------|
| Test Cases | 18 |
| Passed | 18 |
| Bugs Found | 0 |
| Pass Rate | 100% |

#### Sprint Performance

- Duration: 3 days
- Velocity: 8 points per day (highest of all sprints!)
- Features: 5 user stories delivered
- Quality: Zero bugs, 100% browser compatibility

#### Sprint 5 Deliverables

- User profile management with password change
- Advanced search with multiple filters
- Cancel registration with seat recalculation
- Browser compatibility testing (Chrome, Firefox, Edge)
- Comprehensive code documentation

---

### Overall Project Summary – by Surya

#### All 5 Sprints Overview

| Sprint | Duration | Points | Status |
|--------|----------|--------|--------|
| Sprint 1 | 7 days | 16 | COMPLETED |
| Sprint 2 | 4 days | 19 | COMPLETED |
| Sprint 3 | 4 days | 21 | COMPLETED |
| Sprint 4 | 2 days | 15 | COMPLETED |
| Sprint 5 | 3 days | 24 | COMPLETED |
| **Total** | **20 days** | **95** | **COMPLETED** |

#### What We Built

**Sprint 1:** User registration, login, event browsing  
**Sprint 2:** Event registration, payments, tickets  
**Sprint 3:** Admin panel, create/edit/delete events, view attendees  
**Sprint 4:** Reports dashboard, PDF export, email notifications  
**Sprint 5:** Profile management, search, cancel registration

#### Final System Features

Complete university event portal with:
- User registration and authentication
- Event browsing with search and filters
- Online payment processing
- Ticket generation
- Full admin management
- Reports and analytics
- Email notifications
- Profile management
- Registration cancellation
- Browser compatible
- Mobile responsive
- Fully documented

**Total:** 95 story points delivered over 20 days!

---

## Part 2: Sprint Retrospective

### What Went Well

**Fariba:**  
"Great teamwork in Sprint 5. Muneera and I coordinated perfectly on APIs. Our highest velocity - 8 points per day - shows how experienced we've become. Smart technical decisions kept things simple and maintainable."

**Muneera:**  
"Everyone was super responsive. When Gita found the Edge bug, I fixed it fast. Search feature turned out amazing. Documentation came together smoothly because everyone wrote comments as they coded."

**Gita:**  
"Zero bugs in Sprint 5! That's incredible. Starting browser testing early on Day 1 helped us catch issues fast. We now have over 60 test cases for the whole project."

**Surya:**  
"Planning and execution were perfect. Daily standups kept us aligned. Completing 24 points in 3 days with zero bugs is outstanding. This team became highly efficient."

---

### Challenges We Faced

**Fariba:**  
"Tight timeline - 24 points in 3 days felt aggressive. Had to think carefully about cancel registration transaction logic to make sure nothing breaks."

**Muneera:**  
"Designing search UI with all those filters without overwhelming users took several iterations. Coordinating timing with Fariba on backend readiness needed patience."

**Gita:**  
"Testing 3 features plus browser compatibility in 3 days was a lot. But starting early and testing continuously made it work."

---

### Key Learnings from Sprint 5

**Fariba:**  
"Building flexible APIs with optional parameters is better than multiple endpoints. Improved my API security skills with cancel registration."

**Muneera:**  
"Learned debouncing for search optimization. Better at browser compatibility testing and CSS debugging now."

**Gita:**  
"Early and continuous testing catches issues when they're easy to fix. My test documentation skills improved a lot."

---

### Key Learnings from Entire Project

**Fariba:**  
"Learned how Agile Scrum works - daily standups, sprint planning, reviews really help. Can break big features into small tasks now. Learned payment integration, email systems, API design, database optimization. Ready for professional development!"

**Muneera:**  
"User experience is as important as functionality. Learned responsive design deeply. Working with Fariba taught me backend collaboration. Learned React components, CSS Grid, form validation. Design requires iteration and feedback."

**Gita:**  
"Learned comprehensive QA - test cases, execution, documentation, regression testing. Testing isn't just finding bugs, it's building confidence. Browser compatibility testing was new. Quality is everyone's responsibility!"

---

### What We're Most Proud Of

**Fariba:** "Payment integration in Sprint 2. Complex but zero payment bugs throughout the project."

**Muneera:** "The overall UI. Professional, modern, clean. Users will enjoy using it."

**Gita:** "Quality metrics. 60+ test cases, high pass rates, stable system."

**Marwa:** "This team. Great communication, support, consistent delivery. This is how Agile should work."

**Surya:** "The team's growth. From uncertain in Sprint 1 to efficient in Sprint 5. Built something meaningful."

---

### Future Recommendations

**Fariba:** Add multi-language, audit logs, real email with university SMTP, automated backups

**Muneera:** More animations, mobile app, dark mode

**Gita:** Automated testing, continuous integration, load testing

**Marwa:** Pilot testing with real students, gather feedback, iterate

---

## Closing Remarks

### Final Words – by Surya

"Twenty days ago we started with nothing. Today we have a complete university event registration portal with 95 story points delivered.

We followed Agile Scrum perfectly. Five sprints. Daily standups. Reviews. Retrospectives. Story points. Velocity tracking.

Most importantly, we worked as a team. Communicated openly. Helped each other. Delivered quality work.

Fariba, Muneera, Gita, Marwa - thank you. It's been an honor.

This project is complete. We should all be very proud!"

### Team Celebration

**Fariba:** "Amazing project! Thanks everyone!"

**Muneera:** "Great team! Love what we built!"

**Gita:** "Proud of this quality work!"

**Marwa:** "Outstanding job everyone! Congratulations!"

---

## Key Decisions

- Sprint 5 completed and fully accepted
- All 95 story points across 5 sprints delivered successfully
- University Event Registration Portal project officially complete
- System ready for pilot testing and deployment

---

## Project Final Status

**Total Duration:** November 15 - December 5, 2025 (20 days)

**Final Deliverables:**
- Complete web application
- User and admin functionality
- Payment processing
- Search and filters
- Reports and analytics
- Email notifications
- Mobile responsive
- Browser compatible
- 100% documented
- Production-ready

**Final Metrics:**
- Total Story Points: 95
- Completion Rate: 100%
- Test Pass Rate: 100%
- Bugs: 0
- Quality: Production-ready

---

**Recording Link:** (https://drive.google.com/file/d/1bWzU9ESG15gQJmJ3xcSnHa3d6_aE2GaG/view?usp=drive_link)

**Document Prepared By:** Surya Yousufzai (Scrum Master)  
**Date Completed:** December 5, 2025



























































