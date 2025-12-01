# Backend Implementation Summary - Sprint 3

**Project:** University Event Registration Portal  
**Sprint:** Sprint 3  
**Team Member:** Fariba (Backend Lead)  
**Date:** November 27-30, 2025

---

## Objectives

In Sprint 3, I implemented the backend functionality for the admin panel. This included creating APIs for event management (create, edit, delete) and viewing attendee information. Since we're using localStorage as our database, I simulated what would normally be server-side operations on the client side.

---

## What I Built

### 1. Admin Authentication

I modified the existing login function to check for admin credentials before checking regular users.

```javascript
function handleLogin(event) {
    // Check for admin first
    if (email === 'admin@university.edu' && password === 'admin123') {
        const adminUser = {
            id: 0,
            name: 'Admin User',
            email: 'admin@university.edu',
            role: 'admin',
            studentId: 'ADMIN'
        };
        
        currentUser = adminUser;
        localStorage.setItem('currentUser', JSON.stringify(adminUser));
        showPage('adminDashboard');
        return false;
    }
    
    // Then check regular users...
}
```

How it works:
- Admin credentials are hardcoded
- If credentials match, create an admin user object with role: 'admin'
- Store in localStorage as currentUser
- Redirect to admin dashboard instead of events page

In production, this would be an environment variable and the password would be hashed.

---

### 2. Dashboard Statistics API

Shows admins total events, total registrations, and active events.

```javascript
function loadAdminDashboard() {
    if (!currentUser || currentUser.role !== 'admin') {
        alert('Access denied. Admin privileges required.');
        showPage('home');
        return;
    }
    
    const tickets = JSON.parse(localStorage.getItem('tickets') || '[]');
    
    document.getElementById('totalEventsCount').textContent = events.length;
    document.getElementById('totalRegistrationsCount').textContent = tickets.length;
    document.getElementById('activeEventsCount').textContent = events.filter(e => e.seatsAvailable > 0).length;
}
```

First thing I do is check if the current user has admin role. If not, deny access.

---

### 3. Create Event API

Allows admins to create new events.

Validations I implemented:
1. Admin role check
2. Date validation - event date must be today or in the future
3. Capacity validation - must be a positive number
4. All required fields must be filled

ID generation:
I use `Date.now()` to generate unique IDs based on current timestamp.

Date formatting:
The date comes from the form as "2025-12-15" but I store it as "December 15, 2025" for display.

---

### 4. Edit Event API

The tricky part is calculating seat availability when capacity changes.

Let's say an event has:
- totalSeats: 100
- seatsAvailable: 80 (20 people registered)

If admin changes totalSeats to 120:
- seatsDifference = 120 - 100 = 20
- new seatsAvailable = 80 + 20 = 100

This maintains the number of people who already registered while adding the new capacity.

```javascript
const currentSeatsAvailable = events[eventIndex].seatsAvailable;
const seatsDifference = capacity - events[eventIndex].totalSeats;

events[eventIndex].seatsAvailable = currentSeatsAvailable + seatsDifference;
```

---

### 5. Delete Event API

When we delete an event, we also need to delete all tickets for that event. This is called a cascade delete.

```javascript
function confirmDeleteEvent() {
    // Delete the event
    events = events.filter(e => e.id !== currentEventToDelete);
    saveEvents();
    
    // Cascade delete tickets
    let tickets = JSON.parse(localStorage.getItem('tickets') || '[]');
    tickets = tickets.filter(t => t.eventId !== currentEventToDelete);
    localStorage.setItem('tickets', JSON.stringify(tickets));
}
```

Why cascade delete is important:
If we don't delete the tickets, we'll have orphaned records pointing to an event that doesn't exist anymore.

---

### 6. View Attendees API

Gets all people who registered for a specific event.

```javascript
function viewAttendees(eventId) {
    const tickets = JSON.parse(localStorage.getItem('tickets') || '[]');
    const eventTickets = tickets.filter(t => t.eventId === eventId);
    
    // Build table with attendee info
    // Store for CSV export
    window.currentEventForExport = { event, tickets: eventTickets };
}
```

I store the filtered tickets in a global variable so the CSV export function can access them.

---

### 7. CSV Export API

Creates a downloadable CSV file with attendee information.

```javascript
function exportAttendeesCSV() {
    let csv = 'Name,Email,Registration Date,Payment Status,Ticket Code\n';
    
    tickets.forEach(ticket => {
        csv += `"${ticket.userName}","${ticket.userEmail}","${registrationDate}","${paymentStatus}","${ticket.ticketCode}"\n`;
    });
    
    const blob = new Blob([csv], { type: 'text/csv' });
    const url = window.URL.createObjectURL(blob);
    const a = document.createElement('a');
    a.href = url;
    a.download = event.title.replace(/\s+/g, '_') + '_attendees.csv';
    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);
    window.URL.revokeObjectURL(url);
}
```

How CSV generation works:
1. Start with headers row
2. Loop through each ticket and add a row
3. Create a Blob from the CSV string
4. Create a temporary download link
5. Trigger the download
6. Clean up

---

## Helper Functions

### formatDate(dateStr)

Converts "2025-12-15" to "December 15, 2025"

### formatTime(timeStr)

Converts "14:00" to "2:00 PM"

### reverseFormatDate(dateStr)

Converts "December 15, 2025" back to "2025-12-15" for the date input field

### reverseFormatTime(timeStr)

Converts "2:00 PM" back to "14:00" for the time input field

I need both directions because:
- When displaying: Use formatted versions
- When editing: Need to convert back to input format

---

## Challenges I Faced

**Challenge 1:** Maintaining seat availability when editing capacity

Solution: Calculate the difference and add it to available seats.

**Challenge 2:** Cascade deletes

Solution: Filter the tickets array to remove all tickets with matching eventId.

**Challenge 3:** Admin vs user permissions

Solution: Check `currentUser.role === 'admin'` at the start of every admin function.

---

## Testing

I tested each function manually:

1. Create Event - valid data works, validations work correctly
2. Edit Event - capacity changes calculate seats correctly
3. Delete Event - removes event and all tickets
4. View Attendees - shows all attendees or empty state
5. CSV Export - downloads with correct format

---

## What I Would Do Differently in Production

1. Real database (PostgreSQL)
2. Hashed passwords
3. JWT tokens for authentication
4. Server-side validation
5. Environment variables for credentials
6. Input sanitization
7. Rate limiting
8. Logging for audit trail
9. Better error handling

---

## Time Spent

- Admin authentication: 1 hour
- Create event API: 2 hours
- Edit event API: 2 hours
- Delete event API: 1 hour
- View attendees API: 1 hour
- CSV export: 1 hour
- Testing: 2 hours
- Bug fixes: 1 hour

Total: 11 hours

---

## Conclusion

I successfully implemented all backend functionality for Sprint 3. The admin panel allows full CRUD operations on events and provides visibility into event registrations. While this is a localStorage-based simulation, the logic mirrors what would happen in a real backend.

All acceptance criteria for Sprint 3 backend tasks have been met.
