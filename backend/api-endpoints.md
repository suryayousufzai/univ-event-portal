
# API Endpoints Documentation

## Authentication Endpoints

### Register User
*POST* /api/register
json
Request:
{
  "name": "Fariba Mohammadi",
  "email": "Fariba@example.com",
  "password": "SecurePass123"
}

Response:
{
  "success": true,
  "message": "User registered successfully",
  "userId": 123
}


### Login
*POST* /api/login
Fariba
Request:
{
  "email": "Fariba@example.com",
  "password": "SecurePass123"
}

Response:
{
  "success": true,
  "token": "jwt_token_here",
  "user": {
    "id": 123,
    "name": "Surya Yousufzai",
    "email": "surya@example.com"
  }
}


## Events Endpoints

### Get All Events
*GET* /api/events

Response:
json
{
  "success": true,
  "events": [
    {
      "id": 1,
      "title": "Tech Conference 2025",
      "date": "2025-12-10",
      "location": "Main Hall",
      "price": 50.00
    }
  ]
}

---

## Sprint 2 - New Endpoints

### Event Registration

*POST* /api/events/:eventId/register

*Description:* Register user for an event

*Authentication:* Required (JWT token)

*Request:*
json
{
  "userId": 6
}


*Success Response (200):*
json
{
  "success": true,
  "message": "Registration successful",
  "registrationId": 12,
  "ticketCode": "TICKET-ABC123"
}


*Error Responses:*
- 401: Not authenticated
- 400: Event is full
- 409: Already registered

---

### Process Payment

*POST* /api/payments

*Description:* Process payment for event registration

*Authentication:* Required

*Request:*
json
{
  "registrationId": 12,
  "amount": 50.00,
  "cardNumber": "4111111111111111",
  "expiryDate": "12/26",
  "cvv": "123",
  "cardholderName": "Surya Yousufzai"
}


*Success Response (200):*
json
{
  "success": true,
  "transactionId": "TXN-789456",
  "amount": 50.00
}


---

### Get Ticket

*GET* /api/tickets/:registrationId

*Description:* Get ticket details for a registration

*Authentication:* Required

*Success Response (200):*
json
{
  "success": true,
  "ticket": {
    "ticketCode": "TICKET-ABC123",
    "eventName": "Tech Conference 2025",
    "eventDate": "2025-12-15",
    "userName": "Surya Yousufzai"
  }
}


---

### Get User Registrations

*GET* /api/users/:userId/registrations

*Description:* Get all registrations for a user

*Authentication:* Required

*Success Response (200):*
json
{
  "success": true,
  "registrations": [ ... ]
}


---

### Cancel Registration

*DELETE* /api/registrations/:registrationId

*Description:* Cancel an event registration

*Authentication:* Required

*Success Response (200):*
json
{
  "success": true,
  "message": "Registration cancelled",
  "refundAmount": 50.00
}

---

## Sprint 3 - Admin Endpoints

### Admin Login Enhancement
*POST* /api/login

*Description:* Enhanced to support admin authentication

*Authentication:* None required (this is the login endpoint)

*Request:*
```json
{
  "email": "admin@university.edu",
  "password": "admin123"
}
```

*Success Response (200):*
```json
{
  "success": true,
  "token": "jwt_token_here",
  "user": {
    "id": 0,
    "name": "Admin User",
    "email": "admin@university.edu",
    "role": "admin"
  }
}
```

*Regular User Response (200):*
```json
{
  "success": true,
  "token": "jwt_token_here",
  "user": {
    "id": 123,
    "name": "Surya Yousufzai",
    "email": "surya@student.edu",
    "role": "user"
  }
}
```

*Error Responses:*
- 401: Invalid email or password
- 400: Missing required fields

---

### Get Admin Dashboard Statistics
*GET* /api/admin/dashboard

*Description:* Get statistics for admin dashboard

*Authentication:* Required (Admin only)

*Success Response (200):*
```json
{
  "success": true,
  "statistics": {
    "totalEvents": 6,
    "totalRegistrations": 15,
    "activeEvents": 5
  }
}
```

