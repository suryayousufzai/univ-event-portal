
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
    "name": "John Doe",
    "email": "john@example.com"
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

```

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
  "cardholderName": "John Doe"
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
    "userName": "John Doe"
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

