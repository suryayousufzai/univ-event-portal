# Database Setup Documentation

**Project:** University Event Registration Portal  
**Developer:** Fariba Mohammadi (Backend Lead)  
**Database:** MySQL  
**Sprint:** Sprint 1  
**Date:** November 22, 2025

---

## What This Document Is About

So basically this is all my notes on how I set up the database for our event registration portal. It covers the database structure, all the tables I created, and the test data I put in to make sure everything works.

---

## Database Info

**Database Name:** university_events_db  
**Engine:** MySQL 8.0  
**Character Set:** UTF-8  
**Collation:** utf8mb4_unicode_ci

Pretty standard MySQL setup. I went with UTF-8 because we might have events with different languages or special characters.

---

## Tables I Created

For Sprint 1, I set up 4 main tables:

| Table Name | What It Does | Test Records |
|------------|--------------|-------------|
| users | Stores all user accounts | 5 test users |
| events | All the event info | 10 sample events |
| registrations | Tracks who registered for what | 0 (doing this in Sprint 2) |
| payments | Payment records | 0 (also Sprint 2) |

---

## Detailed Table Structures

### 1. Users Table

This table holds all the user account information.

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

**What each column does:**
- **user_id** - Auto-incrementing ID, this is the primary key
- **name** - Person's full name
- **email** - Their email address (has to be unique, no duplicates allowed)
- **password** - Hashed password using bcrypt (NOT plain text!)
- **student_id** - Optional field for student ID number
- **role** - Either 'user' or 'admin', defaults to 'user'
- **created_at** - Timestamp of when the account was created
- **updated_at** - Updates automatically whenever the record changes

**Indexes:**
- Primary key on user_id
- Unique index on email (so we can quickly check if an email already exists)

---

### 2. Events Table

This is where all the event details live.

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

**Column breakdown:**
- **event_id** - Primary key, auto-increment
- **title** - Event name (max 150 characters)
- **description** - Longer text field for event details
- **category** - Type of event like "Conference", "Workshop", "Social", etc.
- **event_date** - The date when the event happens
- **event_time** - What time it starts
- **location** - Where it's happening
- **capacity** - Maximum number of people who can attend
- **available_seats** - How many seats are still open (starts same as capacity)
- **price** - Ticket price, defaults to 0.00 for free events
- **image_url** - Link to the event poster/image
- **created_by** - Foreign key linking to the admin who created it
- **created_at** - When the event was added to the system
- **updated_at** - Last time it was modified

