 # University Event Registration Portal
 ## Backend Database Schema
---

## Objective
In this part, the backend system will be using database to sort out the data that saves in this portal. MySQL is the prefered database software to store all data in the separated tables about users, events, and registrations in a very effective and secure way.  

---

## Database Tables

### 1. Users
| Field  | Type  | Description    |
|--------|-------|----------------|
| user_id | INT (PK) | Unique user ID |
| name | VARCHAR(100) | User’s full name |
| email | VARCHAR(100) | User’s email (unique) |
| password | VARCHAR(255) | Encrypted password |
| role | ENUM('user','admin') | Defines user type |
| created_at | DATETIME | Account creation date |

---

### 2. Events
| Field  | Type  | Description  |
|--------|-------|--------------|
| event_id | INT (PK) | Unique event ID |
| title | VARCHAR(150) | Event name |
| description | TEXT | Event details |
| category | VARCHAR(50) | Type of event |
| event_date | DATE | Date of the event |
| location | VARCHAR(100) | Venue |
| price | DECIMAL(10,2) | Ticket price (0 for free) |
| created_by | INT (FK) | Admin who created the event |
| created_at | DATETIME | Creation timestamp |

---

### 3. Registrations
| Field  | Type  | Description  |
|--------|-------|--------------|
| reg_id | INT (PK) | Registration ID |
| user_id | INT (FK) | Registered user |
| event_id | INT (FK) | Selected event |
| payment_status | ENUM('pending','paid','cancelled') | Payment result |
| registered_at | DATETIME | Time of registration |

---

### 4. Payments
| Field  | Type  | Description  |
|--------|-------|--------------|
| payment_id | INT (PK) | Payment ID |
| reg_id | INT (FK) | Registration record |
| amount | DECIMAL(10,2) | Amount paid |
| transaction_id | VARCHAR(100) | Payment gateway transaction ID |
| status | ENUM('success','failed','refunded') | Payment outcome |
| date | DATETIME | Payment date |

---

*Written by:* Fariba Mohammadi (Backend Lead Developer)  
*Date:* November 14, 2025  
