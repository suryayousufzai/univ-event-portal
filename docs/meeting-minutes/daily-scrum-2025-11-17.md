# daily scrum meeting #6 – november 17, 2025

**project:** university event registration portal  
**sprint:** sprint 1 (day 2)  
**meeting type:** daily scrum  
**duration:** 12 mins  
**time:** 10:00 am  
**platform:** google meet  

---

## Attendees
- surya yousufzai — scrum master  
- marwa paiman — product owner  
- fariba mohammadi — backend lead  
- muneera aman — frontend lead  
- gita rahmany — qa & devops  

✔️ everyone attended

---

## Meeting intro

**Surya:**  
good morning team! it’s day 2 of sprint 1. yesterday was mostly setup. today let’s focus on what got done and what’s next.

---

## updates from each member

### Fariba (backend)
**yesterday:**
- created database `university_events_db`
- finished `users` and `events` tables  
- started `registrations` table  
- added 5 test users + 10 sample events  
- db setup almost done 🎉

**today:**
- complete `registrations` & `payments` tables  
- start registration api (`POST /api/register`)  
- set up express.js routes  
- install bcrypt (using 10 salt rounds)  
- test db connection  

**blockers:** none  
**progress:** database ~80% done  

---

### Muneera (frontend)
**yesterday:**
- created the react project successfully  
- set up folder structure (components, pages, services)  
- installed router, axios, tailwind  
- made basic navbar + footer  
- routing is ready 👍

**today:**
- work on login page ui  
- build reusable form inputs  
- style everything with tailwind  
- basic validation (email format, password length)  
- connect form to state  

**blockers:** none for now (waiting for backend later)  
**progress:** frontend setup ~70% done  

---

### Gita (qa & devops)
**Yesterday:**
- created test case templates (registration + login)  
- set up postman workspace  
- manual testing checklist ready  
- made spreadsheet for test data  

**today:**
- write test cases for event browsing  
- start postman api test collection  
- create password validation scenarios  
- make bug report template  
- review db for testing needs  

**blockers:** none  
**progress:** ~60% ready  

---

### Marwa (product owner)
**updates:**
- reviewed progress – everything looks on track  
- confirmed database setup with fariba  
- ui from yesterday looks good (figma match)  
- no changes to sprint backlog

**today:** available for questions & will review api criteria with fariba  
**blockers:** none  

---

### Surya (scrum master)
**yesterday:**
- updated sprint board  
- organized documentation  
- uploaded meeting recording  

**Today:**
- update burndown chart  
- track progress  
- make sure frontend & backend stay aligned  

**blockers:** none  

---

## Sprint progress (day 2/7)

| user story | status |
|------------|--------|
| us-001 registration (5 pts) | ~30% |
| us-002 login (3 pts) | ~20% |
| us-004 browse events (5 pts) | ~10% |
| nfr-001 security (3 pts) | ~15% |

✔️ **0 / 16 story points completed (still in dev stage)**

### Tasks
- [x] db tables created  
- [x] sample data added  
- [x] react base setup  
- [x] test case templates done  
- [ ] registration api (in progress)  
- [ ] login ui (starting today)  
- [ ] api testing prep (in progress)  

---

## 💬 discussion

**Fariba:** “using bcrypt with 10 salt rounds – is that ok?”  
→ **Marwa:** “yes, that’s standard. go ahead.”

**Muneera:** “should i add 'remember me' option on login page?”  
→ **Marwa:** “not now, we’ll add it in sprint 2.”

**Gita:** “student_id field is required?”  
→ **Marwa:** “optional, registration only needs name, email, password.”

**Surya:** “great progress team! db looks solid.”

✔️ all agreed

---

## Blockers / issues
✨ none reported today

---

## Action items

| task | owner | due |
|------|--------|-----|
| finish registration api | fariba | nov 18 |
| complete login ui | muneera | nov 17 (eod) |
| finalize test cases | gita | nov 17 (eod) |
| update sprint board | surya | nov 17 (eod) |

---

## Key decisions
1. bcrypt with 10 salt rounds confirmed  
2. “remember me” moved to sprint 2  
3. student_id optional during registration  

---

## Estimated by end of today
- database → 100%  
- registration api → ~40%  
- login ui → ~50%  
- test cases → ~80%  

✔️ overall progress is going well

---

## Next scrum
**november 18, 2025 – 10:00 am – google meet**

---

## Meeting recording
https://drive.google.com/file/d/145D6iFhDYAso_0BiYWeP2gwrn_RU6BJm/view?usp=drive_link

---

**notes by:** surya yousufzai (scrum master)  
**date:** november 17, 2025
