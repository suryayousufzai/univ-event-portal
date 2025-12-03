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

# Frontend Components Structure - Sprint 3

*Project:* University Event Registration Portal  
*Developer:* Muneera Aman (Frontend Lead)  
*Sprint:* Sprint 3  
*Date:* November 30, 2025

---

## Overview
This document describes the admin panel components added in Sprint 3. All these components are admin-only and require admin authentication to access.

---

## Sprint 3 - Admin Components

### Page Components

#### AdminDashboard.jsx
*Purpose:* Main admin dashboard with statistics and quick actions  
*Location:* src/pages/admin/AdminDashboard.jsx

*Props:*
- None (gets data from API)

*State:*
- totalEvents (number)
- totalRegistrations (number)
- activeEvents (number)
- loading (boolean)

*API Calls:*
- GET /api/admin/dashboard on mount

*Features:*
- Three stat cards showing counts
- Two action cards (Create Event, Manage Events)
- Real-time data updates
- Responsive grid layout

*Usage:*
jsx
<AdminDashboard />

---

#### CreateEventPage.jsx
*Purpose:* Form to create new events  
*Location:* src/pages/admin/CreateEventPage.jsx

*Props:*
- None

*State:*
- title (string)
- description (string)
- category (string)
- icon (string)
- date (string)
- time (string)
- location (string)
- capacity (number)
- price (number)
- error (string)
- loading (boolean)

*API Calls:*
- POST /api/admin/events

*Validation:*
- All required fields must be filled
- Date must be in future
- Capacity must be positive number
- Price cannot be negative

*Form Layout:*
- Two-column grid for date/time and capacity/price
- Single column for title, description, location
- Dropdowns for category and icon

---

#### ManageEventsPage.jsx
*Purpose:* Table view of all events with admin actions  
*Location:* src/pages/admin/ManageEventsPage.jsx

*Props:*
- None

*State:*
- events (array)
- loading (boolean)
- showEditModal (boolean)
- showDeleteModal (boolean)
- selectedEvent (object)

*API Calls:*
- GET /api/admin/events on mount
- PUT /api/admin/events/:id for edit
- DELETE /api/admin/events/:id for delete

*Child Components:*
- EventsTable
- EditEventModal
- DeleteConfirmModal
- LoadingSpinner

*Features:*
- Search and filter (planned for future)
- Action buttons per row
- Empty state when no events

---

#### ViewAttendeesPage.jsx
*Purpose:* Show all registrations for a specific event  
*Location:* src/pages/admin/ViewAttendeesPage.jsx

*Props:*
- None (gets eventId from URL params)

*State:*
- event (object)
- attendees (array)
- loading (boolean)

*API Calls:*
- GET /api/admin/events/:id/attendees on mount
- GET /api/admin/events/:id/attendees/export for CSV

*Child Components:*
- AttendeesTable
- ExportButton
- LoadingSpinner

*Features:*
- Display attendee details in table
- Color-coded payment status
- CSV export button
- Shows empty state if no attendees
- Back button to Manage Events

---

### Reusable Components

#### StatCard.jsx
*Purpose:* Display single statistic on dashboard  
*Location:* src/components/admin/StatCard.jsx

*Props:*
- label (string) - Stat description
- value (number) - Stat number
- icon (string) - Optional emoji or icon

*Usage:*
jsx
<StatCard 
  label="Total Events" 
  value={6} 
  icon="📅"
/>

*Styling:*
- Purple gradient background
- Large number (3rem font)
- White text
- Rounded corners with shadow

---

#### ActionCard.jsx
*Purpose:* Clickable card for admin actions  
*Location:* src/components/admin/ActionCard.jsx

*Props:*
- title (string) - Card title
- icon (string) - Emoji icon
- onClick (function) - Click handler

*Features:*
- Hover effect (lifts up, changes border)
- Centered text and icon
- Responsive sizing

*Usage:*
jsx
<ActionCard 
  title="Create Event" 
  icon="➕"
  onClick={() => navigate('/admin/create')}
/>

---

#### EventsTable.jsx
*Purpose:* Table displaying all events with actions  
*Location:* src/components/admin/EventsTable.jsx

*Props:*
- events (array) - Events to display
- onEdit (function) - Called with eventId
- onDelete (function) - Called with eventId
- onViewAttendees (function) - Called with eventId

