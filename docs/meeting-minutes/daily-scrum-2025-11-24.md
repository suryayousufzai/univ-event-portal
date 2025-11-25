# Daily Scrum Meeting Meetings – Sprint 2, Day 2
**Project:** University Event Registration Portal  
**Duration:** 11 minutes  
**Platform:** Zoom 

---

## Attendees
| Role | Name |
|------|------|
| Scrum Master | **Surya Yousufzai** |
| Product Owner | **Marwa Paiman** |
| Backend Lead Developer | **Fariba Mohammadi** |
| Frontend Lead Developer | **Muneera Aman** |
| QA & DevOps Engineer | **Gita Rahmany** |

---

## Meeting Purpose
To share progress from Day 1 of Sprint 2, review completed work, and plan the next steps for event registration, API integration, and testing.

---

## Meeting Summary

**Surya (Scrum Master):**  
Welcomed the team to Day 2 of Sprint 2.  
Reviewed the goals: Registration API, Event Details page, and testing.  
Encouraged the team to share yesterday’s accomplishments.

---

**Fariba (Backend Lead Developer):**  
Completed the Event Registration API (POST `/api/events/{eventId}/register`).  
- Checks JWT token for login  
- Checks seat availability  
- Creates registration record in DB  
- Updates available seats  
- Returns success message with registration ID  

Tested various scenarios in Postman including free events, seat availability, and duplicate registrations.  
Plans for today: Build the Payment API (POST `/api/payments`) with sandbox payment gateway integration.  
No blockers.

---

**Muneera (Frontend Lead Developer):**  
Completed Event Details page.  
- Shows event image, title, description, date, location, price, and available seats  
- Added "Register Now" button with confirmation modal  
- Modal confirms registration with Yes/Cancel buttons  

Plans for today: Integrate frontend with Fariba’s Registration API, add loading spinner, display success message, and start designing payment page.  
No blockers.

---

**Gita (QA & DevOps Engineer):**  
Prepared test cases for event registration:  
- TC-011: Register for free event  
- TC-012: Register for paid event  
- TC-013: Register when event is full  
- TC-014: Register without login  

Prepared Postman collection with sample requests.  
Plans to execute TC-011 and TC-013 today.  
No blockers.

---

**Marwa (Product Owner):**  
Reviewed Event Details page and Registration API documentation.  
Will perform manual testing of registration flows today.  
Available for team questions.  
No blockers.

---

## General Discussion
- Muneera asked if the API returns registration ID after success → Fariba confirmed yes.  
- Surya summarized progress: Registration API and Event Details page complete; today’s focus on integration, Payment API, and testing.  
- Team confirmed no other blockers.

---

## Key Decisions
- Registration API verified and ready for testing  
- Event Details page complete, integration starts today  
- Payment API development begins today  

---

## Blockers
- None reported.

---

## Next Meeting
**Date:** November 25, 2025  
**Topic:** Daily Scrum #3 – Integration and Payment API Progress  
**Facilitator:** Surya (Scrum Master)

---

**Recording Link:** (https://drive.google.com/file/d/1pZl93Cjyx7SssWJmb6uA2h212fCGpQuW/view?usp=drive_link)

---

**Document Prepared by:** Surya Yousufzai (Scrum Master)  
**Reviewed by:** Marwa Paiman (Product Owner)
