





 **Product Owner Sprint 1 Report**\
**Product Owner: Marwa Paiman \
Project: Event Registration Portal at the University. \
Sprint: Sprint 1 (Nov 15-22, 2025)\
Report Date: November 22, 2025**











**Achievement of Sprint Goal:**\
\
**Sprint 1 goal:** \
Deliver the core user access system and event browsing capabilities, comprising of working registration capability, login capability, event browsing capability, full database configuration, initial test cases, and the UI pages.\
**Status**: Achieved 

\
**Completed User Stories :**

| ID | User Story | Story Points | Status | Notes |
|----|------------|--------------|--------|-------|
|US-001 |User registration| 5| Complete|Fully functional| All acceptance criteria have been met|
|US-002| User Login| 3 |Complete| authentication with JWT functionality| 
|US-004| Browse Events| 5 |Complete| Search and filter working|
|NFR-001 |HTTPS/Security Setup| 3 |Complete| Basic security provisions made|
**Total points completed on story**: 16/ 16 (100 percent)

**Acceptance Criteria Review**:\
**US-001: User Registration**\
Acceptance Criteria:\
Successful creation of an account.\
Email with confirmation sent (simulated)\
Duplicate emails rejected

Before storage hashed passwords.\
**PO Decision**: ACCEPTED\
**Comments:** All criteria met. Discovered and resolved testing bug of duplicate email handling. Last implementation is firm.

\
**US-002 -User Login**:\
Acceptance Criteria:\
Successful login of verified accounts.\
Logout will clear session.\
Error message appear when facing invalid Credentials \
Generated and returned JWT token.\
**PO Decision**: ACCEPTED\
**Comments**: The process of logging in is seamless. Good error handling. User experience is clean.\
\
**US-004: Browse Events**\
Acceptance Criteria:\
Events list will contain events title, venue, date.\
Search by keyword works\
Filter by category works\
Page loads within 2 seconds

**PO Decision**: ACCEPTED\
**Comment**s: The 10 sample events are all presented correctly. Search and filtering are as it should be. Performance is excellent.\
\
**NFR-001: HTTPS/Security**\
**Acceptance Criteria:**\
Each and every page loaded by using HTTPS.\
Invalid requests sent back\
Passwords encrypted\
No sensitive data in logs\
**PO Decision:** ACCEPTED\
**Comments:** Fundamental security on board. Will require improvement to production deployment.\
\
**Stakeholder Value Generated.**\
What Users Can Do Now:\
Register on the portal.\
Secure log in using email and password.\
View events on all universities.\
Search for specific events\
Filter events by category\
\
**Business Value:**\
Base on event registration system is developed.\
Ready user authentication system.\
Database design lends credence to the features in the future.\
UI is receptive to user friendliness.\
\
**Product Backlog Updates**\
Items that have been completed (Moved to Done):\
US-001 User Registration\
US-002 User Login\
US-004 Browse Events\
NFR-001 HTTPS/Security Setup\
\
**Ready for Sprint 2:**\
US-007 Register for Event (8 points)\
US-008 Payment Integration (13 points)\
US-009 Ticket Confirmation (5 points)\
\
**Backlog Refinements Made:**\
None needed Sprint 1 items.\
Sprint 2 checked and verified prepared.\
\
**Sprint Metrics:**

|Metric| Target| Actual| Status |
|--------|--------|--------|--------|
|Story Points Planned| 16| 16 |Done 100%|
|Story Points Completed| 16| 16|Done 100%|
|User Stories Completed| 4| 4|Done 100%|
|Bugs Found| 0| 1| 
|Bugs Fixed| N/A| 1|Done|
|Sprint Goal Met|Yes|Yes|Done|

