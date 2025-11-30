# Product Owner Report - Sprint 3

Written by: Marwa Paiman (Product Owner)
Date: November 30, 2025
Sprint: Sprint 3 (November 27-30, 2025)

---

## What We Planned for Sprint 3

The goal for Sprint 3 was to build the admin side of our event registration portal. Before this sprint, we only had the student side working - students could browse events and register. But we had no way for university staff to create or manage events through the website. They would have to ask a developer to add events directly to the database, which is not practical.

So for Sprint 3, we needed to build a complete admin panel where staff can:
- Log in as an admin
- Create new events
- Edit existing events
- Delete cancelled events
- See who registered for each event

We planned 4 user stories totaling 21 story points.

---

## What We Actually Delivered

The team delivered everything we planned. All 4 user stories are complete and working.

### User Story 1: Admin Login and Dashboard (3 points)

What we got:
- A login page specifically for admin users
- The system checks if the person logging in has admin role in the database
- After login, admins see a dashboard with a menu
- The menu has three options: Create Event, Manage Events, View Attendees
- Regular students cannot access these admin pages (they get an error if they try)

My feedback:
This works really well. The login is secure and the dashboard is clean and easy to navigate. I tested it with both admin and regular user accounts. Admins can get in, regular users cannot. Perfect.

Status: Accepted

---

### User Story 2: Create Events (8 points)

What we got:
- A form where admins can create new events
- The form has all the fields we need: title, description, category, date, time, location, capacity, and price
- The form checks that required fields are filled in
- It also checks that the date is in the future (you cannot create an event in the past)
- It checks that capacity is a positive number
- When you click Create Event, it saves to the database
- You see a success message
- The new event appears in the events list immediately

My feedback:
This is exactly what we needed. I created several test events myself. The form is intuitive and the validation catches mistakes. For example, I tried to create an event with a date in the past and it stopped me with a clear error message. I tried to put a negative number for capacity and again it showed an error. This prevents bad data from getting into the system.

The form looks professional and is easy to use even for staff who are not tech-savvy.

Status: Accepted

---

### User Story 3: Edit and Delete Events (5 points)

What we got:
- A page called Manage Events that shows all events in a table
- Each event has an Edit button and a Delete button
- When you click Edit, a form opens with the current event information already filled in
- You can change any field and save
- When you click Delete, a warning pops up asking "Are you sure? This will delete the event and all registrations"
- If you confirm, the event is deleted from the database
- The list updates automatically after editing or deleting

My feedback:
The edit feature works smoothly. I tested editing event titles, dates, and capacities. Everything saves correctly.

The delete confirmation is a very important safety feature. I am glad the team added the warning about deleting registrations too, because that is a serious action. The warning makes it clear what will happen.

I tested deleting an event that had 3 registrations. The event was removed and when I checked the database, the registrations were also removed. This is correct behavior - we do not want orphaned registrations for events that no longer exist.

Status: Accepted

---

### User Story 4: View Attendees (5 points)

What we got:
- Each event in the Manage Events page now has a "View Attendees" button
- When you click it, you see a list of everyone who registered
- The list shows: name, email, registration date, and payment status
- At the top it shows the total count like "15 people registered"
- There is an "Export as CSV" button
- If you click it, it downloads a CSV file with all the attendee data
- If nobody registered yet, it shows a message "No one has registered for this event yet"

My feedback:
This is very useful. As a Product Owner, I can now see which events are popular and which are not. The CSV export is excellent because staff can download the list and send emails to attendees, or print attendance sheets.

I tested the CSV export and opened it in Excel. All the data is there and properly formatted with headers.

The empty state message is a nice touch for events with no registrations.

Status: Accepted

---

## Overall Sprint Assessment

Sprint 3 was excellent. The team delivered all planned features on time with high quality.

### What Went Well

1. Complete Delivery
The team completed all 21 story points. This is our highest velocity yet (Sprint 1 was 16 points, Sprint 2 was 19 points).

2. Quality
I did not find any bugs. Everything works as expected. Gita's testing was thorough.

3. User Experience
The admin panel is professional and easy to use. I could navigate it without any training. This is important because university staff are not all technical people.

