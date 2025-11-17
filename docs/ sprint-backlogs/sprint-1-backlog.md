# Sprint 1 Summary Document

**Sprint:** 1  
**Duration:** Nov 15 → Nov 22, 2025  
**Scrum Master:** Surya Yousufzai  
**Product Owner:** Marwa Paiman  

---

## Sprint Goal
Deliver the core user access system and event browsing features, including:

- Working registration + login  
- Working event browsing  
- Complete database setup  
- Initial test cases  
- UI pages for registration, login, events  

---

## User Stories Included in Sprint 1

| ID       | User Story             | SP | Assigned To       |
|----------|-------------------------|----|--------------------|
| US-001   | User registration       | 5  | Fariba + Gita      |
| US-002   | User login              | 3  | Fariba + Muneera   |
| US-004   | Browse events           | 5  | Muneera            |
| NFR-001  | HTTPS / security setup  | 3  | Gita               |

---

## Sprint 1 Tasks (Detailed)

### Backend Tasks – *Assigned to Fariba*

#### 1. Database Setup
- Create database and tables (users, events, registrations, payments)  
- Test DB connection  

#### 2. Registration API
- `POST /api/register`  
- Input validation  
- Password hashing  
- Save user to DB  

#### 3. Login API
- `POST /api/login`  
- JWT authentication setup  

#### 4. Events List API
- `GET /api/events`  
- Return available events from DB  

---

### Frontend Tasks – *Assigned to Muneera*

#### 5. Login Page UI
- Form (email, password)  
- Error messages  

#### 6. Registration Page UI
- Form (name, email, password, confirm)  
- Redirect to login  

#### 7. Events List UI
- Display all events  
- Basic filtering  

---

### QA Tasks – *Assigned to Gita*

#### 8. Write Test Cases
- TC for registration  
- TC for login  
- TC for event browsing  

#### 9. Setup Testing Environment
- Postman collection setup  
- Manual testing checklist  

#### 10. CI/CD Setup (Basic)
- GitHub Actions workflow draft  

---

### Scrum Master Tasks – *Assigned to Surya*

#### 11. Meeting Coordination
- Daily Scrum notes  
- Recording upload  
- Sprint board update  

#### 12. Sprint Documentation
- Finalize sprint backlog  
- Track progress with burndown chart (start empty)  

---

## Blockers (Expected)
None at the beginning of Sprint 1.

---

## Expected Sprint 1 Deliverables
- Working backend APIs (Register, Login, Events)  
- Working UI pages  
- Basic DB ready  
- Basic QA test plan updated  
- All code pushed to GitHub in separate branches  

---

## Prepared by
**Surya Yousufzai (Scrum Master)**  
**Approved by:** Marwa Paiman (Product Owner)

