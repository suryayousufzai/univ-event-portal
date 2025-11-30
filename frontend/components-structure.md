# Frontend Components Structure

*Project:* University Event Registration Portal  
*Developer:* Muneera Aman (Frontend Lead)  
*Sprint:* Sprint 1  
*Date:* November 22, 2025

---

## Overview
This document describes the React component structure and organization for the University Event Registration Portal frontend.

---

## Technology Stack
- *React.js* - Main framework
- *React Router* - Page navigation
- *Tailwind CSS* - Styling
- *Axios* - API calls

---

## Components Implemented in Sprint 1

### 1. *Layout Components*

#### Navbar.jsx
*Purpose:* Navigation bar displayed on all pages  
*Features:*
- Logo and site title
- Navigation links (Home, Events, Login, Register)
- Responsive hamburger menu for mobile
- Changes to show "My Events" and "Logout" when user is logged in

*Props:*
- isLoggedIn (boolean) - Shows different menu items based on login status

---

#### Footer.jsx
*Purpose:* Footer section displayed on all pages  
*Features:*
- University contact information
- Social media links
- Copyright information

*Props:* None

---

### 2. *Page Components*

#### LoginPage.jsx
*Purpose:* User login page  
*Features:*
- Email input field
- Password input field
- "Remember me" checkbox
- "Forgot password?" link
- "Sign up" link for new users
- Form validation
- API call to /api/login

*State:*
- email (string)
- password (string)
- error (string) - for error messages
- loading (boolean) - for loading state

*API Integration:*
javascript
POST /api/login
Body: { email, password }
Response: { token, user }

---

#### RegisterPage.jsx
*Purpose:* New user registration page  
*Features:*
- Full name input
- Email input
- Password input
- Confirm password input
- Student ID input (optional)
- Form validation
- API call to /api/register
- Redirects to login page on success

*State:*
- name (string)
- email (string)
- password (string)
- confirmPassword (string)
- studentId (string)
- error (string)
- loading (boolean)

*Validation Rules:*
- Email must be valid format
- Password minimum 8 characters
- Password must match confirm password
- All required fields must be filled

*API Integration:*
javascript
POST /api/register
Body: { name, email, password, studentId }
Response: { success, userId }

---

#### EventsPage.jsx
*Purpose:* Display list of all events  
*Features:*
- Search bar
- Category filter dropdown
- Date filter
- Grid of event cards
- API call to /api/events

*State:*
- events (array) - list of events
- searchTerm (string)
- selectedCategory (string)
- loading (boolean)

*Child Components:*
- EventCard (multiple instances)

*API Integration:*
javascript
GET /api/events
Response: { events: [...] }

---

### 3. *Reusable Components*

#### EventCard.jsx
*Purpose:* Display individual event information in a card format  
*Features:*
- Event image/thumbnail
- Event title
- Date and time
- Location
- Price (or "Free")
- Available seats
- "View Details" button

*Props:*
- event (object)
  - id
  - title
  - date
  - location
  - price
  - availableSeats
  - imageUrl

*Usage:*
jsx
<EventCard 
  event={{
    id: 1,
    title: "Tech Conference 2025",
    date: "2025-12-10",
    location: "Main Hall",
    price: 50.00,
    availableSeats: 100
  }}
/>

---

#### Button.jsx
*Purpose:* Reusable button component with consistent styling  
*Features:*
- Primary and secondary variants
- Loading state
- Disabled state

*Props:*
- text (string) - button text
- onClick (function) - click handler
- variant (string) - "primary" | "secondary"
- loading (boolean)
- disabled (boolean)

---

### 4. *Service Layer*

#### api.js
*Purpose:* Centralized API communication  
*Features:*
- Axios instance configuration
- Base URL setup
- Authentication token handling
- Error handling

*Functions:*
javascript
// Authentication
export const loginUser = (email, password) => {...}
export const registerUser = (userData) => {...}

// Events
export const getEvents = () => {...}
export const getEventById = (id) => {...}

---

### 5. *Utility Functions*

#### validation.js
*Purpose:* Form validation helper functions  
*Functions:*
- validateEmail(email) - checks email format
- validatePassword(password) - checks password strength
- validateRequired(value) - checks if field is not empty

---

## Component Communication Flow

App.jsx
  ├── Navbar
  ├── LoginPage
  │     └── api.loginUser()
  ├── RegisterPage
  │     └── api.registerUser()
  └── EventsPage
        ├── EventCard (multiple)
        └── api.getEvents()

