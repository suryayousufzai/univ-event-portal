# Frontend Design Document  
*Prepared by:* Muneera Aman (Frontend Lead Developer)  
*Date:* November 12, 2025  

---

## Overview
The frontend of the *University Event Registration Portal* will be developed using *React.js* with a fully responsive design compatible with both desktop and mobile devices.  
This document outlines the main screens and expected behaviors for each UI page.

---

## Screens / Pages

### *1. Home Page*
*Header links:* Home, Events, About, Login, Register  

*Sections include:*
- Why choose UniEvent?  
- Number of events hosted  
- Active students  
- Partner organizations  

*Footer includes:*
- Quote  
- Contact information  
- Social media links  

---

### *2. Login Page*
*Fields:*
- Email  
- Password  

*Options:*
- “Forgot Password?” → user enters email for verification  
- “Don’t have an account? Sign up”  

---

### *3. Sign Up Page*
*Fields:*
- Full Name  
- Student ID  
- Email  
- Password  
- Confirm Password  

After successful signup → *redirect to Login* page.

---

### *4. Events Page*
Displays all *upcoming events*.

*Includes:*
- Search bar  
- “All Categories” dropdown  

*Event list details:*
- Title  
- Date & Location  
- “View Details” button  

*Filters:*
- Category  
- Date  
- Price  

---

### *5. Event Details Page*
*Shows:*
- Event title  
- Overview & detailed description  
- Event schedule/agenda (e.g., registration, keynote, lunch, networking)  
- Organizer details + contact  
- Availability info (date, location, capacity)  

*Actions:*
- “Register Now” button  
- After registration:
  - Confirmation email  
  - Options to *Cancel* or *Download Ticket*  

---

### *6. My Events Page*
Displays the list of events the user has registered for.

*Actions:*
- Cancel Registration  
- Download Ticket  

---

### *7. Admin Dashboard*
*Sidebar menu includes:*
- Create Event  
- Manage Events  
- View Reports  

Admin dashboard also includes:
- Attendee lists  
- Event management tools  

---

### *8. Admin Events Page*
*Features:*
- Button: *Create New Event*  

*Event table contains:*
- Event Name  
- Date & Time  
- Location  
- Attendees  
- Capacity  

*Actions:*
- View  
- Edit  
- Delete  

*Editable fields include:*
- Title  
- Date  
- Time  
- Venue  
- Description  
- Capacity  

---

## Tools Used
- *React.js* – main frontend library  
- *Tailwind CSS* – styling  
- *React Router* – navigation  
- *Axios* – API calls  
- *Toast notifications* – user feedback for actions  

---

## Wireframe Sketch (Text-Only Outline)
(Actual design created in Figma; this is a structural outline only.)

- *Home → Events → Event Details → Register → My Events*  
- *Admin Dashboard → Manage Events → Create / Edit / Delete*

---
