# Daily Scrum Meeting - November 20, 2025

**Sprint:** Sprint 1 (Day 5 of 7)  
**Date:** November 20, 2025  
**Time:** 10:00 AM
**Duration:** 13 minutes  
**Location:** Zoom (online) 


---

## Who Was There?

- ✅ **Surya Yousufzai** - Scrum Master
- ✅ **Marwa Paiman** - Product Owner  
- ✅ **Fariba Mohammadi** - Backend Developer
- ✅ **Muneera Aman** - Frontend Developer
- ✅ **Gita Rahmany** - QA & DevOps Engineer


---

## Meeting Vibe

**Energy Level:** (Off the charts!)

Today was AMAZING! The bug is fixed, all APIs are done, the UI is gorgeous, and testing is almost complete! We can smell the finish line! Everyone is excited and motivated. Sprint 1 is basically done with 2 days to spare! Let's gooooo! 💪

---

## Opening (Surya - Scrum Master)

**Surya started the meeting:**

"Good morning team! Day 5 of Sprint 1! Yesterday was super productive - we fixed the bug, completed the Events API, and finished the Events UI. We're crushing it! Let's hear what everyone accomplished. Fariba, you're up first!"

---

## Fariba's Update (Backend Lead)

### What She Did Yesterday: ✅

**THE BIG NEWS:** Fariba fixed BUG-001! 

Remember the duplicate email bug that Gita found? Fariba added a check before inserting users into the database. Now if someone tries to register with an existing email, the system shows a nice, clear error message: "Email already registered." No more scary 500 errors! Gita retested it and confirmed it's completely fixed!

**PLUS:** Fariba finished the Events List API!

The endpoint `GET /api/events` is 100% complete and working! It returns all events from the database with every detail - title, date, location, price, everything. She added:
- Category filtering - want only workshops? Done!
- Keyword search - search for "tech" and get tech events!
- Tested with all 10 sample events - works perfectly!

She pushed all her code to feature branches and merged some to development.

### What She's Doing Today:

**Code cleanup time!**

1. **Refactoring** - Making the code even cleaner and more organized
2. **Adding comments** - So anyone can understand the code easily
3. **Writing documentation** - Creating a complete manual for all API endpoints
4. **Being available** - Ready to help Muneera with any API questions during integration
5. **Backend summary document** - Writing up everything built in Sprint 1

### Blockers: 

**NONE!** All Sprint 1 backend work is COMPLETE! 

### Team Reaction:

Everyone clapped (virtually)! All backend tasks done on Day 5 is incredible!

---

## Muneera's Update (Frontend Lead)

### What She Did Yesterday: 

**BIG WIN:** Muneera completed the Events List page! 

And it's not just complete - it's STUNNING! Here's what she built:

**The Events Page Features:**
- Beautiful card layout for each event
- Each card shows: image placeholder, title, date, location, price
- Free events display "Free" in green text - super clear!
- Search bar at the top - type keywords instantly
- Category filter dropdown - select Workshop, Conference, Social, etc.
- **Responsive magic:** 3 cards per row on desktop, 2 on tablet, 1 on mobile
- Professional design that looks like a real product!

**BONUS:** She started API integration!

She connected the registration form to Fariba's registration API and the login form to the login API. Did basic testing and BOTH ARE WORKING! Real data flowing between frontend and backend!

### What She's Doing Today:

**Integration Day!**

1. **Connect Events page** to the Events API - show real data from database
2. **Add loading spinners** - those spinning circles that show "please wait"
3. **Better error handling** - If something fails, show clear messages
4. **Test complete user journey** - Register → Login → Browse events
5. **Fix any UI bugs** found during testing
6. **Polish responsive design** - Make sure it's perfect on all screen sizes

### Blockers:

**NONE!** All APIs are ready and waiting! Integration can start immediately!

### Team Reaction:

Marwa was super impressed with how professional the UI looks! "It looks like a real product!"

---

## Gita's Update (QA & DevOps)

### What She Did Yesterday:

**TESTING EXTRAVAGANZA!** Gita had a busy day!

**First:** Retested BUG-001 after Fariba's fix
- Tried registering with same email twice
- Result: Perfect error message! "Email already registered"
- No crash, no 500 error
- Status: **BUG FIXED AND VERIFIED!**

**Then:** Continued with other test cases

**TC-005: Browse events**
- Checked if all 10 events display
- Result: PASSED! All events showed correctly

**TC-006: Search events**
- Searched for "Tech"
- Result: PASSED! Only tech events appeared

**TC-007: Filter by category**
- Selected "Workshop" from dropdown
- Result: PASSED! Only workshops displayed

**TC-008: Password validation**
- Tried registering with weak password "123"
- Result: PASSED! System rejected it

**TC-009: Email format validation**
- Entered invalid email "test at test"
- Result: PASSED! System caught it

**Score Update:** 9 out of 10 tests completed - **90% pass rate!**

### What She's Doing Today: 
**Final testing day!**

1. **TC-010: Responsive design** - Test on mobile, tablet, desktop sizes
2. **Integration testing** - Test Muneera's frontend-backend connection
3. **Complete user flow testing** - Register, login, browse - end to end
4. **Browser compatibility** - Chrome, Firefox, Edge, Safari
5. **Start test results document** - Write up everything for Sprint Review