---

## Styling Approach

All components use *Tailwind CSS* utility classes:
- Consistent color scheme (blue primary, gray secondary)
- Responsive design (mobile-first approach)
- Hover and focus states
- Form input styling
- Button styling

*Example:*
jsx
<button className="bg-blue-600 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
  Login
</button>

---

## State Management

Currently using *React useState* for local component state.

For future sprints, may implement:
- Context API for global state (user authentication)
- Redux (if app grows more complex)

---

## Routing

Using *React Router* for navigation:
javascript
<Routes>
  <Route path="/" element={<HomePage />} />
  <Route path="/login" element={<LoginPage />} />
  <Route path="/register" element={<RegisterPage />} />
  <Route path="/events" element={<EventsPage />} />
</Routes>

---

## Components Planned for Future Sprints

*Sprint 2:*
- EventDetailsPage.jsx
- EventRegistrationForm.jsx
- PaymentPage.jsx

*Sprint 3:*
- AdminDashboard.jsx
- CreateEventForm.jsx
- EditEventForm.jsx

*Sprint 4:*
- MyEventsPage.jsx
- TicketDownload.jsx
- NotificationsList.jsx

---

## Testing

Each component should be tested for:
- Renders correctly
- Handles user input
- Validates forms
- Makes correct API calls
- Displays error messages
- Responsive on different screen sizes

---

*Prepared by:* Muneera Aman (Frontend Lead Developer)  
*Last Updated:* November 22, 2025


## Sprint 2 - Components

### Page Components
#### EventDetailsPage.jsx
*Purpose:* Display full information about a single event  cardholder
*Location:* src/pages/EventDetailsPage.jsx

*Props:*
- None (gets eventId from URL params)

*State:*
- event (object) - Event details from API
- loading (boolean)
- error (string)
- showModal (boolean) - For registration modal

*API Calls:*
- GET /api/events/:id on mount

*Child Components:*
- EventDetailCard
- RegistrationModal
- LoadingSpinner

---

#### PaymentPage.jsx
*Purpose:* Payment form for paid event registrations  
*Location:* src/pages/PaymentPage.jsx

*Props:*
- None (gets registrationId from URL params)

*State:*
- cardNumber (string)
- expiryDate (string)
- cvv (string)
- cardholderName (string)
- loading (boolean)
- error (string)

*API Calls:*
- POST /api/payments

*Validation:*
- Card number: 16 digits
- Expiry: MM/YY format, not expired
- CVV: 3 digits

---

#### PaymentSuccessPage.jsx
*Purpose:* Confirmation page after successful payment  
*Location:* src/pages/PaymentSuccessPage.jsx

*Features:*
- Shows success message
- Displays ticket information
- Provides download ticket button

---

#### MyEventsPage.jsx
*Purpose:* Show all user's registered events  
*Location:* src/pages/MyEventsPage.jsx

*Props:*
- None (gets userId from auth context)

*State:*
- registrations (array) - User's registrations
- loading (boolean)
- filter (string) - 'all', 'upcoming', 'past'

*API Calls:*
- GET /api/users/:userId/registrations

*Child Components:*
- MyEventCard (multiple)
- LoadingSpinner
  
---

### Reusable Components

#### RegistrationModal.jsx
*Purpose:* Popup to confirm event registration  
*Location:* src/components/RegistrationModal.jsx

*Props:*
- isOpen (boolean) - Controls visibility
- onClose (function) - Called when modal closes
- onConfirm (function) - Called when user confirms
- eventName (string) - Event being registered for
- price (number) - Event price

*Usage:*
jsx
<RegistrationModal
  isOpen={showModal}
  onClose={() => setShowModal(false)}
  onConfirm={handleRegister}
  eventName="Tech Conference 2025"
  price={50.00}
/>

---

#### PaymentForm.jsx
*Purpose:* Credit card input form  
*Location:* src/components/PaymentForm.jsx

*Props:*
- onSubmit (function) - Called with payment data
- amount (number) - Amount to pay
- loading (boolean) - Shows loading state

*Features:*
- Card validation
- Format card number with spaces
- Detect card type (Visa, Mastercard, etc.)

---

#### MyEventCard.jsx
*Purpose:* Single event card in My Events list  
*Location:* src/components/MyEventCard.jsx

*Props:*
- registration (object) - Registration details
- onCancel (function) - Called when cancel clicked
- onDownload (function) - Called when download clicked

*Features:*
- Shows event details
- Status badge (confirmed, pending, cancelled)
- Action buttons

