# Sprint 4 Backlog

**Project:** University Event Registration Portal  
**Sprint:** Sprint 4  
**Duration:** December 1-2, 2025 (2 days)  
**Sprint Goal:** Add reporting, notifications, and export features to improve system usability

---

## Sprint Overview

Sprint 4 is our shortest sprint - just 2 days. We're adding important features that make the portal more professional and useful. Admins need better reporting to see how events are performing, users need email notifications when they register, and we need to improve the attendee export feature we started in Sprint 3.

This sprint is about polish and usability improvements rather than building completely new features.

---

## Sprint Backlog Items

| ID | User Story | Story Points | Status | Assigned To |
|----|------------|--------------|--------|-------------|
| ENHANCE-014 | Export Enhancements (PDF + Improved CSV) | 5 | Not Started | Fariba + Muneera + Gita |
| US-015 | Basic Reports Dashboard | 5 | Not Started | Fariba + Muneera + Gita |
| US-016 | Automated Email Notifications | 5 | Not Started | Fariba + Muneera + Gita |

**Total Story Points:** 15

**Note:** ENHANCE-001 is an enhancement to US-014 (View Attendees) which was completed in Sprint 3. We're adding PDF export capability and improving the CSV format.

---

## Task Breakdown by Feature

---

### ENHANCE-001: Export Enhancements - PDF & Improved CSV (5 points)

**What it does:**
In Sprint 3, we built the view attendees page with basic CSV export. Now we're adding PDF export and improving the CSV format to make it more professional. This is an enhancement to US-014 that was completed in Sprint 3.

