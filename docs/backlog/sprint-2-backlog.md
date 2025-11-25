# Sprint 2 Backlog

**Project:** University Event Registration Portal  
**Sprint:** Sprint 2  
**Duration:** November 23-26, 2025 (4 days)  
**Sprint Goal:** Enable users to register for events and make payments

---

## Sprint Backlog Items

| ID | User Story | Story Points | Status | Assigned To |
|----|------------|--------------|--------|-------------|
| US-007 | Register for Event | 8 | In Progress | Fariba + Muneera + Gita |
| US-008 | Payment Integration | 8 | Not Started | Fariba + Muneera + Gita |
| US-009 | Ticket Generation | 3 | Not Started | Fariba + Muneera |

**Total Story Points:** 19

---

## Task Breakdown

### US-007: Register for Event

**Backend (Fariba):**
- [ ] Create registration API endpoint
- [ ] Validate user authentication
- [ ] Check seat availability
- [ ] Update database (create registration, decrease seats)
- [ ] Return confirmation response

**Frontend (Muneera):**
- [ ] Build Event Details page
- [ ] Add "Register Now" button
- [ ] Create registration confirmation modal
- [ ] Connect to registration API
- [ ] Show success/error messages

**QA (Gita):**
- [ ] Write test cases (TC-011 to TC-014)
- [ ] Test registration API
- [ ] Test frontend flow
- [ ] Document results

### US-008: Payment Integration

**Backend (Fariba):**
- [ ] Create payment API endpoint
- [ ] Integrate payment gateway (sandbox)
- [ ] Validate payment information
- [ ] Update registration status
- [ ] Create payment record

**Frontend (Muneera):**
- [ ] Build payment form page
- [ ] Card number, expiry, CVV inputs
- [ ] Connect to payment API
- [ ] Show payment processing state
- [ ] Handle success/failure

**QA (Gita):**
- [ ] Write payment test cases
- [ ] Test with valid/invalid cards
- [ ] Test error handling
- [ ] Document results

### US-009: Ticket Generation

**Backend (Fariba):**
- [ ] Generate unique ticket code
- [ ] Create ticket API endpoint
- [ ] Simulate email sending

**Frontend (Muneera):**
- [ ] Build ticket display component
- [ ] Add download button
- [ ] Show ticket details

**QA (Gita):**
- [ ] Test ticket generation
- [ ] Verify ticket details

---

## Definition of Done (Sprint 2)
- [ ] All APIs tested and working
- [ ] All UI pages complete and responsive
- [ ] Integration complete (frontend ↔ backend)
- [ ] All test cases passed
- [ ] Code pushed to GitHub
- [ ] Documentation updated
- [ ] Product Owner acceptance

---

**Prepared by:** Marwa Paiman (Product Owner)     
**Date:** November 23, 2025
