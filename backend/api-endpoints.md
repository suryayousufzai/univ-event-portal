
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