*Error Responses:*
- 401: Not authenticated
- 403: Admin privileges required

---

### Create Event
*POST* /api/admin/events

*Description:* Create a new event (admin only)

*Authentication:* Required (Admin only)

*Request:*
```json
{
  "title": "AI Workshop",
  "description": "Learn about artificial intelligence and machine learning",
  "category": "tech",
  "icon": "💻",
  "date": "2025-12-20",
  "time": "14:00",
  "location": "Computer Lab",
  "capacity": 50,
  "price": 20.00
}
```

*Success Response (200):*
```json
{
  "success": true,
  "message": "Event created successfully",
  "event": {
    "id": 1701360200000,
    "title": "AI Workshop",
    "date": "December 20, 2025",
    "time": "2:00 PM",
    "location": "Computer Lab",
    "category": "tech",
    "price": 20.00,
    "seatsAvailable": 50,
    "totalSeats": 50,
    "icon": "💻",
    "description": "Learn about artificial intelligence and machine learning"
  }
}
```

*Error Responses:*
- 401: Not authenticated
- 403: Admin privileges required
- 400: Event date must be in the future
- 400: Capacity must be a positive number
- 400: Missing required fields

---

### Get All Events (Admin View)
*GET* /api/admin/events

*Description:* Get all events with management details

*Authentication:* Required (Admin only)

*Success Response (200):*
```json
{
  "success": true,
  "events": [
    {
      "id": 1,
      "title": "Annual Music Festival",
      "date": "December 15, 2025",
      "location": "Campus Auditorium",
      "totalSeats": 200,
      "seatsAvailable": 150,
      "price": 25.00
    },
    {
      "id": 2,
      "title": "Tech Innovation Conference",
      "date": "December 20, 2025",
      "location": "Engineering Building",
      "totalSeats": 100,
      "seatsAvailable": 80,
      "price": 15.00
    }
  ]
}
```

*Error Responses:*
- 401: Not authenticated
- 403: Admin privileges required

---

### Update Event
*PUT* /api/admin/events/:eventId

*Description:* Update an existing event

*Authentication:* Required (Admin only)

*Request:*
```json
{
  "title": "AI Workshop (Updated)",
  "description": "Updated description about AI",
  "category": "tech",
  "icon": "💻",
  "date": "2025-12-20",
  "time": "14:00",
  "location": "Computer Lab - Room 301",
  "capacity": 60,
  "price": 15.00
}
```

*Success Response (200):*
```json
{
  "success": true,
  "message": "Event updated successfully",
  "event": {
    "id": 1,
    "title": "AI Workshop (Updated)",
    "seatsAvailable": 60,
    "totalSeats": 60,
    "price": 15.00
  }
}
```

*Error Responses:*
- 401: Not authenticated
- 403: Admin privileges required
- 404: Event not found
- 400: Event date must be in the future
- 400: Capacity must be a positive number

---

### Delete Event
*DELETE* /api/admin/events/:eventId

*Description:* Delete an event and all its registrations (cascade delete)

*Authentication:* Required (Admin only)

*Success Response (200):*
```json
{
  "success": true,
  "message": "Event and all registrations deleted successfully",
  "deletedEventId": 1,
  "deletedRegistrations": 5
}
```

*Error Responses:*
- 401: Not authenticated
- 403: Admin privileges required
- 404: Event not found

---

### Get Event Attendees
*GET* /api/admin/events/:eventId/attendees

*Description:* Get all attendees for a specific event

*Authentication:* Required (Admin only)

*Success Response (200):*
```json
{
  "success": true,
  "event": {
    "id": 2,
    "title": "Tech Innovation Conference"
  },
  "attendees": [
    {
      "id": 1701360100000,
      "userName": "Surya Yousufzai",
      "userEmail": "surya@student.edu",
      "registrationDate": "2025-11-30",
      "paymentStatus": "Paid",
      "ticketCode": "ABCD-1234-EFGH",
      "price": 15.00
    },
    {
      "id": 1701360200000,
      "userName": "Fariba Mohammadi",
      "userEmail": "fariba@student.edu",
      "registrationDate": "2025-11-30",
      "paymentStatus": "Paid",
      "ticketCode": "WXYZ-5678-IJKL",
      "price": 15.00
    }
  ],
  "totalCount": 2
}
```

