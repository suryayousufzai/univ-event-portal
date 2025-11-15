# Software Requirements Specification  
## University Event Registration Portal  

**Project:** University Event Registration Portal  
**Version:** 1.0  
**Date:** November 9, 2025  
**Prepared by:** Surya Yousufzai (Scrum Master) and Team  

---

### 1. Introduction  

#### 1.1 Purpose  
This report involves the functional and non-functional specifications of the University Event Registration Portal. The portal also allows users (students, staff, and guests) to browse, register, pay, where necessary and have tickets or confirmations sent. Admins are able to generate, administer and track events.

#### 1.2 Scope  
The system offers web based platform where users are able to:
- See what is happening in the university.
- Book and make payments on the Internet.
- Email confirmation and downloadable tickets.
- Administrators will be able to add, modify and delete events and see attendees.

The system offers data security, performance and easy usability.  


#### 1.3 Definitions and Abbreviations  
- **UI:** User Interface  
- **API:** Application Programming Interface  
- **NFR:** Non-Functional Requirement  
- **FR:** Functional Requirement  

#### 1.4 References  
- ITC315 Course Notes – Requirement Engineering  
- Chapter 4 – Software Requirements Specification  
- Scrum Guide 2020  

---

### 2. Overall Description  

#### 2.1 Product Perspective  
It is a web application on its own, which has a service that links to a database and a payment gateway (sandbox). It supports two roles normal users and administrative users.  

#### 2.2 Product Functions  
Main functions:  
- User registration and login  
- Event browsing and search  
- Registration for events  
- Payment (for paid events)  
- Ticket confirmation  
- Admin management of events and users  

#### 2.3 User Characteristics  
- **Students/Staff/Guests:** Need a simple, easy-to-use interface.  
- **Admins:** Should be able to manage events efficiently.  

#### 2.4 Constraints  
- Must use secure HTTPS protocol.  
- Only valid users can access protected pages.  
- Must be delivered by **Dec 5, 2025**.  

#### 2.5 Assumptions and Dependencies  
- Payment gateway sandbox exists.  
- Users possess consistent internet and valid email addresses.  

---

### 3. System Requirements  

#### 3.1 Functional Requirements  

| ID | Description |
|----|--------------|
| **F-001** | User registration: visitor has the opportunity to create an account with the use of name, email and password. |
| **F-002** |  User login/logout: the users are able to log in and out securely. |
| **F-003** | Profile management: user is able to update name, contact details and student ID. |
| **F-004** | Browse events: display a list of upcoming events. |
| **F-005** | Search/filter events: users are able to search by key word, category or date. |
| **F-006** | See event details: description of the event, date, venue, and available seats.|
| **F-007** | Register event: user is capable of registering to an event and being registered. |
| **F-008** |Payment: a user is able to pay on paid events (sandbox). |
| **F-009** | Ticket creation: system gives email confirmation and downloadable ticket. |
| **F-010** | Cancel registration: user will have the ability to cancel event prior to its commencement. |
| **F-011** | Login as an administrator: the higher access is available to the administrator. |
| **F-012** |Admin create event: create event with all details. |
| **F-013** | Admin edit/delete event: edit or delete events.|
| **F-014** | Admin view attendees: view and export attendee list. |
| **F-015** | Admin reports: see registration counts and revenue. |
| **F-016** | Notification: send automated emails on registration/payment. |
| **F-017** | Multi-language: that is, switch English and local language |
| **F-018** | Audit log: This is a system which documents all significant activities. |
| **F-019** | Accessibility: site is screen reader friendly and easy to navigate |
| **F-020** | Role-based control: limit pages that have the word admin to users that are admins. |

---

#### 3.2 Non-Functional Requirements  

| ID | Description |
|----|--------------|
| **N-001** | Security: HTTPS, passwords are coded and no card data. |
| **N-002** |Performance: Page load time should be less than 2secs, payment less than 5secs. |
| **N-003** | Usability interface should be easy and simple to students. |
| **N-004** |Availability: uptime of the system 99% business hours |
| **N-005** | Reliability: system should experience graceful recovery in case of network problems |
| **N-006** | Accessibility: meet WCAG AA basic standards. |
| **N-007** | Maintainability: clean, modular, documented code. |
| **N-008** | Scalability: accommodate increment in users/ events. |
| **N-009** |  Backup and recovery Data should be backed up on daily basis and restored easily. |

---

### 4. Appendices  
- Use Case Diagram: will be incorporated in subsequent spring.  
- Sequence Diagrams: will be added during later sprint.  

---

**Prepared by:**  
 Marwa Paiman(Product Owner) and Surya Yousufzai (Scrum Master)  
University Event Registration Portal Project  
Date: November 9, 2025

### PO Review and Approval
_Product Owner:_ Marwa Paiman  
Review date: November 12, 2025  
_Approval statement:_ "I have read this Requirements Specification and ensured that it is an accurate representation of the current product vision and priorities. I agree with the SRS as my initial point to develop the Product Backlog and Sprint work."  

