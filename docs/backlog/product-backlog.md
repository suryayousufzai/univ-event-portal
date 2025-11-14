





**University Event Registration Portal Backlog**

**Marwa Paiman (Product Owner)**

**Software Engineering - ITC315** 

**13/11/2025**











**1. Introduction**

The Product Backlog is the only repository for work items in the University Event Registration Portal. It is drawn from Software Requirements Specification (SRS) and covers all functional and non-functional requirements defined as User Stories and Technical Stories. Each entry defines acceptance criteria, priority and effort estimation. The backlog is not static. It changes as the project progresses

**2. Functional Backlog Items (User Stories)**

|**ID**|**User Story**|**Acceptance Criteria**|**Priority**|**Estimation (Story Points)**|**Sprint**|**Responsible**|
| :-: | :-: | :-: | :-: | :-: | :-: | :-: |
|US 001|As a visitor, I want to create an account with my name, email, and password so I can access the portal.|Account created; confirmation email sent; duplicate emails rejected.|High|5|Sprint 1|Backend Lead (Fariba) + QA (Gita)|
|US 002|As a user, I would like to be able to log in and out safely to navigate my profile and events. |Verified account login is successful; cleared out session; denied invalid account login.|High|3|Sprint 1|<p>Backend Lead (Fariba) + </p><p>` `Frontend (Muneera)</p>|
|US 003|As a user, I would like to change my profile (name, contact, student ID) to ensure that my data is up to date.|Changes made on profile; confirmation message appeared.|Medium|3|Sprint 2|Backend Lead (Fariba)+ Frontend (Muneera)|
|US 004|As a user, I would like to navigate through future events to be able to know what is happening in the university.|Events list is with title, venue, date.|High|5|Sprint 1|Frontend Lead (Muneera)|
|US 005|As a user, I would like to be able to search/filter events by keyword, category or date in order to find the relevant events.|Results of search are correct; filters used properly.|High|8|Sprint 2|Frontend Lead (Muneera)|
|US 006|As a user, I desire to see event details to enable me make a decision of attending or not.|Page of event displays description, date, location and seats available.|High|3|Sprint 1|Frontend Lead (Muneera)|
|US 007|As a user, I want to register for an event so I can confirm my participation.|Registration saved; confirmation email sent; duplicate prevented.|High|8|Sprint 2|Backend Lead (Fariba) + QA (Gita)|
|US 008|As a user, I want to pay for paid events online so I can secure my spot.|Payment processed via sandbox; receipt generated; failed payments handled.|High|13|Sprint 2|Backend Lead (Fariba)|
|US 009|As a user, I want to receive a ticket/confirmation so I can attend the event.|Ticket downloadable; confirmation email includes QR code/ID.|High|5|Sprint 2|Backend Lead (Fariba) + QA (Gita)|
|US 010|As a user, I would like to cancel my registration prior to the event beginning to free my spot.|Confirmed cancellation; released seat; e-mail notification.|Medium|5|Sprint 3|Backend Lead (Fariba)|
|US 011|As an admin, I want to log in with higher privileges so I can manage events.|Admin dashboard accessible only to admins.|High|3|Sprint 3|Backend Lead (Fariba)|
|US 012|As an admin, I want to create events with details so I can publish them.|Event saved; visible to users; validation on required fields.|High|8|Sprint 3|Backend Lead (Fariba) + Frontend Lead (Muneera)|
|US 013|As an admin, I would like to edit or remove events in order to maintain the accuracy of the information|Saved changes, and deleted events erased from the list|High|5|Sprint 3|Backend Lead (Fariba)+ Frontend (Muneera)|
|US 014|As an administrator, I would like to view and export attendee lists to be able to manage participation,|Attendant list (csv/ PDF); accurate data.|Medium|8|Sprint 4|Backend Lead (Fariba) + QA (Gita)|
|US 015|As an administrator, I would like to see reports (registrations, revenue) in order to monitor performance.|Reports generated; charts/tables displayed.|Medium|13|Sprint 4|Backend Lead (Fariba) + QA (Gita)|
|US 016|I as a user would like to get automated notification to avoid missing updates.|Email sent on registration, payment, cancellation.|Medium|5|Sprint 4|Backend Lead (Fariba)|
|US 017|As a user, I want to switch between English and local language so I can use the portal easily.|Language toggle works; translations accurate.|Low|8|Sprint 5|Frontend Lead (Muneera)|
|US 018|As an admin, I want an audit log so I can track system activities.|Log records login, registration, payment, admin changes.|Medium|8|Sprint 4|Backend Lead (Fariba)|
|US 019|As a user, I want the portal to be accessible so I can use it with assistive technologies.|Meets WCAG AA standards; screen reader friendly.|Medium|8|Sprint 5|Frontend Lead (Muneera) + QA (Gita)|
|US 020|I would prefer role based access control as a system where only the admins can use the features of an admin.|Non admins unable to access pages of admins; experimented with numerous roles.|High|5|Sprint 3|Backend Lead (Fariba)|

**Non Functional Backlog Items (Technical Stories)**

|**ID**|**Technical Story**|**Acceptance Criteria**|**Priority**|**Estimation**|**Sprint**|**Responsible**|
| :-: | :-: | :-: | :-: | :-: | :-: | :-: |
|NFR 001|As a system, I should implement HTTPS on all connections.|Each and every page was accessed through HTTPS; invalid requests were sent back.|High|3|Sprint 1|QA/DevOps (Gita)|
|NFR 002|As a system, I should be able to load pages within 2 seconds when there is normal load.|Performance tests pass; <2s response time.|High|8|Sprint 2|QA/DevOps (Gita)|
|NFR 003|As a system, I must support 100 concurrent users.|Load test passes with 100 users.|High|13|Sprint 4|QA/DevOps (Gita)|
|NFR 004|As a system, I must back up data daily.|Backup job runs daily; restore tested.|Medium|5|Sprint 4|QA/DevOps (Gita)|
|NFR 005|As a system, I must run on major browsers.|Tested on Chrome, Edge, Firefox.|Medium|3|Sprint 5|QA/DevOps (Gita)|
|NFR 006|As a system, I must comply with data protection regulations.|Privacy policy documented; no sensitive card data stored.|High|8|Sprint 5|QA/DevOps (Gita)|
|NFR 007|As a system, I must recover gracefully from network failures.|Recovery tested; no data loss.|Medium|5|Sprint 4|QA/DevOps (Gita)|
|NFR 008|As a system, I must maintain modular, documented code.|Code reviewed; documentation updated.|Medium|5|Sprint 5|Backend Lead (Fariba) + QA (Gita)|

**Prioritization Strategy**:\
\
**High Priorities**: Main features such as registration, login, event browsing, payment, administrative management, security).\
**Medium Priorities**: Enhancement such as reports, notifications, audit logs, accessibility, reliability).\
**Low Priorities**: Optional features such as multi-language support).\
\
**Guidance on Sprint Planning:**\
\
**Sprint 1 (20 pts):** User Registration/ Login, Browsing of events, Database setting.\
**Sprint 2 (25 pts):** Registration of Event, Cancellation, Payment Integration.\
**Sprint 3 (23 pts):** Create/Edit/ Delete Events Adams Dashboard.\
**Sprint 4 (26 pts):** Audit logs, Reports, Notifications.\
**Sprint 5 (20 pts**): Accessibility, Multi language Support, Final Testing and Deployment.