4. Security
The role-based access control works correctly. Regular students cannot access admin features. This was a requirement and the team implemented it properly.

5. Practical Features
The CSV export and delete confirmation are thoughtful additions that will be very useful in real use.

6. Team Communication
The team communicated well throughout the sprint. When I had questions, they responded quickly. The daily scrum meetings were efficient.

### What Could Be Better

These are not problems with what was delivered, but ideas for future improvements:

1. Search and Filter
Right now the Manage Events page shows all events in one table. If we have 100 events, it will be hard to find a specific one. In the future, we should add search and filter options.

2. Email Notifications
It would be helpful if admins could send email notifications to all attendees directly from the View Attendees page. Right now they have to export the CSV and use their own email.

3. Event Analytics
It would be nice to see statistics like how many people viewed an event versus how many registered. This would help us understand event popularity.

4. Bulk Actions
If we need to delete multiple events at once (like old events from last year), right now we have to delete them one by one. Bulk delete would be helpful.

But again, these are future enhancements, not problems with Sprint 3.

---

## Testing and Quality

Gita tested all features thoroughly. Her test report shows:
- 9 test cases executed
- 9 test cases passed
- 0 bugs found

I also did my own testing by using the features as an actual admin would. Everything worked correctly.

The features work on different browsers (I tested Chrome and Safari) and on mobile devices too.

---

## Business Value Delivered

Sprint 3 completes the core functionality of our event registration portal.

Before Sprint 3, we had:
- Students can browse events
- Students can register for events
- Students can pay for tickets
- Students can see their registrations in their dashboard

After Sprint 3, we now also have:
- Staff can create events
- Staff can manage events (edit/delete)
- Staff can see who registered
- Staff can export attendee lists

This means the portal is now a complete system. We do not need developers to manually add events to the database anymore. Staff can manage everything themselves through the website.

This is a major milestone for the project.

---

## Acceptance Status

All 4 user stories are ACCEPTED.

The Sprint 3 goal is achieved: Enable administrators to create, manage, and monitor events.

---

## Feedback to the Team

I want to thank the team for their excellent work in Sprint 3.

Fariba built solid backend APIs with good validation and error handling.

Muneera created a clean and intuitive user interface that is easy to use.

Gita's thorough testing ensured zero bugs made it to production.

Surya kept the team organized and the sprint running smoothly.

This was our best sprint yet in terms of velocity, quality, and team collaboration.

---

## Next Steps

Now that the core features are complete, we can focus on enhancements and polish for Sprint 4.

Potential items for Sprint 4:
- Add search and filter to Manage Events page
- Add email notification feature
- Add event analytics and reports
- Performance testing with large datasets
- Implement the action items from the Sprint 3 retrospective (automated testing, API documentation, activity logging)

I will work with Surya to prioritize these items for Sprint 4 planning.

---

## Product Backlog Status

After Sprint 3, our MVP (Minimum Viable Product) is essentially complete. We have all the core features needed for the portal to function:

Completed:
- User registration and authentication
- Event browsing and search
- Event registration
- Payment processing (Stripe integration)
- User dashboard
- Admin authentication
- Event management (CRUD operations)
- Attendee management

Remaining (enhancements):
- Advanced search and filtering
- Email notifications
- Analytics and reporting
- User profile management
- Event categories management
- Performance optimizations

The team should be proud. We built a working event registration system in just 3 sprints.

---

## Metrics Summary

Sprint 3 Performance:
- Planned Story Points: 21
- Delivered Story Points: 21
- Completion Rate: 100%
- Defects Found: 0
- Team Velocity: 21 points (highest so far)

Team velocity trend:
- Sprint 1: 16 points
- Sprint 2: 19 points
- Sprint 3: 21 points
- Average velocity: 18.7 points

This upward trend shows the team is getting more efficient and working well together.

---

## Final Thoughts

Sprint 3 was a success by every measure. The team delivered everything planned, with high quality, on time, and with no major issues.

The admin functionality makes the portal truly useful for our university. Staff can now manage events independently without technical help.

I am satisfied with the Sprint 3 deliverables and approve them for deployment to production (after final UAT).

Looking forward to Sprint 4 where we will add the finishing touches and polish.

---

Marwa Paiman
Product Owner
November 30, 2025
