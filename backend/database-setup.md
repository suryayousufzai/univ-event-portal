# University Event Registration Portal – Backend Database Documentation

**Developer:** Fariba Mohammadi (Backend Lead)  
**Database:** MySQL  
**Sprints Included:** Sprint 1 + Sprint 2  
**Updated:** November 26, 2025

---

## What This Document Covers

This file includes both Sprint 1 and Sprint 2 work for the database side of our University Event Registration Portal.

Basically, everything from database setup → tables → relationships → test data → triggers → stored procedures → improvements made in Sprint 2.

The writing is kept simple, natural, and student-friendly so it's easy to read later or present in class.

---

## Sprint 1 – Database Setup

### Database Info

- **Database Name:** `university_events_db`
- **Engine:** MySQL 8.0
- **Charset:** UTF-8
- **Collation:** `utf8mb4_unicode_ci`

UTF-8 is used so we can handle names, languages, and special characters without problems.

---

### Tables Created in Sprint 1

| Table | Purpose | Test Data |
|-------|---------|-----------|
| `users` | Stores all user accounts | 5 users |
| `events` | Stores all event info | 10 sample events |
| `registrations` | Tracks event sign-ups | Added in Sprint 1 (used in Sprint 2) |
| `payments` | Tracks payment records | Used in Sprint 2 |

---

## Table Structures

### Users Table

```sql
CREATE TABLE users (
    user_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    student_id VARCHAR(50),
    role ENUM('user', 'admin') DEFAULT 'user',
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

**Quick Explanation:**
- Stores all account info (admins + students)
- Email must be unique
- Passwords are bcrypt-hashed
- Roles decide permissions

---

### Events Table

```sql
CREATE TABLE events (
    event_id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(150) NOT NULL,
    description TEXT,
    category VARCHAR(50),
    event_date DATE NOT NULL,
    event_time TIME,
    location VARCHAR(100),
    capacity INT DEFAULT 100,
    available_seats INT DEFAULT 100,
    price DECIMAL(10,2) DEFAULT 0.00,
    image_url VARCHAR(255),
    created_by INT,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (created_by) REFERENCES users(user_id) ON DELETE SET NULL
);
```

**Highlights:**
- `available_seats` starts equal to capacity
- `created_by` references an admin in the users table

---

### Registrations Table

```sql
CREATE TABLE registrations (
    reg_id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    event_id INT NOT NULL,
    registration_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    payment_status ENUM('pending', 'paid', 'cancelled') DEFAULT 'pending',
    ticket_code VARCHAR(50) UNIQUE,
    FOREIGN KEY (user_id) REFERENCES users(user_id) ON DELETE CASCADE,
    FOREIGN KEY (event_id) REFERENCES events(event_id) ON DELETE CASCADE,
    UNIQUE KEY unique_registration (user_id, event_id)
);
```

**Notes:**
- Prevents duplicate registrations (user cannot register twice for the same event)
- Cascade delete → if the event/user is deleted, the registration disappears too
- `ticket_code` is unique per registration

---

### 4️⃣ Payments Table

```sql
CREATE TABLE payments (
    payment_id INT AUTO_INCREMENT PRIMARY KEY,
    reg_id INT NOT NULL,
    amount DECIMAL(10,2) NOT NULL,
    transaction_id VARCHAR(100) UNIQUE,
    payment_method VARCHAR(50),
    status ENUM('success', 'failed', 'refunded') DEFAULT 'success',
    payment_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (reg_id) REFERENCES registrations(reg_id) ON DELETE CASCADE
);
```

---

## How Tables Connect

```
users (1) ----< registrations (many)
events (1) ----< registrations (many)
registrations (1) ----< payments (many)
users (1) ----< events (created_by)
```

So:
- A user can join many events
- An event has many registrations
- A registration can have multiple payment attempts
- Admins create events

---

## Sprint 1 Test Data

### Sample Users

```sql
INSERT INTO users (name, email, password, role) VALUES
('Surya Yousufzai', 'admin@university.edu', '$2b$10$hashedpassword1', 'admin'),
('Fariba Mohammadi', 'fariba.m@student.edu', '$2b$10$hashedpassword2', 'user'),
('Marwa Payman', 'marwa.p@student.edu', '$2b$10$hashedpassword3', 'user'),
('Gita Rahmany', 'gita.r@student.edu', '$2b$10$hashedpassword4', 'user'),
('Muneera', 'muneera@student.edu', '$2b$10$hashedpassword5', 'user');
```

**Testing passwords:**
- Admin → `Admin123!`
- Users → `Password123!`

*(Only for testing! Not for real apps.)*

---

### Sample Events (10 total)

```sql
INSERT INTO events (title, description, category, event_date, event_time, location, capacity, available_seats, price, created_by) VALUES
('Tech Conference 2025', ..., 200, 200, 50.00, 1),
('Web Development Workshop', ..., 30, 30, 0.00, 1),
('Career Fair 2025', ..., 500, 500, 0.00, 1),
('AI & Machine Learning Seminar', ..., 100, 100, 25.00, 1),
('Cultural Night', ..., 300, 300, 0.00, 1),
('Entrepreneurship Bootcamp', ..., 50, 50, 100.00, 1),
('Sports Day 2025', ..., 1000, 1000, 0.00, 1),
('Research Symposium', ..., 80, 80, 0.00, 1),
('Alumni Networking Event', ..., 150, 150, 20.00, 1),
('Holiday Gala', ..., 250, 250, 30.00, 1);
```

---

## Sprint 2 – Backend Database Enhancements

Sprint 2 focused on automation, data consistency, and smarter DB operations.

---

### 1. Database Trigger for Handling Event Seats

Whenever someone registers, we want the system to automatically reduce available seats.

**Trigger: Reduce seat count when registration is added**

```sql
CREATE TRIGGER reduce_seats
AFTER INSERT ON registrations
FOR EACH ROW
BEGIN
    UPDATE events
    SET available_seats = available_seats - 1
    WHERE event_id = NEW.event_id;
