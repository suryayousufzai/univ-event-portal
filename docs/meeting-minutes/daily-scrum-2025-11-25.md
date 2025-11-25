## Daily Scrum Meeting Meetings – Sprint 2, Day 3
**Project:** University Event Registration Portal  
**Meeting Type:** Daily Scrum #3  
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
To share progress from Day 2 of Sprint 2, review completed work, and plan the next steps for payment integration, ticket generation, and testing.

---

## Meeting Summary

**Surya (Scrum Master):**  
Welcomed the team to Day 3 of Sprint 2.  
Reviewed yesterday’s accomplishments and encouraged updates from each team member.  

---

**Fariba (Backend Lead Developer):**  
Completed the Payment API (POST `/api/payments`):  
- Receives payment information (card number, expiration, CVV, amount, registration ID)  
- Simulated sandbox payment processing  
- Updates registration status from "pending" to "paid" on success  
- Creates payment record in database  
- Added error handling for invalid card, expired card, insufficient funds  
- Tested successfully in Postman  

Plans for today: Build **Ticket Generation feature** (GET `/api/tickets/{registrationId}`) and simulate sending confirmation email.  
No blockers.

---

**Muneera (Frontend Lead Developer):**  
Completed integration of Event Details page with Registration API.  
- Loading spinner during API call  
- Success message on successful registration  
- Error messages for full events or failures  

Built Payment Page for paid events:  
- Fields: card number, expiration, CVV, cardholder name  
- Validations: 16-digit card, valid expiry, 3-digit CVV  
- Styled professionally with secure appearance  

Plans for today: Connect Payment Page to Payment API, add loading states and success/error messages, redirect after payment, start "My Events" page.  
No blockers.

---

**Gita (QA & DevOps Engineer):**  
Tested Registration API:  
- TC-011 (free event) → PASSED  
- TC-013 (event full) → PASSED  

Tested frontend integration: successful registration workflow works with loading spinner and success message.  

Plans for today: Test Payment API (TC-012, TC-014) and document results.  
No blockers.

---

**Marwa (Product Owner):**  
Performed manual testing of registration flows for free and paid events.  
Reviewed Event Details and Payment Page; looks professional and smooth.  

Plans for today: Test complete flow including payment and review ticket generation.  
No blockers.

---

## General Discussion
- Day 3 progress: Payment API done, Registration API done, Event Details page complete, frontend integration complete, Payment Page built  
- Today’s focus: Payment integration (Muneera), Ticket generation (Fariba), Payment testing (Gita)  
- Day 4 plans: Final testing, bug fixes, documentation, Sprint Review preparation  
- Team confirmed no blockers or concerns  

---

## Key Decisions
- Ticket generation feature to be completed today  
- Payment integration to be completed today  
- Testing continues on Payment API and registration flows  

---

## Blockers
- None reported.

---

## Next Meeting
**Date:** November 26, 2025  
**Topic:** Daily Scrum #4 – Final Testing & Sprint Review Preparation  
**Facilitator:** Surya (Scrum Master)

---

**Recording Link:** (https://drive.google.com/file/d/1uXpFe6_OOfNZxja3vTAernvw5Ek0-1uN/view?usp=drive_link)

---

**Document Prepared by:** Surya Yousufzai (Scrum Master)  
**Reviewed by:** Marwa Paiman (Product Owner)