---

#### Ticket.jsx
*Purpose:* Ticket display component  
*Location:* src/components/Ticket.jsx

*Props:*
- ticket (object) - Ticket information
  - ticketCode
  - eventName
  - eventDate
  - userName
  - location

*Features:*
- Ticket-style design
- Downloadable
- Printable format

---

#### StatusBadge.jsx
*Purpose:* Show registration status with color  
*Location:* src/components/StatusBadge.jsx

*Props:*
- status (string) - 'confirmed', 'pending', 'cancelled'

*Renders:*
- Green badge for confirmed
- Yellow badge for pending
- Red badge for cancelled

---

#### LoadingSpinner.jsx
*Purpose:* Loading animation  
*Location:* src/components/LoadingSpinner.jsx

*Props:*
- size (string) - 'small', 'medium', 'large'
- message (string) - Optional loading text

*Usage:*
jsx
<LoadingSpinner size="large" message="Processing payment..." />

---

## Component Hierarchy - Sprint 2

App
├── EventDetailsPage
│   ├── EventDetailCard
│   ├── RegistrationModal
│   └── LoadingSpinner
├── PaymentPage
│   ├── PaymentForm
│   ├── PaymentSummary
│   └── LoadingSpinner
├── PaymentSuccessPage
│   └── Ticket
└── MyEventsPage
    ├── MyEventCard (x multiple)
    ├── StatusBadge
    └── LoadingSpinner

---

## Styling Notes

All Sprint 2 components use:
- Tailwind CSS utility classes
- Consistent color scheme
- Responsive design
- Smooth animations
- Hover effects

---

*Updated:* November 26, 2025 - Sprint 2

---

## Components Implemented in Sprint 3
## Public Pages

**Home Page** - Landing page with welcome message
**Register Page** - User registration form with password strength indicator
**Login Page** - Authentication form (supports admin and regular users)
**Event Page** - Browse events with search and filter
**Event Details Page** - Full event information with register button
**Payment Page** - Payment form for paid events
**Ticket Page** - Confirmation and digital ticket display

---

### Admin Pages (Admin only)

**Admin Dashboard** - Statistics and quick actions
**Create Event Page** - Form to create new events
**Manage Events Page** - Table of all events with edit/delete options
**View Attendees Page** - List of registered users per event

---

## Modal Components
**Edit Event Modal** - Popup form to edit existing events
**Delete Confirmation Modal** - Warning before deleting events
---

## Reusable UI Elements

### Navigation Bar
- Logo
- Navigation buttons (Home, Events)
- User info section
- Admin button (for admin users)

### Alert Messages
- Success alerts (green)
- Error alerts (red)
- Info alerts (blue)

### Buttons
- Primary (purple gradient)
- Secondary (gray with purple border)
- Success (green)
- Danger (red)
- Warning (orange)

### Form Elements
- Form groups with labels
- Input fields with icons
- Password toggles
- Dropdowns
- Textareas
- Date/time pickers

### Event Cards
- Icon background
- Category badge
- Title and details
- Price display
- Seat availability
- View Details button

### Statistics Cards
- Large number display
- Label below
- Gradient background

### Tables
- Header row
- Data rows with hover effect
- Action buttons
- Responsive scroll

---

## State Management

### Global Variables
let currentUser = null;
let currentEvent = null;
let currentEventToDelete = null;
let events = [];

### LocalStorage
localStorage - users
localStorage - events
localStorage - tickets
localStorage - currentUser

### Page Visibility
Controlled by .active class on .page divs

---

## Component Interactions

### Event Registration Flow
1. Events Page → View Details
2. Event Details → Register button
3. Payment Page (if paid)
4. Ticket Page → Confirmation

### Admin Event Management Flow
1. Admin Dashboard → Create Event
2. Create Event Form → Submit
3. Manage Events → Show new event
4. Edit/Delete as needed

---

## Access Control

### Public (No login required)
- Home, Register, Login, Events, Event Details

### Authenticated Users
- Payment, Ticket, Logout

### Admin Only
- All admin pages and functions

---

## Responsive Design

**Breakpoint:** 768px

**Mobile changes:**
- Single column layouts
- Stacked forms
- Scrollable tables
- Simplified navigation

---

## Summary

**Total Pages:** 11 (7 public + 4 admin)

**Modals:** 2

**Reusable Elements:** Nav, Alerts, Buttons, Forms, Cards, Tables

**Last Updated:** Sprint 3 - November 30, 2025











