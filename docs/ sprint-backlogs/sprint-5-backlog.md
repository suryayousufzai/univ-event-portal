# Sprint 5 Backlog

**Project:** University Event Registration Portal  
**Sprint:** Sprint 5  
**Duration:** December 3-5, 2025 (3 days)  
**Sprint Goal:** Complete final features and prepare system for production

---

## Sprint Overview

Sprint 5 is our final sprint. The MVP is complete from Sprints 1-4, so now we're adding the last important features that users actually need. We're keeping it simple and realistic - just 3 days to finish everything and prepare for deployment.

We picked features that are useful and achievable, not trying to do everything.

---

## Sprint Backlog Items

| ID | User Story | Story Points | Status | Assigned To |
|----|------------|--------------|--------|-------------|
| US-003 | User Profile Management | 3 | Not Started | Fariba + Muneera |
| US-005 | Advanced Search & Filters | 8 | Not Started | Muneera + Gita |
| US-010 | Cancel Registration | 5 | Not Started | Fariba + Muneera |
| NFR-005 | Browser Compatibility Testing | 3 | Not Started | Gita |
| NFR-008 | Code Documentation | 5 | Not Started | Everyone |

**Total Story Points:** 24

---


## What We're NOT Doing in Sprint 5

We decided to skip these for now because they're either too complex or not essential:

- US-017: Multi-language support (8 points) - Nice to have but not critical
- US-018: Audit log (8 points) - Can be added later if needed
- US-019: Accessibility (8 points) - Would require major UI changes
- NFR-003: 100 concurrent users testing (13 points) - Too complex in that mush time
- NFR-004: Daily backups (5 points) - Production concern, not for demo
- NFR-006: Data protection compliance (8 points) - Already following basic practices
- NFR-007: Network failure recovery (5 points) - Out of scope

We picked features that will actually be used and make the portal better for real users.

---

## Task Breakdown by Feature

### US-003: User Profile Management (3 points)

**What it does:**  
Users can edit their profile information and change their password.

**Why we need it:**  
Right now users can't update their info if it changes. This is basic functionality every system should have.

**Acceptance Criteria:**
- User can access profile page from menu
- User can edit: name, email, student ID
- User can change password (must enter old password first)
- Changes saved to database
- Success message shown
- Form validation works

**Backend Tasks (Fariba):**
- [ ] Create API: GET /api/users/:id/profile (return current user info)
- [ ] Create API: PUT /api/users/:id/profile (update name, email, student ID)
- [ ] Create API: PUT /api/users/:id/password (verify old password, save new password)
- [ ] Hash passwords properly
- [ ] Test in Postman

**Frontend Tasks (Muneera):**
- [ ] Build User Profile page
- [ ] Add "Profile" link to navbar
- [ ] Form with current data pre-filled
- [ ] Change Password section (old password, new password, confirm)
- [ ] Connect to APIs
- [ ] Show success/error messages
- [ ] Make responsive

**QA Tasks (Gita):**
- [ ] Test updating profile with valid data
- [ ] Test with invalid data
- [ ] Test changing password correctly
- [ ] Test with wrong old password
- [ ] Test with weak new password

---

### US-005: Advanced Search & Filters (8 points)

**What it does:**  
Users can search events by keyword and filter by category, date, and price.

**Why we need it:**  
Right now all events just show in a list. With many events, users can't find what they want easily.

**Acceptance Criteria:**
- Search box at top of events page
- Search works on title and description
- Filter by category (tech, sports, cultural, academic, all)
- Filter by date range
- Filter by price (free, paid, all)
- Results update as user types/selects
- "Clear filters" button
- Shows "No events found" if no results
- Shows count: "12 events found"

**Backend Tasks (Fariba):**
- [ ] Update GET /api/events endpoint
- [ ] Add query parameters: search, category, dateFrom, dateTo, priceFilter
- [ ] Filter events in SQL query
- [ ] Return filtered results
- [ ] Test with different combinations

