# Test Results – Sprint 1

**Project:** University Event Registration Portal  
**Tester:** Gita Rahmany (QA & DevOps Engineer)  
**Sprint:** Sprint 1 (Nov 15–22, 2025)  
**Testing Period:** Nov 19–21, 2025  
**Environment:** Local development server

---

## Test Summary

| Metric | Value |
|--------|-------|
| Total Test Cases | 10 |
| Passed | 9 |
| Failed | 1 |
| Pass Rate | 90% |
| Critical Bugs | 0 |
| Major Bugs | 1 |
| Minor Bugs | 0 |

---

## Test Execution Details

### TC-001: User Registration with Valid Information
**Status:** ✅ PASSED  
**Date:** Nov 19, 2025

**Summary:** Registration worked perfectly with valid inputs. The system created the account and displayed a confirmation message. Email verification was also sent successfully.

---

### TC-002: User Login with Correct Credentials
**Status:** ✅ PASSED  
**Date:** Nov 19, 2025

**Summary:** Login worked as expected. The user was redirected to the dashboard, and a JWT token was correctly stored in `localStorage`.

---

### TC-003: User Login with Incorrect Credentials
**Status:** ✅ PASSED  
**Date:** Nov 19, 2025

**Summary:** The system correctly rejected invalid credentials and displayed the appropriate error message.

---

### TC-004: Register with Duplicate Email
**Status:** ❌ FAILED  
**Date:** Nov 19, 2025

**Issue:** When trying to register with an email already in use, the system crashed with a server error (500) instead of showing a proper message.

**Bug ID:** BUG-001  
**Severity:** Major  
**Fix Status:** Resolved on Nov 20

**Retest Result:** ✅ PASSED

---

### TC-005: Browse Events Page
**Status:** ✅ PASSED  
**Date:** Nov 20, 2025

**Summary:** The events page displayed all event data properly. Loading time was fast (under 1 second).

---

### TC-006: Search Events by Keyword
**Status:** ✅ PASSED  
**Date:** Nov 20, 2025

**Summary:** The search function worked as expected and returned only events matching the keyword “Tech.”

---

### TC-007: Filter Events by Category
**Status:** ✅ PASSED  
**Date:** Nov 20, 2025

**Summary:** Filtering by category worked correctly and returned only workshop-related events.

---

### TC-008: Password Validation
**Status:** ✅ PASSED  
**Date:** Nov 20, 2025

**Summary:** The system correctly blocked weak passwords and showed the appropriate error message.

---

### TC-009: Email Format Validation
**Status:** ✅ PASSED  
**Date:** Nov 20, 2025

**Summary:** Invalid email formats were detected, and error messages were shown properly.

---

### TC-010: Responsive Design Test
**Status:** ✅ PASSED  
**Date:** Nov 21, 2025

**Summary:** The layout adapted well across mobile, tablet, and desktop views. The mobile menu also worked smoothly.

---

## Bugs Found

### BUG-001: Duplicate Email Registration Issue
**Severity:** Major  
**Priority:** High  
**Status:** Fixed  
**Found:** Nov 19  
**Fixed:** Nov 20  
**Tested by:** Gita Rahmany  
**Fixed by:** Fariba Mohammadi

**Description:**  
Registering with an existing email caused a server error instead of a user-friendly message.

**Fix:**  
A validation check was added to catch duplicate emails and return a clear message.

**Retest:** Passed.

---

## API Testing (Postman)

### Registration API — POST /api/register  
**Status:** ✅ PASSED

The API successfully created a user with valid input and returned the correct response.

---

### Login API — POST /api/login  
**Status:** ✅ PASSED

Login worked correctly and returned a valid token and user data.

---

### Events API — GET /api/events  
**Status:** ✅ PASSED

The API returned a list of 10 events with no issues.

---

## Performance Testing

| Page | Load Time | Status |
|------|-----------|--------|
| Home | 0.8s | ✅ |
| Login | 0.6s | ✅ |
| Registration | 0.7s | ✅ |
| Events List | 1.2s | ✅ |

All pages loaded well under the target of 2 seconds.

---

## Security Testing

All major security checks passed:

- HTTPS enforced  
- Passwords hashed  
- SQL injection blocked  
- XSS inputs sanitized  
- JWT expiration working properly  

---

## Browser Compatibility

| Browser | Version | Status |
|---------|---------|--------|
| Chrome | 119 | ✅ |
| Firefox | 120 | ✅ |
| Edge | 119 | ✅ |
| Safari | 17 | ✅ |

---

## Recommendations for Sprint 2

- Add loading indicators for better UX  
- Improve error logging  
- Strengthen frontend input validation  
- Add a password strength meter  
- Implement proper “Remember Me” functionality  

---

## Test Coverage

- **Functional Testing:** 90%  
- **API Coverage:** 100% for Sprint 1 endpoints  
- **UI Testing:** 85%  
- **Security:** Basic coverage completed  

---

## Conclusion

Sprint 1 testing went well with a 90% pass rate. Only one major issue was found, and it was quickly resolved. Core functionality like registration, login, and event browsing is stable and ready for Sprint Review.

**Overall Quality:** Good  
**Ready for Review:** Yes ✅

