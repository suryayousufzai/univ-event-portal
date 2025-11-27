# Product Owner – Sprint 2 Summary Report

**Product Owner:** Marwa Paiman  
**Project:** University Event Registration Portal  
**Sprint:** Sprint 2 (Nov 23–26, 2025)  
**Report Date:** November 26, 2025

---

## 1. Sprint Goal Completion

**Sprint 2 Goal:**  
Allow users to register for university events and make payments.

**Result:** Goal fully met.

By the end of this sprint, the system now supports:
- Registration for both free and paid events  
- Secure payment processing  
- Viewing all registered events  
- Downloading tickets  
- Cancelling registrations and issuing refunds  

---

## 2. User Stories Delivered

| ID | User Story | Points | Status | Notes |
|----|------------|--------|--------|--------|
| US-007 | Event Registration | 8 | Completed | All criteria satisfied |
| US-008 | Payment Integration | 8 | Completed | Sandbox payments working properly |
| US-009 | Ticket Generation | 3 | Completed | Basic ticket format ready |

**Total:** 19 / 19 story points delivered

---

## 3. Acceptance Review

### US-007: Event Registration
**Criteria checked:**
- Registration button functional  
- Seat availability validated  
- Registration stored in DB  
- Seat count updates correctly  
- Clear success message shown  
- Prevents duplicate registration  
- Prevents registration if event is full  

**Decision:** Accepted  
**Notes:** User flow is straightforward and gives clear feedback. Error handling is well implemented.

---

### US-008: Payment Integration
**Criteria checked:**
- Payment form operational  
- Card information validation  
- Sandbox processing successful  
- Status updates to “paid”  
- Transaction ID created  
- Proper handling of failed payments  

**Decision:** Accepted  
**Notes:** The payment screen looks reliable and secure. Validation works well, and the sandbox integration behaves as expected.

---

### US-009: Ticket Generation
**Criteria checked:**
- Unique code generated  
- Ticket shows event/user information  
- Downloading works  
- Email confirmation simulated correctly  

**Decision:** Accepted  
**Notes:** Ticket output is clean and meets the agreed-upon scope for this sprint.

---

## 4. Value Delivered This Sprint

### End-User Benefits
From Sprint 1 users could browse, search, and log in.  
Now, they can also:
- Register for events  
- Pay for events  
- Access their event list  
- Download tickets  
- Cancel and receive refunds  

### Business Benefits
- Ability to collect event fees  
- Reduced manual handling of ticketing  
- Automated refund system  
- Improved professionalism and trust in the platform  

This sprint enabled the core operational functionality of the entire system.

---

## 5. Sprint Metrics

| Metric | Target | Result |
|--------|--------|--------|
| Story Points Planned | 19 | 19 |
| Story Points Completed | 19 | 19 |
| User Stories Completed | 3 | 3 |
| Bugs Reported | 0 | 0 |
| Sprint Goal Achieved | Yes | Yes |
| Duration | 4 days | On schedule |

---

## 6. Quality Evaluation

**Code Quality:**  
Backend and frontend code follow good structure, validations work as expected, and payment logic is solid.

**Testing:**  
All functional and non-functional tests passed. No defects reported.

**User Experience:**  
Registration and payment flows are simple and logical. “My Events” provides essential information clearly.

**Performance:**  
Pages load quickly and API calls are responsive.

---

## 7. Risks and Issues

No major issues occurred during the sprint.  
Potential risks (payment complexity, short timeline) were managed successfully.

---

## 8. Feedback Highlights

Feedback from testing indicated:
- Payment flow feels reliable  
- Event registration is simple  
- Ticket look and information are clear  
- Refund process is fast  

Suggestions for the future:
- Add QR codes to tickets  
- Send reminder emails before events  
- Consider calendar integration  

---

## 9. Product Vision Alignment

The project vision is to build a convenient way for students and staff to find, join, and manage events.

This sprint delivered key components of that vision:
- Registration  
- Payments  
- Access to tickets  
- Event management for users  

All work completed aligns strongly with long-term product goals.

---

## 10. Sprint 3 Recommendations

### Focus Areas
1. Admin dashboard  
2. Creating and editing events  
3. Viewing registered attendees  

Expected team capacity: **around 23 story points**

**Proposed Sprint 3 Goal:**  
Enable administrators to manage and monitor events.

---

## 11. Team Performance

The team worked very efficiently:
- All planned work completed  
- No defects  
- Good communication  
- Fast integration and testing  

Velocity is improving:
- Sprint 1: 16 points  
- Sprint 2: 19 points  

Projected for Sprint 3: 20–23 points

---

## 12. Product Owner Decisions

### Approved for release:
- Event registration  
- Payments (sandbox)  
- Ticket generation  
- My Events page  
- Cancellations and refunds  

### Prepared for next sprint:
- Admin-focused user stories  
- Updated acceptance criteria  
- Backlog refined and prioritized  

---

## 13. Business Notes

The system now supports financial operations:
- Accepting payments  
- Recording transactions  
- Managing refunds  

This lays the foundation for real revenue once a live payment gateway is connected.

---

## 14. Sprint Comparison

| Category | Sprint 1 | Sprint 2 |
|----------|----------|----------|
| Story Points | 16 | 19 |
| Duration | 7 days | 4 days |
| Complexity | Lower | Higher |
| Bugs | 1 | 0 |
| Completion | 100% | 100% |

Despite the increased complexity, the team matched all expectations.

---

## 15. PO Approval

After reviewing all deliverables, I confirm:
- All user stories meet their requirements  
- The sprint goal is fully completed  
- The delivered features provide strong value  
- Quality is high  
- The team can move forward to Sprint 3  

**Sprint 2 is formally approved and closed.**

**Signed:**  
Marwa Paiman  
Product Owner  
November 26, 2025