**Quality Assessment**:\
**Code Quality:**\
Well-structured Backend APIs.\
Frontend components that can be reused.\
Schema of database normalized appropriately.\
Documentation comprehensive\
**Rating:** (4/5)\
\
**Testing Quality:**\
90% test pass rate\
All critical paths tested\
Bug found and fixed quickly\
Good test coverage\
**Rating:** (4/5)\
\
**User Experience:**\
A clean and intuitive UI. \
Good validation of Forms \
Clear error messages \
Responsive \
**Rating**: (5/5)\
\
**Issues encountered:**\
1\. Duplicate Email Bug (BUG-001)\
Severity: Major\
Status: Resolved\
Impact: Low, caught in testing.\
Resolution: Fixed within 1 day\
\
**No Blockers:**\
Team worked smoothly\
No major impediments\
Great collaboration\
\
**Feedback of Stakeholders:**\
The process of logging in is smooth.\
The event browsing is quick and convenient.\
The UI design is professional.\
API calls Should have loading indicators (noted on Sprint 2)\
\
**Product Vision Alignment:**

**Vision**: Develop a user friendly portal where students and staff members can find, enroll and manage university events easily.\
\
**Sprint 1 Contribution:**\
Bases attained on user management.\
Working event discovery feature.\
Security access is ensured through authentication .\
Responsive design will ensure accessibility\
**Alignment:** Excellent - Sprint 1 deliverables are in direct correspondence with the product vision. \
\
**Sprint 2 Priorities:**\
**According to Sprint 1 and stakeholders value:**\
**High Priorities:**\
Event Registration (US-007): Is a core feature and needed urgently.\
Payment Integration (US-008): A necessary option for the paid events.\
Ticket Generation (US-009) - Generates flow registration.\
**Probable Sprint 2 Capacity**: 25 story points.

\
**Sprint 2 Goal (Proposed):**\
Enabling users to register to events, accept payments and issue confirmation tickets.\
Team Performance\
What Went Well:\
Team has brought 100% of promised story points.\
All acceptance criteria met\
Effective communication with daily scrums.\
Quick bug resolution\
Documentation is excellent\
\
**Team Velocity:**\
Sprint 1: 16 story points accomplished.\
Sprint 2 estimated velocity: 20-25 points.\
**Team Rating:** (5/5)\
\
**Product Owner Decisions**:\
**ACCEPTED for Production:**\
User Registration feature\
User Login feature\
Event Browsing feature

\
**BACKLOG ITEMS READY:**\
Sprint 2 user stories that were screened and prepared.\
Acceptance criteria clear\
Dependencies which are known technically.\
**NEXT SPRINT COMMITMENT:**\
Approve Sprint 2 plan

Meeting Sprint Planning.\
Review Sprint 2 deliverables\
\
**Financial/Resource Notes**\
Budget Status: On track \
Resource Distribution: Sufficient. \
No extra resources need for the sprint 2.\
\
**Recommendations**:\
**For Sprint 2:**\
Include indicators on loading in API calls.\
Adopt superior error logs.\
Password strength indicator to be considered.\
Include email notification (real or fake)\
\
**The Future Sprints:**\
Plan for load testing (Sprint 4)\
Take into account version mobile app (after Sprint 5)\
Audit of plan accessibility (Sprint 5)\
\
**Product Owner Approval:**\
\
**Status of Sprint 1**: Approved and accepted.\
\
I, Marwa Paiman, have checked all the deliverables of Sprint 1 and confirm:\
All user stories meet the acceptance criteria.\
The Sprint 1 Goal has been met.\
The features that are delivered are valuable to users.\
The quality meet our standards.\
The team is prepared to proceed to Sprint 2.\
\
**Signature**: Marwa Paiman \
**Date:** November 22, 2025 \
**Status:** Sprint 1 Completed \
\
\
**References:**\
Product Backlog /backlog/product-backlog.md.\
Sprint 1 Backlog: /docs/sprint-backlogs/sprint-1-backlog.md\
Test Results: /docs/testing/test-results-sprint1.md\
Review of Sprints: /docs/meeting-minutes/sprint-review-2025-11-22.md.\
\
**Prepared by :** Marwa Paiman (Product Owner) \
**Date:** November 22, 2025 \
**Next Review**: Sprint 2 Review (Date TBD)