**Frontend Tasks (Muneera):**
- [ ] Add search bar to Events page (search icon)
- [ ] Search as user types (500ms delay)
- [ ] Add category dropdown
- [ ] Add date range picker (from and to)
- [ ] Add price filter (checkboxes: Free / Paid / All)
- [ ] Add "Clear Filters" button
- [ ] Connect to API with query parameters
- [ ] Update event list when filters change
- [ ] Show empty state if no results
- [ ] Show count of results

**QA Tasks (Gita):**
- [ ] Test search with different keywords
- [ ] Test each filter individually
- [ ] Test combining multiple filters
- [ ] Test clearing filters
- [ ] Test with no results
- [ ] Test with special characters

---

### US-010: Cancel Registration (5 points)

**What it does:**  
Users can cancel their event registration if they can't attend.

**Why we need it:**  
Plans change. Users should be able to cancel, and it frees up the seat for others.

**Acceptance Criteria:**
- "Cancel Registration" button on My Events page
- Confirmation popup before cancelling
- Registration deleted from database
- Seat becomes available again
- Refund processed if paid event (simulated)
- Cancellation email sent
- User sees updated list

**Backend Tasks (Fariba):**
- [ ] Create API: DELETE /api/registrations/:id
- [ ] Check registration belongs to logged-in user
- [ ] Delete registration
- [ ] Increase available_seats by 1
- [ ] Mark as refunded if paid (simulate)
- [ ] Trigger cancellation email
- [ ] Return success

**Frontend Tasks (Muneera):**
- [ ] Add "Cancel Registration" button to My Events
- [ ] Only show for upcoming events
- [ ] Red button style
- [ ] Create confirmation modal
- [ ] Warning: "Are you sure? You can't undo this."
- [ ] Connect to API
- [ ] Show loading state
- [ ] Remove event from list after success
- [ ] Show success message

**QA Tasks (Gita):**
- [ ] Test cancelling free event
- [ ] Test cancelling paid event
- [ ] Test seat becomes available
- [ ] Test can't cancel other user's registration
- [ ] Test cancellation email sent
- [ ] Test can't cancel past events

---

### NFR-005: Browser Compatibility Testing (3 points)

**What it does:**  
Make sure the portal works on all major browsers.

**Why we need it:**  
Different students use different browsers. We need it to work for everyone.

**Acceptance Criteria:**
- Works on Chrome (latest)
- Works on Firefox (latest)
- Works on Edge (latest)
- Works on Safari if available
- All major features tested
- Bugs documented and fixed

**QA Tasks (Gita):**
- [ ] Test on Chrome: registration, login, browse, register, payment, admin
- [ ] Test on Firefox: same features
- [ ] Test on Edge: same features
- [ ] Test on Safari if possible
- [ ] Test responsive design on each
- [ ] Document issues
- [ ] Report to team for fixes
- [ ] Retest after fixes

**Team Tasks:**
- [ ] Fariba and Muneera fix any bugs found

---

### NFR-008: Code Documentation (5 points)

**What it does:**  
Add comments and documentation to all code.

**Why we need it:**  
Good documentation helps future maintenance. Required for class project submission.

**Acceptance Criteria:**
- All backend functions have comments
- All frontend components have comments
- Database schema documented
- README explains how to run project
- API documentation complete
- Deployment instructions written

**Backend Tasks (Fariba):**
- [ ] Add comments to all API endpoints
- [ ] Document database schema
- [ ] Write backend README
- [ ] Document environment variables

**Frontend Tasks (Muneera):**
- [ ] Add comments to all components
- [ ] Write frontend README
- [ ] Document how to build for production

**QA Tasks (Gita):**
- [ ] Review all documentation
- [ ] Test instructions work
- [ ] Write testing documentation

**Scrum Master Tasks (Surya):**
- [ ] Compile all documentation
- [ ] Create final project report
- [ ] Organize files for submission

---

## Definition of Done (Sprint 5)