*Features:*
- Responsive table layout
- Scrolls horizontally on mobile
- Action buttons per row
- Shows capacity and availability
- Price formatting (Free or $X.XX)

*Columns:*
- Title
- Date
- Location
- Capacity
- Available
- Price
- Actions (3 buttons)

---

#### AttendeesTable.jsx
*Purpose:* Table showing event registrations  
*Location:* src/components/admin/AttendeesTable.jsx

*Props:*
- attendees (array) - Registration records
- eventTitle (string) - Event name

*Features:*
- Color-coded payment status
- Monospace font for ticket codes
- Formatted registration dates

*Columns:*
- Name
- Email
- Registration Date
- Payment Status
- Ticket Code

---

#### EditEventModal.jsx
*Purpose:* Popup modal to edit existing event  
*Location:* src/components/admin/EditEventModal.jsx

*Props:*
- isOpen (boolean) - Controls visibility
- event (object) - Current event data
- onClose (function) - Close handler
- onSave (function) - Save handler with updated data

*State:*
- All event fields (same as CreateEventPage)
- loading (boolean)
- error (string)

*Features:*
- Pre-fills form with current data
- Same validation as create
- Close button in header
- Save and Cancel buttons in footer

*Usage:*
jsx
<EditEventModal
  isOpen={showModal}
  event={selectedEvent}
  onClose={() => setShowModal(false)}
  onSave={handleUpdate}
/>

---

#### DeleteConfirmModal.jsx
*Purpose:* Confirmation dialog before deleting event  
*Location:* src/components/admin/DeleteConfirmModal.jsx

*Props:*
- isOpen (boolean)
- eventTitle (string)
- onConfirm (function) - Called when user confirms
- onCancel (function) - Called when user cancels

*Features:*
- Warning icon
- Clear warning message about cascade delete
- Red delete button
- Gray cancel button

*Usage:*
jsx
<DeleteConfirmModal
  isOpen={showDeleteModal}
  eventTitle="AI Workshop"
  onConfirm={handleDelete}
  onCancel={() => setShowDeleteModal(false)}
/>

---

#### ExportButton.jsx
*Purpose:* Button to export attendees to CSV  
*Location:* src/components/admin/ExportButton.jsx

*Props:*
- eventId (number)
- eventTitle (string)
- disabled (boolean) - Disabled if no attendees

*Features:*
- Downloads CSV file
- Shows loading state during export
- Green success color

*API Call:*
javascript
GET /api/admin/events/:eventId/attendees/export

---

#### EmptyState.jsx
*Purpose:* Message shown when no data to display  
*Location:* src/components/admin/EmptyState.jsx

*Props:*
- icon (string) - Emoji icon
- title (string) - Main message
- message (string) - Detailed message
- actionButton (component) - Optional button to show

*Usage:*
jsx
<EmptyState
  icon="📅"
  title="No Events Yet"
  message="Create your first event to get started."
  actionButton={<Button text="Create Event" onClick={handleCreate} />}
/>

---

#### AdminHeader.jsx
*Purpose:* Page header for admin pages  
*Location:* src/components/admin/AdminHeader.jsx

*Props:*
- title (string) - Page title
- actions (component) - Optional action buttons

*Features:*
- Purple bottom border
- Flex layout for title and actions
- Consistent spacing

*Usage:*
jsx
<AdminHeader
  title="Manage Events"
  actions={
    <>
      <Button text="Create Event" onClick={handleCreate} />
      <Button text="Dashboard" onClick={goToDashboard} />
    </>
  }
/>

---

## Component Hierarchy - Sprint 3

App
├── AdminDashboard
│   ├── StatCard (x3)
│   ├── ActionCard (x2)
│   └── LoadingSpinner
├── CreateEventPage
│   ├── AdminHeader
│   └── EventForm (new)
├── ManageEventsPage
│   ├── AdminHeader
│   ├── EventsTable
│   ├── EditEventModal
│   ├── DeleteConfirmModal
│   └── EmptyState
└── ViewAttendeesPage
    ├── AdminHeader
    ├── AttendeesTable
    ├── ExportButton
    ├── EmptyState
    └── LoadingSpinner

---

## Routing Updates

