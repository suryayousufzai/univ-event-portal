# University Event Registration Portal – Test Plan

## 1. Objective

The purpose of this test plan is to ensure that all features of the University Event Registration Portal work correctly, smoothly, and securely. The testing is based on the Product Backlog and User Stories. This test plan confirms stability, data protection, correct system behavior, and good user experience for both frontend and backend.

## 2. Testing Types

### 2.1 Integration Testing
* Ensures that the frontend and backend work together correctly (API requests, data flow, responses).

### 2.2 Unit Testing
Tests individual components such as:
* Login function  
* Registration function  
* Buttons, forms, validation  
* API endpoints  

### 2.3 Functional Testing
Verifies that every feature works as expected, including:
* Login  
* Registration  
* Event browsing  
* Event creation (Admin)  
* Payments  
* Cancellations  

### 2.4 Security Testing
Ensures:
* HTTPS enforced  
* Passwords stored securely  
* Role-based access control (admin vs user)  
* No unauthorized access allowed  
* Input validation to prevent attacks  

### 2.5 Usability Testing
Confirms:
* Interface is simple and easy to use  
* Pages are responsive  
* Buttons, forms, and messages are clear  

### 2.6 Regression Testing
After every sprint:
* All old features are re-tested  
* New changes do not break previous functionality  

### 2.7 Performance / Load Testing
Tests that the system:
* Handles up to 100 users at the same time  
* Does not slow down or crash  

## 3. Test Scenarios

| Test Case ID | Scenario | Expected Result |
|--------------|----------|-----------------|
| TC-001 | User registers with valid information | Account created and confirmation email sent |
| TC-002 | User logs in with correct credentials | User is redirected to dashboard |
| TC-003 | User logs in with incorrect credentials | Error message displayed |
| TC-004 | Admin creates a new event | Event is visible in event list |
| TC-005 | User registers and pays for an event | Registration stored, payment confirmed, ticket sent |
| TC-006 | User cancels a registration | Seat released, cancellation email sent, refund processed |
| TC-007 | System under high load (100 users) | System remains stable and responsive |
| TC-008 | Unauthorized user tries to access admin pages | Access denied |
| TC-009 | Payment fails due to invalid card | Error message shown, no ticket generated |
| TC-010 | User updates their profile | Details updated and saved |

## 4. Tools Used

* GitHub – Version control, CI/CD, documentation  
* Postman – API testing  
* Manual Testing – UI, behavior, and usability checks  

---

**Prepared By:** Gita Rahmany – QA & DevOps Engineer  
**Date:** November 14, 2025
