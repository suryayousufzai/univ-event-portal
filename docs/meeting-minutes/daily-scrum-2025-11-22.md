# Sprint Review Meeting – Sprint 1  
**Project:** University Event Registration Portal  
**Meeting Type:** Sprint 1 Review  
**Date:** November 22, 2025  
**Duration:** 21 minutes  
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

This was our Sprint 1 Review, basically the big demo day where we showcased everything developed during the past 7 days. The goal was to:
- Demonstrate completed features  
- Gather feedback  
- Get Product Owner acceptance  
- Officially close Sprint 1  

---

## Meeting Summary

### Opening – by Surya (Scrum Master)
- Welcomed everyone and highlighted that November 22 is the final day of Sprint 1.
- Recalled the Sprint Goal:  
  “Deliver the core user access system and event browsing features.”
- Covered agenda:
  1. Sprint goal review  
  2. Feature demonstration  
  3. Product Owner acceptance  
  4. Metrics & next steps  
- Sprint duration: Nov 15–22 (7 days)  
- Committed 16 story points over 4 user stories  
- Handed over to Fariba for backend demo  

---

### Backend Demo – by Fariba (Backend Lead Developer)

Despite not having her laptop, Fariba explained everything verbally while Surya handled the demo screen.

#### Database Overview
- Database: `university_events_db`
- Tables:
  - `users` – contains 5 test users  
  - `events` – 10 sample events  
  - `registrations` – ready (Sprint 2)  
  - `payments` – ready (Sprint 2)  
- Clean structure, proper foreign keys, good normalization

#### API Demonstrations

| Endpoint | Demo Highlights |
|----------|----------------|
| `POST /api/register` | Created new user “Demo User” (ID 6), password hashed, duplicate email detected correctly |
| `POST /api/login` | JWT token generated (valid 24h), invalid credentials handled |
| `GET /api/events` | All 10 events displayed, category filtering and keyword search showcased |

Fariba mentioned APIs are fully working, tested, and documented.

---

### Frontend Demo – by Muneera (Frontend Lead Developer)

Live walkthrough of the website:

#### Registration Page
- Clean UI with fields: name, email, password, confirm password, student ID
- Password strength indicator (red to green)
- Success message – auto redirect to login page

#### Login Page
- Successfully logged in using the registered account  
- Smooth loading – redirected to Events page

#### Events Page
- Grid of 10 event cards showing title, date, location, price  
- “Free” events marked clearly  
- Real-time search (“tech”) and category filter working  
- Fully responsive:
  - Desktop → 3 per row  
  - Tablet → 2 per row  
  - Mobile → 1 per row  

Muneera emphasized full responsiveness and great UI performance.

---

### Testing Report – by Gita (QA & DevOps Engineer)

Summary:
- 10 test cases executed – 10 passed (100% success rate)

| Test Case | Result |
|-----------|--------|
| Registration (valid) | PASSED |
| Login (correct and incorrect) | PASSED |
| Duplicate email | FAILED initially → FIXED → PASSED |
| Browse, search, filter events | PASSED |
| Password validation, responsive design | PASSED |

#### Bug Report
| Bug ID | Issue | Status |
|--------|--------|--------|
| BUG-001 | Duplicate email caused 500 error | FIXED (Nov 19) |

Performance:
- All pages load under 2 seconds  

Security:
- bcrypt, JWT, input validation – all passed  

Browsers tested:
- Chrome, Firefox, Edge, Safari – no issues  

---

### Product Owner Acceptance – by Marwa

| User Story | Status |
|------------|--------|
| US-001: Registration | Accepted |
| US-002: Login | Accepted |
| US-004: Browse Events | Accepted |
| NFR-001: Security | Accepted |

Final Decision:  
All Sprint 1 deliverables accepted. Sprint 1 officially complete with 100% success.  

Marwa praised the team for excellent collaboration, quality, and fast resolution of issues.

---

### Sprint Metrics – by Surya (Scrum Master)

| Metric | Value |
|--------|-------|
| Story Points Planned | 16 |
| Story Points Completed | 16 |
| Completion Rate | 100% |
| Bugs Found | 1 |
| Bugs Resolved | 1 |
| Test Pass Rate | 100% |
| Sprint Goal | Achieved |

Delivered:
- Secure user registration
- Login with JWT
- Event browsing with search and filter
- Fully working UI and backend
- Database completed
- API documentation and test coverage

Sprint 2 Preview:
Event registration, payment integration, ticket generation and email confirmations.  
Start date: Nov 23, 2025

---

### Closing Remarks

| Team Member | Final Thoughts |
|-------------|----------------|
| Fariba | Great sprint, enjoyed teamwork |
| Muneera | Team was highly supportive |
| Gita | Proud of quality and results |
| Marwa | Excellent teamwork, this is how Scrum should work |
| Surya | Thanked everyone, declared Sprint 1 complete |

Retrospective:
- Formal retrospective at 4 PM was cancelled due to Afghanistan situation
- Instead, team had an informal chat covering feedback and improvements  
- Still productive and meaningful

Everyone congratulated each other.

---

## Key Decisions

- Sprint 1 completed and fully accepted
- Sprint 2 starts November 23, 2025
- Formal retrospective cancelled, replaced with informal discussion
- Focus for Sprint 2 – Event registration and payment integration

---

## Challenges

| Challenge | Resolution |
|-----------|------------|
| Fariba didn’t have laptop during demo | Surya shared screen |
| Duplicate email bug | Fixed before review |
| Retrospective cancellation | Conducted informal discussion |

---

## Retrospective Note

Formal meeting was cancelled due to external circumstances in Afghanistan. Instead, we held a light informal chat session, still covering all main retrospective points.

---

Recording Link: https://drive.google.com/file/d/1KX4PdCD0QyxyoedgOEEhrkSjvRiNrg-t/view?usp=drive_link

Document Prepared By: **Surya Yousufzai** (Scrum Master)  
Date Completed: **November 22, 2025**
