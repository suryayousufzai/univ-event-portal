# Sprint 1 - Frontend Work Summary

**Dev:** Muneera Aman  
**Dates:** Nov 15-22, 2025

Alright so here's everything I built for the frontend this sprint. Got all the main pages done and they're actually working now!

---

## What I Completed

### Registration Page

Built the complete sign-up page with all the features we needed:

**Form Fields:**
- Full name input with a user icon
- Email address field (validates format)
- Password field with show/hide toggle (that eye icon thing)
- Confirm password field
- Optional student ID field

**Cool Features I Added:**
- Real-time password strength indicator - shows "Weak", "Medium", or "Strong" as you type
  - Weak: less than 6 characters (red)
  - Medium: 6-10 characters without uppercase (yellow)
  - Strong: 10+ characters with uppercase (green)
- Password visibility toggle using the Eye/EyeOff icons
- Form validation that checks everything before submitting
- Success message that pops up and bounces when registration works
- Auto-redirect to login page after 2 seconds
- Loading spinner while processing

**Styling:**
- Purple and pink gradient color scheme
- Clean white card with shadow
- Icons on the left side of each input field
- Smooth transitions and hover effects
- Fully responsive design

The password strength thing was actually pretty fun to implement. It updates live as the user types and gives visual feedback with colors.

**Screenshot:** See screenshots/registration-page.png

---

### Login Page

Much simpler than registration, but still has everything needed:

**Form Fields:**
- Email address input
- Password input
- Both have icons (Mail and Lock from lucide-react)