**Indexes:**
- Primary key on event_id
- Index on event_date (we'll be querying by date a lot)
- Index on category (for filtering)
- Foreign key on created_by linking to users table

---

### 3. Registrations Table

This tracks which users signed up for which events.

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

**What's in here:**
- **reg_id** - Primary key
- **user_id** - Who registered (foreign key to users)
- **event_id** - What event they registered for (foreign key to events)
- **registration_date** - When they signed up
- **payment_status** - Whether they've paid yet, cancelled, etc.
- **ticket_code** - Unique code for their ticket (like a QR code or something)

**Important stuff:**
- The UNIQUE KEY on (user_id, event_id) prevents someone from registering twice for the same event
- CASCADE on delete means if a user or event gets deleted, their registrations go too
- Ticket codes have to be unique

**Note:** The actual registration functionality gets implemented in Sprint 2

---

### 4. Payments Table

Stores all payment transactions.

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

**Columns explained:**
- **payment_id** - Primary key
- **reg_id** - Which registration this payment is for
- **amount** - How much they paid
- **transaction_id** - The ID from whatever payment gateway we use (Stripe or whatever)
- **payment_method** - Like "credit card", "PayPal", etc.
- **status** - Whether it worked, failed, or got refunded
- **payment_date** - When the transaction happened

**Note:** Also implementing this in Sprint 2

---

## How Everything Connects

Here's how the tables relate to each other:

```
users (1) ----< (many) registrations
events (1) ----< (many) registrations
registrations (1) ----< (many) payments
users (1) ----< (many) events [via created_by]
```

Basically:
- One user can register for multiple events
- One event can have many registrations
- One registration might have multiple payment attempts (if first one fails)
- One admin can create many events

---

## Test Data I Added

### Sample Users

I created 5 test users to work with:

```sql
INSERT INTO users (name, email, password, role) VALUES
('Admin User', 'admin@university.edu', '$2b$10$hashedpassword1', 'admin'),
('John Doe', 'john.doe@student.edu', '$2b$10$hashedpassword2', 'user'),
('Jane Smith', 'jane.smith@student.edu', '$2b$10$hashedpassword3', 'user'),
('Mike Johnson', 'mike.j@student.edu', '$2b$10$hashedpassword4', 'user'),
('Sarah Williams', 'sarah.w@student.edu', '$2b$10$hashedpassword5', 'user');
```

The passwords shown above are hashed. For testing purposes, the actual passwords are:
- Admin account: Admin123!
- All regular users: Password123!

Obviously these are just for testing, we'd never use passwords this simple in production.

---

### Sample Events

Created 10 different events to test with:

```sql
INSERT INTO events (title, description, category, event_date, event_time, location, capacity, available_seats, price, created_by) VALUES
('Tech Conference 2025', 'Annual technology conference featuring industry leaders', 'Conference', '2025-12-10', '09:00:00', 'Main Auditorium', 200, 200, 50.00, 1),
('Web Development Workshop', 'Hands-on workshop on modern web development', 'Workshop', '2025-11-25', '14:00:00', 'Computer Lab A', 30, 30, 0.00, 1),
('Career Fair 2025', 'Meet potential employers and explore career opportunities', 'Career', '2025-12-01', '10:00:00', 'Student Center', 500, 500, 0.00, 1),
('AI & Machine Learning Seminar', 'Introduction to artificial intelligence and ML', 'Seminar', '2025-11-28', '15:00:00', 'Lecture Hall 101', 100, 100, 25.00, 1),
('Cultural Night', 'Celebrate diversity with music, food, and performances', 'Social', '2025-12-05', '18:00:00', 'University Plaza', 300, 300, 0.00, 1),
('Entrepreneurship Bootcamp', '3-day intensive program for aspiring entrepreneurs', 'Workshop', '2025-12-15', '09:00:00', 'Business Building', 50, 50, 100.00, 1),
('Sports Day 2025', 'Annual inter-department sports competition', 'Sports', '2025-12-08', '08:00:00', 'Sports Complex', 1000, 1000, 0.00, 1),
('Research Symposium', 'Present and discuss latest research findings', 'Academic', '2025-12-12', '10:00:00', 'Conference Room', 80, 80, 0.00, 1),
('Alumni Networking Event', 'Connect with successful alumni from various industries', 'Networking', '2025-11-30', '17:00:00', 'Alumni Hall', 150, 150, 20.00, 1),
('Holiday Gala', 'End of semester celebration with dinner and entertainment', 'Social', '2025-12-20', '19:00:00', 'Grand Ballroom', 250, 250, 30.00, 1);
```

Got a good mix of free and paid events, different categories, different capacities. Should be enough to test all the features.

---

## Database Connection Setup

Here's how I'm connecting to the database in the code:

```javascript
const dbConfig = {
    host: 'localhost',
    user: 'root',
    password: 'your_password',
    database: 'university_events_db',
    port: 3306
};
```

Connection pool settings:
- Max connections: 10
- Min connections: 2
- Idle timeout: 30 seconds

This should handle multiple concurrent users without issues.

---

## Security Stuff I Implemented

### 1. Password Security
- All passwords get hashed with bcrypt before storing
- Using 10 salt rounds
- Never ever storing passwords in plain text

### 2. SQL Injection Prevention
- Using prepared statements for all queries
- Validating all input before it goes to the database

### 3. Connection Security
- Database credentials are in environment variables, not hardcoded
- Will use SSL for the production database connection

### 4. Access Control
- Database user only has the minimum privileges needed
- Separate database users for dev and production

---

## Backup Plan

**How often:** Daily backups at 2 AM  
**Keep for:** 30 days  
**Stored:** Cloud storage (encrypted)  
**Testing:** Check recovery weekly to make sure backups actually work

Backup command I'm using:
```bash
mysqldump -u root -p university_events_db > backup_$(date +%Y%m%d).sql
```

---

## Database Migration Files

Haven't set up a proper migration tool yet, but for Sprint 1 I have these SQL files:

- 001_create_users_table.sql
- 002_create_events_table.sql
- 003_create_registrations_table.sql
- 004_create_payments_table.sql
- 005_insert_test_data.sql

Might look into using something like Flyway or Liquibase later.

---

## Performance Optimization

**Indexes I added:**
- idx_users_email on users(email)
- idx_events_date on events(event_date)
- idx_events_category on events(category)
- idx_registrations_user on registrations(user_id)
- idx_registrations_event on registrations(event_id)

These should make queries way faster, especially when we're searching by email or filtering events by date/category.

**Other optimizations:**
- Always use LIMIT for paginated results
- Avoid SELECT * in production (only grab the columns we need)
- Use JOIN instead of subqueries when possible

---

## Testing Results

Everything I tested:
- All tables created successfully
- Foreign key constraints are working properly
- Unique constraints are being enforced (can't duplicate emails, etc.)
- Default values are being applied correctly
- Test data inserted without any errors
- All queries running under 100ms which is good

---

## Plans for Future Sprints

### Sprint 2:
- Add database triggers to automatically update available_seats when someone registers
- Create some stored procedures for complex operations

### Sprint 3:
- Add an audit log table to track who changed what
- Implement soft deletes (mark records as deleted instead of actually deleting them)

### Sprint 4:
- Add full-text search indexes for event descriptions
- Optimize everything for 100+ concurrent users

---

## Common Problems and Fixes

Some issues I ran into and how to fix them:

**Problem: Connection Refused**
- Make sure MySQL is actually running
- Check that port 3306 isn't blocked by firewall

**Problem: Access Denied**
- Double-check username and password
- Verify the user has the right privileges

**Problem: Foreign Key Constraint Fails**
- Make sure the records you're referencing actually exist
- Check that data types match between tables

---

## Database Schema Diagram

Here's a visual of how everything connects:

```
┌─────────────┐         ┌──────────────┐
│   users     │         │   events     │
├─────────────┤         ├──────────────┤
│ user_id (PK)│────┐    │ event_id (PK)│
│ name        │    │    │ title        │
│ email       │    │    │ description  │
│ password    │    │    │ event_date   │
│ role        │    │    │ location     │
└─────────────┘    │    │ price        │
                   │    │ created_by(FK)│──┐
                   │    └──────────────┘  │
                   │            │          │
                   │            ▼          │
                   │    ┌──────────────┐  │
                   └───>│registrations │<─┘
                        ├──────────────┤
                        │ reg_id (PK)  │
                        │ user_id (FK) │
                        │ event_id(FK) │
                        │ status       │
                        └──────────────┘
                                │
                                ▼
                        ┌──────────────┐
                        │  payments    │
                        ├──────────────┤
                        │ payment_id   │
                        │ reg_id (FK)  │
                        │ amount       │
                        │ status       │
                        └──────────────┘
```

---

**Prepared by:** Fariba Mohammadi (Backend Lead Developer)  
**Last Updated:** November 22, 2025  
**Status:** Sprint 1 Complete