Added admin routes:
javascript
<Routes>
  {/* Previous routes */}
  
  {/* Admin routes - protected */}
  <Route path="/admin" element={<AdminLayout />}>
    <Route path="dashboard" element={<AdminDashboard />} />
    <Route path="create" element={<CreateEventPage />} />
    <Route path="manage" element={<ManageEventsPage />} />
    <Route path="attendees/:eventId" element={<ViewAttendeesPage />} />
  </Route>
</Routes>

---

## Protected Routes

Created ProtectedRoute component to check admin role:
jsx
<ProtectedRoute requireAdmin={true}>
  <AdminDashboard />
</ProtectedRoute>

If user is not admin, redirect to home page.

---

## New Utility Functions

#### dateFormatter.js
*Purpose:* Convert dates between formats

*Functions:*
- formatDate(dateStr) - "2025-12-15" to "December 15, 2025"
- formatTime(timeStr) - "14:00" to "2:00 PM"
- reverseFormatDate(dateStr) - "December 15, 2025" to "2025-12-15"
- reverseFormatTime(timeStr) - "2:00 PM" to "14:00"

Used in edit modal to convert dates for input fields.

---

#### csvExport.js
*Purpose:* Generate and download CSV files

*Functions:*
- exportToCSV(data, filename) - Creates CSV and triggers download

Used by ExportButton component.

---

## State Management Updates

Added admin context:
javascript
const AdminContext = createContext();

Provides:
- isAdmin (boolean)
- adminData (object)
- checkAdminAccess (function)

Used by all admin components to verify access.

---

## Styling Approach

Admin components use:
- Tailwind CSS utility classes
- Consistent purple theme (#667eea, #764ba2)
- Card-based layouts
- Hover effects on interactive elements
- Responsive tables with horizontal scroll
- Modal overlays with dark background

New classes:
- .admin-table - Table styling
- .admin-card - Card container
- .stat-value - Large statistic numbers
- .action-btn - Button groups in tables

---

## Form Validation

All admin forms validate:
- Required fields not empty
- Date is in future
- Capacity is positive
- Price is non-negative
- Email format (for notifications in future)

Validation happens:
1. On blur (when user leaves field)
2. On submit (before API call)

Shows error messages under each field.

---

## API Integration

All admin API calls include:
- Authorization header with JWT token
- Error handling for 401 (unauthorized) and 403 (forbidden)
- Loading states during requests
- Success messages after mutations

Example:
javascript
const response = await fetch('/api/admin/events', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': `Bearer ${token}`
  },
  body: JSON.stringify(eventData)
});

---

## Error Handling

Admin components handle:
- Network errors
- Validation errors
- Permission errors (401/403)
- Not found errors (404)

Shows user-friendly messages:
- "Connection error. Please try again."
- "You don't have permission to access this page."
- "Event not found."

---

## Performance Considerations

For large event lists:
- Table pagination (planned for future)
- Search debouncing (planned for future)
- Lazy loading of attendee data

Currently handles up to 100 events smoothly.

---

## Testing

Each admin component tested for:
- Renders with correct data
- Form validation works
- API calls made correctly
- Error messages display
- Modal open/close works
- CSV export downloads file
- Responsive on mobile

---

## Challenges Faced

1. Modal centering on all screen sizes - solved with flexbox
2. Date format conversion for edit - created helper functions
3. Table responsive on mobile - added horizontal scroll
4. CSV special characters - wrapped values in quotes

---

## Time Spent

- AdminDashboard: 2 hours
- CreateEventPage: 2 hours
- ManageEventsPage: 2 hours
- ViewAttendeesPage: 1.5 hours
- Modals: 1.5 hours
- Styling and polish: 2 hours
- Bug fixes: 1 hour
- Testing: 1.5 hours

Total: 14 hours

---

## Future Improvements

If we had more time:
- Add search and filters on Manage Events
- Pagination for large event lists
- Drag and drop event images
- Rich text editor for description
- Bulk actions (delete multiple)
- Export events to CSV
- Analytics charts on dashboard
- Event duplication feature

---

*Prepared by:* Muneera Aman (Frontend Lead Developer)  
*Last Updated:* November 30, 2025

---

# Frontend Components Structure - Sprint 4

---

## Overview

Sprint 4 was our shortest sprint - just 2 days. We added three new features to the admin panel: export buttons for PDF, a reports dashboard, and email notification messages.

Most of the work was on the backend. My job was to create the UI and connect it to Fariba's APIs.