A feature is "Done" when:
- [ ] Code complete and working
- [ ] All test cases passed
- [ ] No bugs
- [ ] Code has comments
- [ ] Tested on multiple browsers
- [ ] Code pushed to GitHub
- [ ] Product Owner accepted

---

## Sprint 5 Schedule

**Day 1 (Dec 3):**
- Morning: Sprint Planning meeting
- Morning: Start profile and search features
- Afternoon: Gita starts browser testing
- End of Day: Profile 70% done, Search 40% done

**Day 2 (Dec 4):**
- Morning: Complete profile feature
- Afternoon: Continue search and start cancel registration
- Evening: Profile 100% done, Search 70% done, Cancel 30% done

**Day 3 (Dec 5):**
- Morning: Finish all features
- Afternoon: Final testing, fix bugs, complete documentation
- Evening: Sprint Review meeting
- Evening: Sprint Retrospective and project closure

---

## Team Capacity

**Sprint Duration:** 3 days

**Team Velocity History:**
- Sprint 1: 16 points in 7 days = 2.3 pts/day
- Sprint 2: 19 points in 4 days = 4.75 pts/day
- Sprint 3: 21 points in 4 days = 5.25 pts/day
- Sprint 4: 15 points in 2 days = 7.5 pts/day
- Sprint 5: 24 points in 3 days = 8 pts/day (high but achievable)

**Why 24 points in 3 days is achievable:**
- Team is very experienced now (5th sprint)
- Features are straightforward
- No complex integrations
- Documentation can be done in parallel

---

## Technical Notes

**Profile Management:**
- Use existing users table
- Password change needs bcrypt hashing
- Validate email format

**Search & Filters:**
- Backend: SQL WHERE clauses
- Frontend: Debouncing (wait 500ms after typing)
- No complex search engine needed

**Cancel Registration:**
- Delete from registrations table
- Update available_seats in events table
- Simple SQL transaction

**Browser Testing:**
- Test on real browsers, not just Chrome
- Document CSS issues
- Priority: Chrome > Firefox > Edge > Safari

**Documentation:**
- Write as you code, not at the end
- Keep it simple and clear
- Include setup instructions

---

## Risks & Mitigations

**Risk:** Search might be slow with many events  
**Mitigation:** Keep search simple, use database indexes

**Risk:** Browser testing finds major issues late  
**Mitigation:** Gita starts testing on Day 1

**Risk:** Documentation takes too long  
**Mitigation:** Everyone documents as they code

**Risk:** 24 points in 3 days is tight  
**Mitigation:** Features are simpler than previous sprints

---

## Success Criteria

Sprint 5 is successful if:
- ✅ Users can edit their profiles
- ✅ Search and filters work smoothly
- ✅ Users can cancel registrations
- ✅ Portal works on all major browsers
- ✅ All code is documented
- ✅ Zero critical bugs
- ✅ Project ready for deployment

---

## What We're NOT Doing

To keep Sprint 5 realistic, we decided to skip:
- US-017: Multi-language support (8 points) - Too complex
- US-018: Audit log (8 points) - Not essential for MVP
- US-019: Accessibility (8 points) - Major work, can be added later
- NFR-003: Load testing (13 points) - Overkill for class project
- NFR-004: Daily backups (5 points) - Production concern
- NFR-006: Compliance (8 points) - Already following basics
- NFR-007: Network recovery (5 points) - Out of scope

These can be added in future versions if needed.

---

## Notes on Sprint 5

This is our final sprint. After Sprint 5:
- Portal is feature-complete
- All documentation done
- Ready for pilot testing
- Ready for final submission

We're focusing on:
1. User experience (profile, search, cancel)
2. Quality (browser testing)
3. Maintainability (documentation)

These features make the portal feel complete and professional. After Sprint 5, we'll have delivered 95 story points across 5 sprints - a solid university event registration system.

---

**Prepared by:** Surya Yousufzai (Scrum Master)  
**Approved by:** Marwa Payman (Product Owner)  
**Date:** December 3, 2025