**Acceptance Criteria:**
- Admins can export attendee lists as CSV (already exists, we're improving it)
- Admins can export attendee lists as PDF (new feature)
- CSV format includes headers and is clean
- PDF format looks professional with proper formatting
- Both exports include: name, email, registration date, payment status, ticket code
- File names are clear: EventName_attendees.csv or EventName_attendees.pdf

**Backend Tasks (Fariba):**
- [ ] Create PDF export API endpoint: GET /api/admin/events/:id/attendees/export-pdf
  - Use a PHP PDF library (like FPDF or TCPDF)
  - Format data into a professional table
  - Add event name as header
  - Include university logo if time permits
- [ ] Improve CSV export endpoint (already exists from Sprint 3)
  - Add better formatting
  - Make sure special characters don't break the format
  - Add proper headers row
- [ ] Test both exports with different data sizes

**Frontend Tasks (Muneera):**
- [ ] Go to View Attendees page (built in Sprint 3)
- [ ] Add second export button: "Export as PDF"
- [ ] Style the two export buttons nicely
  - CSV button in green
  - PDF button in red
- [ ] Connect PDF button to new API endpoint
- [ ] Test both downloads work properly
- [ ] Show loading spinner while export is generating

**QA Tasks (Gita):**
- [ ] Test CSV export with event that has many attendees (50+)
- [ ] Test CSV export with event that has few attendees (1-2)
- [ ] Test CSV export with event that has no attendees
- [ ] Test PDF export with same scenarios
- [ ] Open exported files to verify formatting
- [ ] Check that special characters in names don't break format
- [ ] Verify file names are correct

---

### US-015: Basic Reports Dashboard (5 points)

**What it does:**
Create a reports page for admins showing key statistics about the portal. This helps university staff understand how the system is being used.

**Acceptance Criteria:**
- New "Reports" page accessible from admin menu
- Shows total number of events created
- Shows total number of registrations across all events
- Shows total revenue collected from paid events
- Shows number of active users (users who registered for at least one event)
- All numbers are accurate
- Page is clean and easy to read
- No complex charts needed - just the numbers displayed nicely

**Backend Tasks (Fariba):**
- [ ] Create Reports API endpoint: GET /api/admin/reports
- [ ] Write SQL query to count total events
- [ ] Write SQL query to count total registrations
- [ ] Write SQL query to calculate total revenue (sum of all payments)
- [ ] Write SQL query to count active users (distinct users with registrations)
- [ ] Return all statistics as JSON
- [ ] Test calculations manually to verify accuracy

**Frontend Tasks (Muneera):**
- [ ] Create new Reports page
- [ ] Add "Reports" option to admin menu
- [ ] Design 4 statistic cards:
  - Card 1: Total Events (with calendar icon)
  - Card 2: Total Registrations (with users icon)
  - Card 3: Total Revenue (with dollar icon, formatted as currency)
  - Card 4: Active Users (with user icon)
- [ ] Make cards colorful and modern looking
- [ ] Connect to Reports API to get data
- [ ] Show loading state while data loads
- [ ] Display numbers in large, easy-to-read format
- [ ] Make page responsive for mobile

**QA Tasks (Gita):**
- [ ] Manually calculate statistics from database
- [ ] Compare manual calculations to what Reports page shows
- [ ] Verify all numbers are accurate
- [ ] Test page on different browsers
- [ ] Test page on mobile device
- [ ] Verify page loads quickly

---

### US-016: Automated Email Notifications (5 points)

**What it does:**
Send automatic emails to users when they register for events, make payments, or cancel registrations. This makes the system feel more professional and keeps users informed.

**Acceptance Criteria:**
- Email sent when user registers for free event
- Email sent when user completes payment for paid event
- Email sent when user cancels registration
- All emails contain relevant information (event name, date, time, location)
- Emails use professional templates
- Emails actually send and arrive in user's inbox

**Backend Tasks (Fariba):**
- [ ] Set up email sending system
  - Use PHPMailer or similar library
  - Configure SMTP settings (use Gmail SMTP for testing)
  - Test that emails can send
- [ ] Create 3 email templates:
  - Registration confirmation email
  - Payment confirmation email
  - Cancellation confirmation email
- [ ] Integrate email sending into registration flow
  - After user registers, trigger registration email
- [ ] Integrate email sending into payment flow
  - After payment succeeds, trigger payment email
- [ ] Integrate email sending into cancellation flow
  - After cancellation, trigger cancellation email
- [ ] Test all three email types

**Email Content Requirements:**
- Registration Email: "Thanks for registering for [Event Name]! Event details: Date, Time, Location. Your ticket code: [CODE]"
- Payment Email: "Payment confirmed for [Event Name]! Amount paid: $X. Your ticket code: [CODE]. See you at the event!"
- Cancellation Email: "Your registration for [Event Name] has been cancelled. Refund processed if applicable."

**Frontend Tasks (Muneera):**
- [ ] Add small notification after registration: "Confirmation email sent to your inbox"
- [ ] Add notification after payment: "Receipt sent to your email"
- [ ] (Optional if time permits) Add email preferences to user profile
  - Checkbox: "Send me email notifications"

**QA Tasks (Gita):**
- [ ] Register for test event and check email arrives
- [ ] Make test payment and check payment email arrives
- [ ] Cancel test registration and check cancellation email arrives
- [ ] Verify all emails contain correct information
- [ ] Check emails don't go to spam folder
- [ ] Test with different email providers (Gmail, Yahoo, Outlook)
- [ ] Verify emails look good on mobile email apps

---

## Definition of Done (Sprint 4)

A feature is "Done" when:
- [ ] Backend API complete and tested
- [ ] Frontend UI complete and responsive
- [ ] Backend and frontend integrated
- [ ] All test cases passed
- [ ] No critical bugs
- [ ] Emails actually sending (for US-016)
- [ ] Exports generate properly (for US-014)
- [ ] Numbers are accurate (for US-015)
- [ ] Code pushed to GitHub
- [ ] Documentation updated
- [ ] Product Owner has accepted

---

## Sprint 4 Schedule

This is a very tight 2-day sprint, so we need to be efficient.

**Day 1 (December 1):**
- Morning: Sprint Planning meeting
- Morning: Start all three features in parallel
  - Fariba: Set up email system and start reports API
  - Muneera: Start reports page design
  - Gita: Write test cases
- Afternoon: Continue building
  - Fariba: Complete reports API, start export improvements
  - Muneera: Complete reports page, start export buttons
  - Gita: Test reports feature
- End of Day 1 Goal: Reports feature 100% complete, Exports 50% complete, Emails 30% complete

**Day 2 (December 2):**
- Morning: Finish remaining features
  - Fariba: Complete email integration, finish PDF export
  - Muneera: Complete export buttons, add email notifications
  - Gita: Test exports and emails
- Afternoon: Final testing and polish
  - Fix any bugs found
  - Make sure everything works smoothly
  - Final documentation
- Evening: Sprint Review meeting (5 PM)
- Evening: Sprint Retrospective meeting (5:30 PM)

---

## Team Capacity

**Sprint Duration:** 2 days (shortest sprint)

**Team Velocity History:**
- Sprint 1: 16 points in 7 days = 2.3 points/day
- Sprint 2: 19 points in 4 days = 4.75 points/day
- Sprint 3: 21 points in 4 days = 5.25 points/day
- Sprint 4: 15 points in 2 days = 7.5 points/day (aggressive but doable)

**Why we think 15 points in 2 days is achievable:**
- Team is very experienced now (4th sprint)
- We're enhancing existing features, not building from scratch
- Reports is mostly just queries and display
- Email setup is straightforward with PHPMailer
- Exports are improvements to existing code from Sprint 3

---

## Technical Notes

**Email Setup:**
- Use PHPMailer library (already available in PHP)
- Configure Gmail SMTP for sending
  - SMTP Host: smtp.gmail.com
  - Port: 587
  - Use app-specific password for security
- Emails will be plain HTML format (not fancy templates)
- For testing, we can send emails to our own addresses

**PDF Generation:**
- Use TCPDF or FPDF library for PHP
- Generate simple table with attendee data
- No need for complex styling - basic professional look is fine

**Reports Calculations:**
- All data comes from existing database tables
- Just need to write SELECT COUNT(*) and SELECT SUM() queries
- No new database tables needed

**Database Changes:**
- No schema changes needed
- All features use existing tables

---

## Risks & Mitigations

**Risk:** 15 points in 2 days is our highest daily velocity
**Mitigation:** Team is experienced, features are smaller enhancements not full new features

**Risk:** Email sending might not work if SMTP setup fails
**Mitigation:** Test SMTP connection first thing on Day 1. If it fails, we can simulate emails (just save to database)

**Risk:** PDF library might be hard to use
**Mitigation:** Simple table format only. If too complex, we can just focus on CSV

**Risk:** Not enough time for testing
**Mitigation:** Gita tests features as soon as they're ready, not waiting until end

---

## Success Criteria

Sprint 4 is successful if:
- ✅ Admins can export attendees as both CSV and PDF (enhancement complete)
- ✅ Reports page shows accurate statistics
- ✅ Users receive email after registration
- ✅ Users receive email after payment
- ✅ All features tested and working
- ✅ No critical bugs
- ✅ Product Owner accepts all features

---

## Notes on Sprint 4

This sprint is shorter but focused. We're not building entirely new features - we're improving what we already have:

- Export feature exists from Sprint 3, we're adding PDF and improving CSV
- Email notifications use existing registration/payment flows, we're just adding email triggers
- Reports use existing data, we're just querying and displaying it

These are "polish" features that make the portal feel more complete and professional. They're important for user experience but not as complex as payment integration or admin CRUD operations.

The goal is to wrap up the project with useful features that add real value without taking too much time.

---

**Prepared by:** Surya Yousufzai (Scrum Master)  
**Approved by:** Marwa Paiman (Product Owner)  
**Date:** December 1, 2025