---

## Sprint 4 - New Components

### Page Components

#### ReportsPage.jsx
*Purpose:* Dashboard showing portal statistics  
*Location:* src/pages/admin/ReportsPage.jsx

*Props:*
- None (gets data from API)

*State:*
- totalEvents (number)
- totalRegistrations (number)
- totalRevenue (number)
- activeUsers (number)
- loading (boolean)

*API Calls:*
javascript
GET /api/admin/reports


*Features:*
- Four colorful stat cards
- Auto-refresh button
- Loading state while fetching data
- Responsive grid layout

*Usage:*
jsx
<ReportsPage />


*Styling:*
- Purple gradient cards
- Large numbers (3rem font size)
- Icons for each stat (📅 📊 💰 👥)
- Hover effect on refresh button

---

### Reusable Components

#### PDFExportButton.jsx
*Purpose:* Button to export attendees as PDF  
*Location:* src/components/admin/PDFExportButton.jsx

*Props:*
- eventId (number) - Event to export
- eventTitle (string) - For filename
- disabled (boolean) - If no attendees

*Features:*
- Red color to match PDF theme
- Loading spinner while generating
- Downloads file automatically
- Shows success message

*Usage:*
jsx
<PDFExportButton 
  eventId={1} 
  eventTitle="Tech Conference"
  disabled={false}
/>


*How it works:*
javascript
function handleExport() {
  setLoading(true);
  window.location.href = `/api/admin/events/${eventId}/attendees/export-pdf`;
  setTimeout(() => {
    setLoading(false);
    showNotification('PDF exported!');
  }, 1000);
}


---

#### EmailNotification.jsx
*Purpose:* Small popup message after registration/payment  
*Location:* src/components/EmailNotification.jsx

*Props:*
- message (string) - Notification text
- type (string) - 'success' | 'error'
- duration (number) - How long to show (default 5000ms)

*Features:*
- Slides in from right
- Auto-dismisses after 5 seconds
- Green for success, red for error
- Smooth fade in/out animation

*Usage:*
jsx
<EmailNotification 
  message="Confirmation email sent to your inbox"
  type="success"
  duration={5000}
/>


*Styling:*
css
.notification {
  position: fixed;
  top: 20px;
  right: 20px;
  background: #10b981;
  color: white;
  padding: 16px 24px;
  border-radius: 8px;
  animation: slideIn 0.3s ease;
}


---

### Updated Components

#### ViewAttendeesPage.jsx (Enhanced)
*What changed:* Added PDF export button next to CSV button

*New features:*
- Two export buttons side by side
- CSV button (green)
- PDF button (red)
- Both buttons disabled if no attendees

*Code added:*
jsx
<div className="export-buttons">
  <CSVExportButton 
    eventId={eventId} 
    eventTitle={event.title}
  />
  <PDFExportButton 
    eventId={eventId} 
    eventTitle={event.title}
  />
</div>


---

#### EventRegistrationFlow (Enhanced)
*What changed:* Added email notification after successful registration

*New features:*
- Shows notification: "Confirmation email sent to your inbox"
- Notification appears after registration completes
- Fades out automatically after 5 seconds

*Code added:*
javascript
// After successful registration
if (response.success) {
  showNotification('Confirmation email sent to your inbox');
  navigate('/my-events');
}


---

#### PaymentSuccessPage (Enhanced)
*What changed:* Added email notification after payment

*New features:*
- Shows notification: "Receipt sent to your email"
- Appears on payment success page load

*Code added:*
javascript
useEffect(() => {
  showNotification('Receipt sent to your email');
}, []);


---

## Component Hierarchy - Sprint 4

App
├── ReportsPage (new)
│   ├── StatCard (x4)
│   ├── RefreshButton
│   └── LoadingSpinner
├── ViewAttendeesPage (updated)
│   ├── CSVExportButton
│   ├── PDFExportButton (new)
│   └── AttendeesTable
├── EventRegistrationFlow (updated)
│   └── EmailNotification (new)
└── PaymentSuccessPage (updated)
    └── EmailNotification (new)

---

## Routing Updates

Added reports route:
javascript
<Route path="/admin/reports" element={<ReportsPage />} />


Updated admin menu to include Reports link.

---

## New Utility Functions

#### formatCurrency.js
*Purpose:* Format numbers as currency

