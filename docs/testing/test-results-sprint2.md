# Test Results – Sprint 2

**Project:** University Event Registration Portal  
**Tester:** Gita Rahmany (QA & DevOps Engineer)  
**Sprint:** 2 (Nov 23–26, 2025)  
**Environment:** Local development server  

---

## Overall Summary

Sprint 2 went really well. I completed 12 test cases that focused on event registration, payments, cancellations, tickets, and API flows. All test cases passed without any bugs, which was great to see.

| Metric | Value |
|--------|-------|
| Total Test Cases | 12 |
| Passed | 12 |
| Failed | 0 |
| Pass Rate | 100% |
| Critical Bugs | 0 |
| Major Bugs | 0 |
| Minor Bugs | 0 |

## Test Case Breakdown

### TC-011: Register for Free Event – PASSED
*Test Steps:*
1. Login as test user
2. Navigate to Events page
3. Click on "Web Development Workshop" (free event)
4. Click "Register Now" button
5. Confirm registration in modal
   
Registration worked without issues. Seats updated correctly (30 → 29).

### TC-012: Register for Paid Event – PASSED
*Test Steps:*
1. Login as test user
2. Navigate to Events page
3. Click on "Tech Conference 2025" (paid event, $50)
4. Click "Register Now"
5. Confirm registration
6. Redirected to payment page
   
User was redirected to the payment page with the correct amount shown.

### TC-013: Register for Full Event – PASSED
*Test Steps:*
1. Manually set event available_seats to 0 in database
2. Try to register for that event
3. Click "Register Now"
   
System showed the correct “Event is full” message. Good validation.

### TC-014: Register Without Login – PASSED
*Test Steps:*
1. Logout from system
2. Navigate to Event Details page directly
3. Try to click "Register Now"
   
Non-logged-in users were redirected to login. Secure behavior.

### TC-015: Payment with Valid Card – PASSED
1. Register for paid event ($50)
2. Enter payment details:
   - Card: 4111 1111 1111 1111 (test card)
   - Expiry: 12/26
   - CVV: 123
   - Name: Test User
3. Click "Process Payment"
   
Test card worked. Payment processed, and status changed to “paid.”

### TC-016: Invalid Card – PASSED
*Test Steps:*
1. Register for paid event
2. Enter invalid card number: 1234 5678 9012 3456
3. Try to submit payment
   
The system detected the invalid card number immediately.

### TC-017: Expired Card – PASSED
*Test Steps:*
1. Register for paid event
2. Enter expired date: 12/23 (expired)
3. Try to submit payment
   
Expired dates were correctly flagged.

### TC-018: Payment Declined – PASSED
*Test Steps:*
1. Register for paid event
2. Use test card that simulates decline: 4000 0000 0000 0002
3. Submit payment
   
Declined card was handled correctly, and status stayed “pending.”
*Notes:* Failed payments don't break the system!

### TC-019: Download Ticket – PASSED
*Test Steps:*
1. Complete registration and payment
2. Navigate to "My Events" page
3. Click "Download Ticket" button
   
Ticket generated with proper event details and code.

### TC-020: Cancel Free Event Registration – PASSED
*Test Steps:*
1. Register for free event
2. Go to "My Events"
3. Click "Cancel Registration"
4. Confirm cancellation
   
Cancellation worked, and seat count updated properly.

### TC-021: Cancel Paid Registration + Refund – PASSED
*Test Steps:*
1. Register and pay for event ($50)
2. Cancel registration
3. Confirm cancellation
   
Refund simulated correctly. Message was clear.

### TC-022: View My Events – PASSED
*Test Steps:*
1. Login as user who registered for 3 events
2. Navigate to "My Events" page
   
All events and details displayed correctly.

---

# API Testing (Postman)

Below are the API tests performed using Postman. All responses, payloads, and statuses are preserved and slightly restructured for readability.

---

## **Registration API**

**Endpoint:**  
`POST /api/events/:id/register`

### **Test 1: Valid Registration**
**Request Body:**
```json
{
  "userId": 6,
  "eventId": 3
}
```

**Response (200 OK):**
```json
{
  "success": true,
  "message": "Registration successful",
  "registrationId": 15,
  "ticketCode": "TICKET-ABC123"
}
```
**Status:** PASSED 

---

### **Test 2: Already Registered**
**Response (409 Conflict):**
```json
{
  "success": false,
  "error": "You are already registered for this event"
}
```
**Status:** PASSED 

---

### **Test 3: Event Full**
**Response (400 Bad Request):**
```json
{
  "success": false,
  "error": "Event is full"
}
```
**Status:** PASSED 

---

## **Payment API**

**Endpoint:**  
`POST /api/payments`

### **Test 1: Valid Payment**

**Request Body:**
```json
{
  "registrationId": 15,
  "amount": 50.00,
  "cardNumber": "4111111111111111",
  "expiryDate": "12/26",
  "cvv": "123",
  "cardholderName": "Test User"
}
```

**Response (200 OK):**
```json
{
  "success": true,
  "transactionId": "TXN-789456",
  "amount": 50.00,
  "paymentDate": "2025-11-25T14:30:00Z"
}
```
**Status:** PASSED 

---

### **Test 2: Invalid Card**

**Response (400 Bad Request):**
```json
{
  "success": false,
  "error": "Invalid card number"
}
```
**Status:** PASSED 

---

## **Get User Registrations API**

**Endpoint:**  
`GET /api/users/:userId/registrations`

**Response (200 OK):**
```json
[
  { "eventId": 3, "status": "paid", "ticketCode": "TICKET-ABC123" },
  { "eventId": 5, "status": "confirmed", "ticketCode": "TICKET-XYZ111" }
]
```
**Status:** PASSED 

---

## **Cancel Registration API**

**Endpoint:**  
`DELETE /api/registrations/:id`

**Response (200 OK):**
```json
{
  "success": true,
  "message": "Registration cancelled successfully",
  "refundAmount": 50.00
}
```
**Status:** PASSED 

---

# Performance Testing

## **Page Load Times**
| Page | Load Time | Result |
|------|-----------|---------|
| Event Details | 0.8s | PASS |
| Payment Form | 1.0s | PASS |
| My Events | 1.3s | PASS |

**Target:** < 2 seconds  
All pages loaded within acceptable limits.

---

## **API Response Times**
| Endpoint | Avg Response | Result |
|----------|--------------|--------|
| POST /api/events/:id/register | 320ms | PASS |
| POST /api/payments | 450ms | PASS |
| GET /api/users/:id/registrations | 280ms | PASS |
| DELETE /api/registrations/:id | 310ms | PASS |

**Target:** < 1 second  
All APIs responded efficiently.

---

# Security Testing

Security checks included:

- JWT required for protected operations  
- Users cannot register on behalf of others  
- No plaintext storage of payment data  
- CVV never stored  
- SQL injection attempts blocked  
- XSS content sanitized  
- CSRF protections implemented  

All tests passed.

---

# Compatibility Testing

| Browser | Version | Status |
|---------|----------|--------|
| Chrome | 119 | PASS |
| Firefox | 120 | PASS |
| Edge | 119 | PASS |
| Safari | 17 | PASS|

---

# Responsive Design Testing

- Mobile (375px) – PASS  
- Tablet (768px) – PASS  
- Desktop (1920px) – PASS  

---

# Bugs Found

None detected this sprint 
System is stable and functioning as expected.

---

# Conclusion

Sprint 2 delivered a full set of working features with perfect test results.  
All functionalities, including registration, payment, cancellation, and ticket generation, performed correctly and reliably.

**Prepared by:** Gita Rahmany  
**Date:** Nov 26, 2025  