END;
```

**Trigger: Increase seats if registration is deleted (cancellation)**

```sql
CREATE TRIGGER increase_seats
AFTER DELETE ON registrations
FOR EACH ROW
BEGIN
    UPDATE events
    SET available_seats = available_seats + 1
    WHERE event_id = OLD.event_id;
END;
```

---

### 🧠 2. Stored Procedures

#### Procedure: Register a User for an Event

This combines:
- Check if seats available
- Insert registration
- Return ticket code

```sql
DELIMITER //

CREATE PROCEDURE register_user_for_event(
    IN p_user_id INT,
    IN p_event_id INT
)
BEGIN
    DECLARE seats INT;

    SELECT available_seats INTO seats
    FROM events
    WHERE event_id = p_event_id;

    IF seats > 0 THEN
        INSERT INTO registrations (user_id, event_id, ticket_code)
        VALUES (p_user_id, p_event_id, UUID());

    ELSE
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'No seats available';
    END IF;
END //

DELIMITER ;
```

---

#### Procedure: Add Payment

```sql
DELIMITER //

CREATE PROCEDURE add_payment(
    IN p_reg_id INT,
    IN p_amount DECIMAL(10,2),
    IN p_method VARCHAR(50)
)
BEGIN
    INSERT INTO payments (reg_id, amount, payment_method, transaction_id)
    VALUES (p_reg_id, p_amount, p_method, UUID());
END //

DELIMITER ;
```

---

## Security Improvements in Sprint 2

- Added more strict validation before inserting registrations
- Ensured ticket codes are always unique
- Input sanitization added to API layer
- ENV variables used for database credentials

---

## Performance Optimization Updates

New indexes added in Sprint 2:
- `idx_registrations_user`
- `idx_registrations_event`
- `idx_payments_reg`

These helped with faster JOIN queries for dashboards.

---

## Updated Schema Diagram

```
┌─────────────┐         ┌──────────────┐
│   users     │         │   events     │
├─────────────┤         ├──────────────┤
│ user_id (PK)│────┐    │ event_id (PK)│
│ name        │    │    │ title        │
│ email       │    │    │ capacity     │
│ password    │    │    │ available_seats
│ role        │    │    │ created_by(FK)
└─────────────┘    │    └──────────────┘
                   │            │
                   │            ▼
                   │    ┌──────────────┐
                   └───>│registrations │
                        ├──────────────┤
                        │ reg_id (PK)  │
                        │ user_id (FK) │
                        │ event_id(FK) │
                        │ ticket_code  │
                        └──────────────┘
                                │
                                ▼
                        ┌──────────────┐
                        │  payments    │
                        ├──────────────┤
                        │ payment_id   │
                        │ reg_id (FK)  │
                        │ amount       │
                        └──────────────┘
```

---

## Sprint Status Summary

### Sprint 1 Completed:
- All tables created
- Test data added
- Database structure stable

### Sprint 2 Completed:
- Triggers added
- Stored procedures created
- Seat automation implemented
- Optimized indexes
- Registration & payment logic now much smoother

---