**Features:**
- Form validation (can't submit empty fields)
- Loading state with spinner when logging in
- "Welcome Back" header to make it friendly
- Same purple/pink gradient button style
- Smooth focus effects on inputs

After successful login, it redirects to the events page. Pretty straightforward implementation.

**Screenshot:** Check out screenshots/login-page.png

---

### Events List Page

This is the main page where users browse events. It's actually pretty feature-rich:

**Search & Filter Section:**
- Search bar with magnifying glass icon - searches event titles in real-time
- Category filter dropdown (All Categories, Workshop, Seminar, Conference)
- Shows count of filtered results (like "Showing 3 of 10 events")
- Both filters work together - can search AND filter by category at the same time

**Event Display:**
- Events shown in responsive grid layout:
  - 1 column on mobile
  - 2 columns on tablets
  - 3 columns on desktop
- Each event card has:
  - Colorful gradient header with emoji icon
  - Category badge (purple pill shape)
  - Event title
  - Date with calendar icon
  - Location with map pin icon
  - Price with dollar icon (shows "Free" in green if $0)
  - "View Details" button
- Cards have hover effect - lifts up slightly and shadow gets bigger
- Empty state message if no events match the search/filter

**Sample Events I Added:**
Created 10 diverse test events:
1. Web Development Workshop (free)
2. Tech Conference 2025 ($50)
3. AI & Machine Learning Seminar ($25)
4. Entrepreneurship Bootcamp (free)
5. Cybersecurity Workshop ($30)
6. Data Science Summit ($75)
7. Design Thinking Workshop (free)
8. Blockchain Technology Seminar ($40)
9. Cloud Computing Conference ($60)
10. Mobile App Development Workshop (free)

Good mix of free and paid, different categories, different dates.

**Screenshot:** screenshots/events-list.png

---

## React Components Structure

Here's how I organized the code:

**Main Component:** MuneeraFrontendDemo
- Manages all state and page navigation
- Handles form submissions
- Contains all three pages (register, login, events)

**State Management:**
Using React useState hooks for:
- `currentPage` - tracks which page to show (register/login/events)
- `formData` - stores registration form fields
- `loginData` - stores login form fields
- `loading` - shows loading spinners during submissions
- `showSuccess` - controls success message display
- `searchTerm` - for event search functionality
- `categoryFilter` - for category filtering
- `showPassword` - toggles password visibility

**Helper Functions:**
- `getPasswordStrength()` - calculates password strength and returns color/text
- `handleRegister()` - processes registration (mock submission with timeout)
- `handleLogin()` - processes login (mock submission with timeout)
- `filteredEvents` - filters events based on search and category

---

## Navigation System

Added a sticky navigation bar at the top with:
- University Events logo with graduation cap emoji
- Three nav buttons: Register, Login, Events
- Active page gets purple background, inactive get gray
- Smooth transitions between pages
- No page reloads, everything is client-side navigation

---

## Styling Approach

Used **Tailwind CSS** exclusively. Here's my color palette:

**Primary Colors:**
- Purple shades: purple-50, purple-100, purple-400, purple-500, purple-600, purple-700
- Pink shades: pink-50, pink-400, pink-600, pink-700
- Gradients: purple-to-pink for buttons and headers

**UI Elements:**
- White cards with rounded corners (`rounded-xl`, `rounded-2xl`)
- Shadow effects for depth (`shadow-md`, `shadow-lg`, `shadow-xl`)
- Gray tones for text hierarchy
- Green for success states and free events
- Red/yellow/green for password strength

**Responsive Design:**
- Mobile-first approach
- Breakpoints: `md:` for tablets, `lg:` for desktop
- Grid system for events layout
- Flexible padding and spacing

**Animations:**
- Hover effects with `transform hover:-translate-y-1`
- Loading spinners with `animate-spin`
- Success message with `animate-bounce`
- Smooth transitions on all interactive elements

---

## Icons Used

Using **lucide-react** icon library throughout:
- Search - for search bar
- Filter - for filter dropdown
- Calendar - for event dates
- MapPin - for locations
- DollarSign - for prices
- User - for name field
- Mail - for email fields
- Lock - for password fields
- CheckCircle - for success message
- Loader - for loading states
- Eye/EyeOff - for password visibility toggle

These icons make the UI way more intuitive and professional looking.

---

## Form Validation Implementation

**Registration Form:**
- All fields required except student ID
- Email must be valid format (browser validation)
- Password must match confirm password
- Shows real-time password strength
- Prevents submission until all validations pass

**Login Form:**
- Both email and password required
- Basic format validation
- Shows loading state during submission

Validation happens on the frontend but in a real app would also validate on backend.

---

## Mock API Integration

Since this is a demo, I'm simulating API calls with `setTimeout`:

**Registration Flow:**
1. User submits form
2. Loading state activates (shows spinner)
3. Wait 1 second (simulating network request)
4. Show success message with bounce animation
5. Wait 2 more seconds
6. Redirect to login page

**Login Flow:**
1. User submits form
2. Loading state activates
3. Wait 1 second
4. Redirect to events page

In Sprint 2 when we connect to Fariba's backend, I'll replace these with actual API calls to:
- POST /api/register
- POST /api/login
- GET /api/events

---

## Search and Filter Logic

The filtering is actually pretty smart:

```javascript
const filteredEvents = events.filter(event => {
  const matchesSearch = event.title.toLowerCase().includes(searchTerm.toLowerCase());
  const matchesCategory = categoryFilter === 'all' || event.category === categoryFilter;
  return matchesSearch && matchesCategory;
});
```

- Case-insensitive search on event titles
- Category filter works with "all" option
- Both conditions must be true (AND logic)
- Results update immediately as user types or changes filter
- Shows count of filtered vs total events

---

## Responsive Behavior

**Mobile (< 768px):**
- Single column layout for everything
- Full-width cards and forms
- Stack search and filter vertically
- Reduced padding and text sizes

**Tablet (768px - 1024px):**
- Two column grid for events
- Side-by-side search and filter
- Moderate spacing

**Desktop (> 1024px):**
- Three column grid for events
- Generous spacing and larger text
- Maximum width container (max-w-7xl)

---

## Status Indicator

Added a floating badge in the bottom-right corner:
- Green background
- "Sprint 1 Complete - 100% Functional" text
- Fixed position so it stays visible while scrolling
- Has shadow for visibility

This is just for demo purposes to show the sprint is done.

---

## Problems I Ran Into

### Password Strength Logic
Initially my password strength function was too simple. Made it more robust by checking:
- Length thresholds (6, 10 characters)
- Uppercase letter presence
- Returns both text and color for styling

### Filter State Management
Had to make sure both search and filter work together properly. The key was using AND logic in the filter function so both conditions are checked.

### Form State After Success
After successful registration, needed to clear the form state, but also keep it intact during the success message animation. Used setTimeout to manage the timing properly.

### Responsive Grid
Getting the grid to look good on all screen sizes took some tweaking. Settled on:
- `grid-cols-1 md:grid-cols-2 lg:grid-cols-3`
- Consistent gap spacing
- Proper card widths

---

## Next Sprint Plans

For Sprint 2 I'll be working on:

1. **Event Details Page**
   - Full event description
   - Larger image/banner
   - Registration button
   - Seat availability counter

2. **Event Registration Flow**
   - Registration form
   - Payment integration (if needed)
   - Confirmation screen
   - Ticket display

3. **Backend Integration**
   - Replace mock API calls with real axios requests
   - Handle JWT token storage
   - Add proper error handling
   - Show API error messages to users

4. **User Profile Page** (if time allows)
   - Display user info
   - Show registered events
   - Ability to cancel registrations

---

## Technical Notes

**Dependencies Used:**
- React (with hooks)
- lucide-react (for icons)
- Tailwind CSS (for styling)

**Component Structure:**
- Single file component (MuneeraFrontendDemo.jsx)
- Functional component with hooks
- Client-side routing using state

**Code Quality:**
- Organized state management
- Reusable styling patterns
- Clean JSX structure
- Commented sections for clarity

**Performance:**
- Efficient filtering with array methods
- No unnecessary re-renders
- Smooth animations with CSS

---

## Files to Add to Repo

**Screenshots Folder:**
Need to add these screenshots:
- registration-page.png - full registration form with all fields
- login-page.png - login form with welcome message
- events-list.png - grid of events with search/filter

---

**Status:** Sprint 1 Complete  
**Code Status:** Fully functional demo ready  
**Next Steps:** Connect to backend APIs in Sprint 2