### Blockers:

**NONE!** Everything is ready for final testing!

### Team Reaction:

90% pass rate with only one test remaining? Everyone is thrilled!

---

## Marwa's Update (Product Owner)

### Her Thoughts: 

**Marwa is EXTREMELY proud!**

She personally tested the bug fix yesterday - works perfectly! The error message is clear and user-friendly. She also looked at the Events List page Muneera built - her words: "It's gorgeous!"

**The Big Picture:**

All Sprint 1 features are now **functionally complete!**
- User registration - works!
- Login - works!
- Event browsing - works!

The quality is very high. Everything looks professional. She's genuinely impressed!

### What She's Doing Today:

1. **Final acceptance testing** - Going through entire user journey herself
2. **Available for questions** - Team can reach her anytime
3. **Preparing for Sprint Review** - Meeting is Saturday (Nov 22)
4. **Thinking about Sprint 2** - Starting to prioritize next features

### Blockers:

**NONE!**

### Team Reaction:

Having the Product Owner this happy is the best validation! 

---

## Sprint Progress Summary (Surya)

**Surya gave the update:**

"Team, let me tell you where we are. Yesterday we hit MAJOR milestones!"

### What's Complete:

- Bug is fixed and verified
- Events API 100% complete
- Events UI 100% complete  
- All backend work for Sprint 1 DONE!
- Frontend 95% done (just integration + polish left)
- Testing 90% complete

### Current Status:

**We're on Day 5 of 7** and we're actually **ahead of schedule!**

If we finish integration and testing today and tomorrow, Sprint 1 will be **complete by tomorrow evening** (Friday). That gives us Saturday to prepare for the Sprint Review!

### Sprint 1 Backlog Status:

- US-001: User Registration - **95% complete** (testing final bits)
- US-002: User Login - **95% complete** (testing final bits)
- US-004: Browse Events - **90% complete** (integration in progress)
- NFR-001: Security - **95% complete** (all security features implemented)

**Estimated completion:** **~15 of 16 story points done functionally!**

---

## Team Discussion

**Surya:** "Does anyone have any blockers or problems?"

**Everyone:** "No blockers!"

**Surya:** "Perfect! So today's focus:"

### Today's Action Plan:

**Fariba:**
- Code documentation and cleanup
- Help with integration questions

**Muneera:**  
- Complete API integration
- Test user flows end-to-end

**Gita:**
- Finish last test case
- Start test results document

**Marwa:**
- Final acceptance testing

**Everyone clear?**

**Team:** "Yes! Crystal clear!"

---

## Celebration Moment

**Surya:** "Team, I have to say - we're doing OUTSTANDING work! Let me list what we've accomplished:"

Found and fixed a bug quickly
Completed ALL backend work  
Built a beautiful, professional UI
Strong testing with 90% pass rate
Ahead of schedule!
Great teamwork and communication

"THIS is what great Scrum teams look like! Let's finish strong today!"

**Marwa:** "I couldn't agree more! You all are amazing! Keep this energy!"

**Team:** *Virtual high-fives all around*

---

## Sprint Metrics

| Metric | Value | Status |
|--------|-------|--------|
| Days Completed | 5 of 7 | Ahead |
| Story Points Done | ~15 of 16 | 94% |
| Tests Passed | 9 of 10 | 90% |
| Bugs Remaining | 0 | 
| Team Morale | 10/10 | 
| On Track? | YES! | 

---

## Blockers / Impediments

**Status:** **ZERO BLOCKERS!**

For the first time this sprint, literally nobody has any blockers! Everything is flowing smoothly!

---

## Action Items

| Action | Owner | Due | Priority |
|--------|-------|-----|----------|
| Complete API integration | Muneera | Nov 20 EOD | High |
| Finish TC-010 (responsive) | Gita | Nov 20 EOD | High |
| Code documentation | Fariba | Nov 20 EOD | Medium |
| Final acceptance testing | Marwa | Nov 20 EOD | High |
| Start test results doc | Gita | Nov 20 | Medium |

---

## Personal Notes (Surya)

This was one of the best daily scrums of the sprint! Everyone is energized, motivated, and proud of what we've built. No blockers, high morale, ahead of schedule - what more could a Scrum Master ask for?

The bug fix yesterday was handled professionally - found quickly, fixed quickly, verified quickly. That's the sign of a mature team!

We're going to nail this Sprint Review on Saturday! 

---

## What's Next?

**Tomorrow (Nov 21):**
- Final polish and testing
- Complete all documentation
- Prepare demos for Sprint Review

**Saturday (Nov 22):**
- Sprint Review at 2:00 PM
- Sprint Retrospective at 4:00 PM
- CELEBRATE! 

---

## Recording

-  [Watch Meeting Recording](https://drive.google.com/file/d/1cp4pMPbnun3gDn0_nC9YqJwKp92yzFYX/view?usp=drive_link)


---

**Document Prepared by:** Surya Yousufzai (Scrum Master)   


---



</div>