*Success Response (No Attendees):*
```json
{
  "success": true,
  "event": {
    "id": 3,
    "title": "Art Exhibition"
  },
  "attendees": [],
  "totalCount": 0
}
```

*Error Responses:*
- 401: Not authenticated
- 403: Admin privileges required
- 404: Event not found

---

### Export Attendees to CSV
*GET* /api/admin/events/:eventId/attendees/export

*Description:* Export attendees list to CSV file

*Authentication:* Required (Admin only)

*Success Response (200):*

Downloads a CSV file named: `EventTitle_attendees.csv`

CSV Format:
```
Name,Email,Registration Date,Payment Status,Ticket Code
"Surya Yousufzai","surya@student.edu","11/30/2025","Paid","ABCD-1234-EFGH"
"Fariba Mohammadi","fariba@student.edu","11/30/2025","Paid","WXYZ-5678-IJKL"
"Marwa Ahmed","marwa@student.edu","11/30/2025","Free","LMNO-9012-PQRS"
```

*Error Responses:*
- 401: Not authenticated
- 403: Admin privileges required
- 404: Event not found
- 400: No attendees to export

---

## Error Codes Summary

### 200 OK
Request successful

### 400 Bad Request
Invalid input data or validation failed

### 401 Unauthorized
Not authenticated - login required

### 403 Forbidden
Admin privileges required

### 404 Not Found
Resource (event/registration) not found

### 409 Conflict
Duplicate entry or constraint violation

---

## Authentication

All admin endpoints require:
1. Valid JWT token in Authorization header
2. User role must be 'admin'

Example header:
```
Authorization: Bearer jwt_token_here
```

---

## Implementation Notes

### LocalStorage (Development)
In the current implementation, data is stored in browser localStorage:
- `users` - All registered users
- `events` - All events
- `tickets` - All registrations
- `currentUser` - Current session

### Production
In production environment:
- Replace localStorage with PostgreSQL/MySQL database
- Implement proper JWT authentication
- Hash passwords with bcrypt
- Add server-side validation
- Enable HTTPS
- Add rate limiting
- Implement logging and monitoring

---

## Testing Examples

### Test Admin Login
```javascript
fetch('/api/login', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    email: 'admin@university.edu',
    password: 'admin123'
  })
})
```

### Test Create Event
```javascript
fetch('/api/admin/events', {
  method: 'POST',
  headers: { 
    'Content-Type': 'application/json',
    'Authorization': 'Bearer ' + token
  },
  body: JSON.stringify({
    title: 'AI Workshop',
    description: 'Learn AI',
    category: 'tech',
    icon: '💻',
    date: '2025-12-20',
    time: '14:00',
    location: 'Computer Lab',
    capacity: 50,
    price: 20.00
  })
})
```

### Test View Attendees
```javascript
fetch('/api/admin/events/2/attendees', {
  method: 'GET',
  headers: { 
    'Authorization': 'Bearer ' + token
  }
})
```

---

## Sprint 3 Summary

**New Endpoints:** 7
1. GET /api/admin/dashboard - Dashboard statistics
2. POST /api/admin/events - Create event
3. GET /api/admin/events - List all events (admin view)
4. PUT /api/admin/events/:eventId - Update event
5. DELETE /api/admin/events/:eventId - Delete event
6. GET /api/admin/events/:eventId/attendees - View attendees
7. GET /api/admin/events/:eventId/attendees/export - Export CSV

**Modified Endpoints:** 1
- POST /api/login - Added admin authentication support

**Total Story Points:** 21
- US-011: Admin Login & Dashboard (3 points)
- US-012: Create Events (8 points)
- US-013: Edit/Delete Events (5 points)
- US-014: View Attendees (5 points)

All endpoints follow RESTful conventions and include proper validation, authentication, and error handling.


