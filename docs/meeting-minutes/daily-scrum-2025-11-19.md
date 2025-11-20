# Daily Scrum Meeting - November 19, 2025

**Sprint:** Sprint 1 (Day 4 of 7)  
**Date:** Thursday, November 19, 2025  
**Time:** 10:00 AM – 10:15 AM  
**Location:** Zoom  
**Weather:** ☀️ Felt like a productive day

---

## Attendees
- **Surya Yousufzai** – Scrum Master  
- **Marwa Paiman** – Product Owner  
- **Fariba Mohammadi** – Backend Developer  
- **Muneera Aman** – Frontend Developer  
- **Gita Rahmany** – QA & DevOps  

Everyone joined on time. Good mood all around.

---

## Team Mood
Energy was high today. Everyone had solid updates, and the first real bug showed up—meaning QA is fully in action now. Collaboration is going smoothly.

---

## Surya’s Opening
I kicked things off with a quick recap of yesterday and reminded the team we’re already past halfway through Sprint 1. Then I handed it over to Fariba for her updates.

---

## Fariba’s Update (Backend)

### Yesterday
Fariba wrapped up the **Login API**, and everything is working exactly as planned:
- Email + password validation  
- JWT token (24-hour expiry)  
- User details sent back  
- Clear error messages  

She tested everything in Postman and shared it with Gita.  
She also began the **Events List API**, even though it wasn’t required yet — ahead of schedule.

### Today
- Complete **Events List API** (`GET /api/events`)  
- Add category filter + search  
- Possibly add pagination  
- Write documentation  
- Support frontend integration if needed  

### Blockers
None.

---

## Muneera’s Update (Frontend)

### Yesterday
She finished the **Registration Page** with:
- All form fields  
- Validation  
- Password strength indicator  
- Live error messages  
- Redirect after success  
- Clean Tailwind design  
- Responsive layout  
- Matches Figma layout really well  

She also started the Events List page structure.

### Today
- Finish UI for **Events List page**  
  - Cards for events  
  - Image, title, date, location, price  
  - Show “Free” for free events  
- Add search + filter  
- Start backend integration tomorrow  

### Blockers
None.

---

## Gita’s Update (QA & DevOps)

### Yesterday
Gita started running test cases. Her results:

- **TC-001:** Register valid data → Passed  
- **TC-002:** Login valid → Passed  
- **TC-003:** Login wrong password → Passed  
- **TC-004:** Register duplicate email → ❌ Failed  

**BUG-001 Found:**  
- Duplicate email crashes server (500 error)  
- Should show “Email already registered”

Fariba confirmed it’s a quick fix.

### Today
- Retest once bug is fixed  
- Continue with:
  - Email format checks  
  - Password rules  
  - Event browsing  
  - Negative login tests  

### Blockers
Waiting on bug fix (but it’s small).

---

## Marwa’s Update (Product Owner)
Marwa tested the registration and login screens herself and said the UI feels smooth and professional.

She approved the bug report and made one decision today:

- Free events must show **“Free”**, not “$0.00”

She is available for reviews anytime.

---

## Bug Discussion
**BUG-001:** Duplicate email causing server crash.

**Fix Plan by Fariba:**
1. Check if email exists  
2. If yes → return 400 with friendly message  
3. Otherwise insert normally  

Estimated time: ~30 minutes.

No stress, team handled it positively.

---

## Action Items

### **Fariba**
- Fix BUG-001  
- Finish Events List API  
- Update documentation  

### **Gita**
- Retest registration  
- Continue new test cases  

### **Muneera**
- Finish Events List UI  
- Prep for integration  

### **Surya**
- Update sprint board  
- Track bug fix & testing  

### **Marwa**
- Review bug fix later  
- Provide feedback anytime  

---

## Sprint Progress (Day 4)

### **US-001 – Registration**
Backend: 100%  
Frontend: 100%  
Testing: 75%  
**Overall: ~90%**

### **US-002 – Login**
Backend: 100%  
Frontend: 100%  
Testing: In progress  
**Overall: ~85%**

### **US-004 – Browse Events**
Backend: ~40%  
Frontend: ~30%  
**Overall: ~45%**

### **Security**
Most parts done (JWT, validation, hashing)

---

## Decisions
- “Free” should display as **Free**  
- Bug fix prioritized  
- Integration starts tomorrow  

---

## Blockers
Only one small blocker (BUG-001 testing delay).  
**Overall risk: Low**

---

## Highlights
- **Fariba:** MVP today  
- **Muneera:** Clean and consistent UI  
- **Gita:** Found first official bug  
- **Marwa:** Quick approvals  
- **Surya:** Keeping everything aligned  

Team morale: very high

---

## Funny Moment
When Surya said “We might finish early,”  
Muneera instantly said, “Don’t jinx it!”  
Everyone laughed

---

## Links
- **Recording:** **  
- Sprint Board  
- Repository  
- Bug Report  

---

## Next Meeting
**Tursday, Nov 20 – 10:00 AM**

---

## Notes
Recorded by: Surya  
Reviewed by: Marwa  
Approved: Nov 19, 2025

---

## Summary
**Strong day: testing started, one bug found, quick fix planned, UI and API progressing fast, team fully aligned.**
