# Sprint 1 - Backend Work Summary
**Developer:** Fariba Mohammadi  
**Dates:** Nov 15–22, 2025

Okay, so here's everything I managed to finish this sprint. Pretty happy with how it turned out!

---

## What I Got Done

### Database Setup
First task was getting the **MySQL database** up and running from scratch.

- **Created 4 main tables:**
  - `users` – stores user info (id, name, email, password hash, etc.)
  - `events` – stores event details (title, date, location, price, category)
  - `registrations` – tracks which user registered for which event
  - `payments` – keeps record of payments for each registration

- Proper foreign key relationships were set up  
  _(e.g., `registrations.user_id` and `registrations.event_id`)_
- Added indexes on frequently queried fields (like `email`, `event_date`) to improve performance

---

### User Registration Endpoint  
**Route:** `POST /api/register`

This allows new users to sign up.

- Validates email format (regex check)
- Verifies password strength (min 8 chars, must include numbers)
- **Uses bcrypt for password hashing** – no plain text passwords!
- Checks for duplicate email before inserting
- On success, returns confirmation and new user ID

---

### Login Endpoint  
**Route:** `POST /api/login`

- Accepts email and password
- Searches for user by email
- Compares password with stored bcrypt hash
- Generates **JWT token** on success
- Returns token + basic user info (`id`, `name`, `email`)
  
_This token will be used to secure future API requests._

---

### Get Events List  
**Route:** `GET /api/events`

Returns all available events with the following features:

- Automatically hides past events
- **Filtering options:**
  - By *category* (e.g., conference, workshop)
  - By *date range*
- **Supports pagination** (10 items per page by default)
- Responds with an array of detailed event objects

---

## Testing

Tested everything thoroughly using **Postman**.

Test cases included:
- Valid API requests
- Requests with missing or invalid data
- Edge cases (e.g., duplicate email, incorrect password)

👉 All tests passed successfully, and results were shared with QA.

---

## Problems I Ran Into

| Issue | Details | Status |
|------|----------|--------|
| Password stored in plain text 😬 | Forgot to hash initially | Fixed using bcrypt |
| No duplicate email handling | QA caught the bug | Added validation before user creation |

> Lesson learned: **security checks first, always!**

---

##  Next Sprint Plans

For **Sprint 2**, I'll be working on:

- Event registration endpoint
- Payment processing API
- Integrating payment gateway _(likely Stripe)_

---

Feeling good about progress so far—authentication and database setup were the toughest parts, and they're all sorted now. Ready to build on top of it in Sprint 2.