*Function:*
javascript
export function formatCurrency(amount) {
  return '$' + amount.toFixed(2);
}


*Usage:*
jsx
<p>Total Revenue: {formatCurrency(875.50)}</p>
// Displays: Total Revenue: $875.50


---

## Styling Details

### StatCard Styling
css
.stat-card {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 12px;
  padding: 24px;
  color: white;
  box-shadow: 0 4px 12px rgba(102, 126, 234, 0.3);
}

.stat-number {
  font-size: 3rem;
  font-weight: 800;
  line-height: 1;
}


### Export Buttons
css
.btn-csv {
  background: #10b981; /* green */
  color: white;
  margin-right: 10px;
}

.btn-pdf {
  background: #ef4444; /* red */
  color: white;
}


### Notification Animation
css
@keyframes slideIn {
  from {
    transform: translateX(400px);
    opacity: 0;
  }
  to {
    transform: translateX(0);
    opacity: 1;
  }
}


---

## API Integration

### Reports Dashboard
javascript
useEffect(() => {
  fetch('/api/admin/reports')
    .then(response => response.json())
    .then(data => {
      setTotalEvents(data.data.totalEvents);
      setTotalRegistrations(data.data.totalRegistrations);
      setTotalRevenue(data.data.totalRevenue);
      setActiveUsers(data.data.activeUsers);
      setLoading(false);
    });
}, []);


### PDF Export
javascript
function exportPDF() {
  setLoadingPDF(true);
  window.location.href = `/api/admin/events/${eventId}/attendees/export-pdf`;
  setTimeout(() => {
    setLoadingPDF(false);
  }, 1000);
}


### Email Notification (Simulated)
javascript
// After registration
await fetch('/api/events/register', { /* ... */ });
showNotification('Confirmation email sent to your inbox');

// After payment
await fetch('/api/payments', { /* ... */ });
showNotification('Receipt sent to your email');


---

## Responsive Design

All Sprint 4 components work on mobile:

*Reports Page:*
- 4 cards on desktop
- 2 cards per row on tablet
- 1 card per row on mobile

*Export Buttons:*
- Side by side on desktop
- Stack vertically on mobile

*Notifications:*
- Adjust position on small screens
- Smaller padding on mobile

---

## State Management

Used React useState for:
- Loading states (loading, loadingPDF)
- Data (stats, attendees)
- Notification visibility (showNotification)

Simple and clean - no need for complex state management for these features.

---

## Error Handling

All components handle:
- Network errors → Show error message
- Empty data → Show empty state
- Loading states → Show spinner

Example:
javascript
try {
  const response = await fetch('/api/admin/reports');
  if (!response.ok) throw new Error('Failed to load');
  // ... handle success
} catch (error) {
  setError('Failed to load reports. Please try again.');
}


---

## Challenges Faced

1. *PDF Download:* Had to use window.location.href to trigger download
2. *Notification Timing:* Had to time the notification to appear after API success
3. *Refresh Button:* Added loading state so user knows data is refreshing
4. *Export Button Styling:* Made sure CSV and PDF buttons look different but consistent

---

## Time Spent

- Reports page: 3 hours (design + API integration)
- PDF export button: 1 hour
- Email notifications: 1 hour
- Testing and polish: 1 hour
- Bug fixes: 0.5 hours
- Responsive design: 1 hour

*Total: 7.5 hours*

Sprint 4 was lighter for frontend since most work was backend.

---

## What I Learned

- How to trigger file downloads in React
- Managing multiple loading states (CSV + PDF)
- Creating auto-dismiss notifications
- Making stat cards that look professional
- Working with formatted currency

The hardest part was making the notification appear at the right time and position correctly on all screen sizes.

---

## Testing

Tested on:
- ✅ Chrome, Firefox, Safari
- ✅ Desktop, tablet, mobile
- ✅ Different screen sizes
- ✅ Slow network (to test loading states)

All features work smoothly!

---

## Future Improvements

If we had more time:
- Add charts to reports page (line chart for revenue over time)
- Add date range filter for reports
- Add email preview before sending
- Add notification center to see all notifications
- Add option to export multiple events at once

But for a 2-day sprint, we delivered everything we planned!

---

*Prepared by:* Muneera Aman (Frontend Lead)  
*Last Updated:* December 2, 2025  
*Sprint:* Sprint 4 Complete ✅
