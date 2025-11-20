# Daily Scrum Meeting – November 18, 2025  
**Sprint 1 — Day 3**

**Project:** University Event Registration Portal  
**Meeting Type:** Daily Scrum  
**Duration:** ~14 minutes  
**Platform:** Zoom / Recorded

---

## Attendees
- **Surya** — Scrum Master  
- **Marwa** — Product Owner  
- **Fariba** — Backend Lead  
- **Muneera** — Frontend Lead  
- **Gita** — QA & DevOps  

---

## Meeting Summary
Surya opened the meeting and welcomed everyone. This is Day 3 of Sprint 1, and the team is making strong progress. No blockers were reported.

---

## Team Updates

### **Fariba – Backend**
**Yesterday**
- Finished all 4 database tables (users, events, registrations, payments)
- Completed Registration API (`POST /api/register`)
  - Includes email validation, password hashing (bcrypt), and returns user ID
- Successfully tested in Postman
- Code pushed to `feature/registration-api`

**Today**
- Start working on Login API (`POST /api/login`)
- Add JWT token generation
- Add clear error messages for failed login attempts
- Begin planning Events List API

**Blockers:** None

---

### **Muneera – Frontend**
**Yesterday**
- Completed Login Page UI
- Added validation, error messages, responsive layout
- Added “Forgot Password” (placeholder) and “Sign Up” link
- Pushed to `feature/login-ui`

**Today**
- Start building Registration Page UI
  - Fields: name, email, password, confirm password, student ID (optional)
  - Add validation + password strength indicator
  - Show success message and redirect to login
  - Style using Tailwind and ensure full responsiveness

**Blockers:** None

---

### **Gita – QA & DevOps**
**Yesterday**
- Completed test cases TC-001 to TC-010
- Prepared Postman collection
- Created bug report template
- Finalized test data sheet

**Today**
- Start testing the Registration API
- Test scenarios:
  - Valid registration
  - Duplicate email
  - Invalid email format
  - Weak password
  - Missing fields
- Document results and report bugs

**Blockers:** None

---

### **Marwa – Product Owner**
- Very happy with the team's progress
- Reviewed Registration API — meets all acceptance criteria
- Login UI looks accurate and matches Figma design
- No changes needed for the backlog
- Will manually test registration flow today

**Blockers:** None

---

### **Surya – Scrum Master**
**Yesterday**
- Updated sprint board and burndown chart

**Today**
- Coordinate frontend–backend integration plan
- Prepare mid-sprint documentation

**Blockers:** None

---

## Sprint Progress (Day 3)

### **User Story Status**
- **US-001: Registration:** ~70% complete  
- **US-002: Login:** ~50% complete  
- **US-004: Browse Events:** ~20% complete  
- **NFR-001: Security:** ~60% complete  

### **Milestones Completed**
- Database finished  
- Registration API done  
- Login UI done  
- Test cases prepared  

### **In Progress**
- Login API (Backend)  
- Registration Page UI (Frontend)  
- Registration API Testing (QA)  

---

## Discussion Highlights
- Gita confirmed Registration API is ready to test.  
- Endpoint: `POST http://localhost:5000/api/register`  
- Registration form password fields will be stacked vertically (per Figma).  
- Team is ahead of schedule and collaboration is smooth.

---

## Blockers
None reported.

---

## Action Items

| Task | Owner | Due |
|------|--------|------|
| Share Postman collection | Fariba | Today (AM) |
| Build Login API | Fariba | Today |
| Build Registration Page UI | Muneera | Today |
| Test Registration API | Gita | Today–Tomorrow |

---

## Next Meeting
**Daily Scrum – November 19, 2025 at 10:00 AM**

---

## Recording  
Google Drive link: *(https://drive.google.com/file/d/1-puxkt0_ko3nHIJS3Hb5hcLvowLG2zhZ/view?usp=sharing)*

---

**Prepared by:** Surya (Scrum Master)  
**Date:** November 18, 2025
