# Backend Implementation Summary - Sprint 4

**Developer:** Fariba Mohammadi (Backend Lead)  
**Sprint:** Sprint 4 (December 1-2, 2025)  
**Project:** University Event Registration Portal  
**Date:** December 2, 2025

---

## Overview

Sprint 4 was our shortest sprint - just 2 days. We focused on three features: improving the export functionality we built in Sprint 3, adding a reports dashboard for admins, and implementing email notifications for users.

This sprint was challenging because of the tight timeline, but we managed to deliver everything we committed to.

---

## What I Built in Sprint 4

### 1. Export Enhancements (ENHANCE-001)

In Sprint 3, we built basic CSV export for attendee lists. In Sprint 4, I added PDF export and improved the CSV formatting.

**What I did:**

**CSV Improvements:**
- I went back to the CSV export code from Sprint 3
- Added proper headers row at the top of the file
- Fixed an issue where special characters in names (like accents or apostrophes) were breaking the format
- Wrapped all values in quotes to handle commas in names properly
- Made the filename cleaner: EventName_attendees.csv with spaces replaced by underscores

**PDF Export:**
- Used TCPDF library for PHP (I've used it before, so I knew it would work)
- Created a new endpoint: GET /api/admin/events/:id/attendees/export-pdf
- Built a function that formats the attendee data into a nice table
- Added the event name as a header at the top
- Set up proper column widths so everything fits on one page
- Made the PDF downloadable with filename: EventName_attendees.pdf

**Challenges:**
- TCPDF has a lot of options and I had to figure out which ones to use
- Getting the table to fit properly on the page took some trial and error
- I wanted to add the university logo but ran out of time, so I skipped it

**Time spent:** About 3 hours total

---

### 2. Basic Reports Dashboard (US-015)

Admins needed a way to see overall statistics about how the portal is being used.

**What I did:**

Created a new endpoint: GET /api/admin/reports

This endpoint returns four statistics:
1. Total number of events in the system
2. Total number of registrations across all events
3. Total revenue collected from paid events
4. Number of active users (users who registered for at least one event)

**The SQL queries I wrote:**

```sql
-- Total events
SELECT COUNT(*) FROM events;

-- Total registrations
SELECT COUNT(*) FROM registrations;

-- Total revenue
SELECT SUM(amount) FROM payments WHERE status = 'success';

-- Active users
SELECT COUNT(DISTINCT user_id) FROM registrations;
```

Pretty straightforward queries. I tested each one in phpMyAdmin first to make sure the numbers were correct, then I built the API endpoint.

**Response format:**
```json
{
  "totalEvents": 12,
  "totalRegistrations": 45,
  "totalRevenue": 875.00,
  "activeUsers": 23
}
```

**Challenges:**
- At first I forgot to filter payments by status = 'success', so the revenue included failed payments. Gita caught this during testing.
- I had to decide whether to count cancelled registrations or not. I decided to count them because they're still registrations that happened, even if they were later cancelled.

**Time spent:** About 2 hours

---

### 3. Automated Email Notifications (US-016)

This was the biggest feature of Sprint 4. Users needed to receive emails when they register, pay, or cancel.

**What I did:**

**Email Setup:**
- Used PHPMailer library (it's built into PHP so I didn't have to install anything)
- Set up Gmail SMTP for sending emails
- Created a config file with SMTP settings:
  - Host: smtp.gmail.com
  - Port: 587
  - Username: our test Gmail account
  - Password: app-specific password (not the regular password, for security)
- Tested that emails actually send by sending a test email to myself

**Created 3 Email Templates:**

**Registration Confirmation Email:**
```
Subject: Registration Confirmed for [Event Name]

Hi [User Name],

Thanks for registering for [Event Name]!

Event Details:
- Date: [Event Date]
- Time: [Event Time]
- Location: [Event Location]

Your ticket code: [Ticket Code]

See you there!

University Events Team
```

**Payment Confirmation Email:**
```
Subject: Payment Confirmed for [Event Name]

Hi [User Name],

Your payment for [Event Name] has been processed successfully!

Amount Paid: $[Amount]
Transaction ID: [Transaction ID]
Your ticket code: [Ticket Code]

Event Details:
- Date: [Event Date]
- Time: [Event Time]
- Location: [Event Location]

See you at the event!

University Events Team
```

**Cancellation Email:**
```
Subject: Registration Cancelled for [Event Name]

Hi [User Name],

Your registration for [Event Name] has been cancelled.

If you paid for this event, a refund has been processed and will appear in your account within 5-7 business days.

If you have any questions, please contact us.

University Events Team
```

**Integration into existing code:**

I had to modify three existing files:

1. **registration.php** - Added email sending after successful registration
2. **payment.php** - Added email sending after successful payment
3. **cancel.php** - Added email sending after cancellation

For each one, I:
- Got the user's email from the database
- Got the event details from the database
- Replaced the placeholders in the template with real data
- Called PHPMailer to send the email
- Added error handling in case email sending fails (the registration/payment still succeeds even if email fails)

**Challenges:**
- Gmail SMTP has security settings that blocked my first attempts. I had to enable "Less secure app access" and use an app-specific password.
- At first, emails were going to spam. I had to add proper headers and a "From" name to fix this.
- The email templates needed the user's name, but in the payment flow we only had the user_id. I had to add a query to get the user's name from the database.
- I wanted to make the emails look nice with HTML formatting, but ran out of time. So they're just plain text, which is fine for now.

**Time spent:** About 6 hours (this was the most time-consuming feature)

---

## Technical Decisions

**Why TCPDF for PDF generation?**
I considered FPDF and TCPDF. I chose TCPDF because it has better Unicode support (handles special characters better) and I've used it before.

**Why Gmail SMTP instead of setting up our own mail server?**
For a university project, Gmail SMTP is easier and more reliable. For production, we'd use the university's own mail server.

**Why plain text emails instead of HTML?**
I wanted to do HTML emails with nice styling, but I prioritized getting the emails to actually send over making them look fancy. Plain text is more reliable and less likely to end up in spam.

**Why not use a queue for emails?**
For small scale (a few registrations per minute), sending emails immediately is fine. For production with high volume, we'd use a queue system like Redis or RabbitMQ to handle email sending in the background.

---

## Testing I Did

**Export Features:**
- Tested CSV export with events that have 1, 10, and 50 attendees
- Tested PDF export with the same events
- Tested with attendees who have special characters in their names (like O'Brien, José)
- Opened the exported files to verify formatting looks good

**Reports Dashboard:**
- Manually calculated statistics from the database using phpMyAdmin
- Compared my manual calculations to what the API returns
- Created test data: added some events, registrations, and payments
- Verified the numbers updated correctly

**Email Notifications:**
- Registered for test events and checked my email inbox
- Made test payments and checked email
- Cancelled test registrations and checked email
- Tested with Gmail, Yahoo, and Outlook email addresses
- Checked that emails weren't going to spam
- Verified that registration still works even if email sending fails

---

## Files I Created/Modified

**New Files:**
- `api/admin/export-pdf.php` - PDF export endpoint
- `api/admin/reports.php` - Reports dashboard endpoint
- `includes/email-templates.php` - Email template functions
- `includes/email-sender.php` - PHPMailer wrapper functions

**Modified Files:**
- `api/admin/export-csv.php` - Improved CSV formatting
- `api/register.php` - Added email notification after registration
- `api/payment.php` - Added email notification after payment
- `api/cancel.php` - Added email notification after cancellation

**Configuration Files:**
- `config/email-config.php` - SMTP settings (not committed to Git for security)

---

## API Documentation

**New Endpoints:**

**1. Export PDF**
```
GET /api/admin/events/:id/attendees/export-pdf
Authentication: Admin required
Returns: PDF file download
```

**2. Reports Dashboard**
```
GET /api/admin/reports
Authentication: Admin required
Returns: JSON with statistics
Example response:
{
  "totalEvents": 12,
  "totalRegistrations": 45,
  "totalRevenue": 875.00,
  "activeUsers": 23
}
```

**Modified Endpoints:**
- POST /api/register - Now sends confirmation email
- POST /api/payment - Now sends payment confirmation email
- POST /api/cancel - Now sends cancellation email

---

## Bugs I Fixed

**Bug 1:** Revenue calculation included failed payments
- Found during testing
- Fixed by adding WHERE status = 'success' to the query

**Bug 2:** Emails going to spam
- Added proper headers: From, Reply-To, X-Mailer
- Used the full email format: "University Events <events@example.com>"

**Bug 3:** CSV export broke when attendee name contained a comma
- Fixed by wrapping all values in quotes

---

## What I Learned

**TCPDF Library:**
- It's powerful but has a lot of options
- Documentation isn't great, I had to look at examples online
- Setting column widths is tricky - had to experiment to get it right

**PHPMailer:**
- Gmail SMTP security is strict - need app-specific password
- Email headers are important for avoiding spam filters
- Plain text emails are more reliable than HTML

**SQL Optimization:**
- For the reports dashboard, I initially ran 4 separate queries
- I realized I could combine some of them, but decided separate queries are clearer and the performance difference is negligible for our scale

---

## Time Breakdown

| Task | Time Spent |
|------|-----------|
| CSV improvements | 1 hour |
| PDF export | 2 hours |
| Reports API | 2 hours |
| Email setup and configuration | 2 hours |
| Email templates | 1 hour |
| Integration into registration flow | 1 hour |
| Integration into payment flow | 1 hour |
| Integration into cancellation flow | 1 hour |
| Testing all features | 2 hours |
| Bug fixes | 1 hour |
| Documentation | 1 hour |

**Total: 15 hours** (spread over 2 days)

---

## Challenges Faced

**1. Tight Timeline**
Two days for 15 story points was aggressive. I had to prioritize getting things working over making them perfect. For example, I skipped adding the university logo to PDFs and kept emails as plain text.

**2. Gmail SMTP Issues**
Took me an hour to figure out the security settings. Gmail kept blocking my attempts until I set up an app-specific password and enabled less secure app access.

**3. Email Reliability**
Emails are tricky. Even after I got them sending, they were going to spam. I had to research email headers and best practices to fix this.

**4. Lack of HTML Email Design**
I'm a backend developer, not a designer. I wanted to make the emails look nice with HTML, but I don't know CSS well enough. So I kept them as plain text which looks less professional but is more reliable.

---

## If I Had More Time

**Email Improvements:**
- Use HTML email templates with proper styling
- Add inline images like the university logo
- Add an "Add to Calendar" button in emails
- Test emails on more email clients

**PDF Improvements:**
- Add university logo to PDF header
- Add QR code to each attendee row for quick check-in
- Better formatting and styling
- Option to export as Excel file in addition to PDF

**Reports Improvements:**
- Add date range filtering (show stats for last week, last month, etc.)
- Add more statistics like average registrations per event
- Add charts and graphs (though Muneera would do the frontend part)

**Email Queue System:**
- Implement background job queue for sending emails
- Add retry logic if email sending fails
- Add email logs to database to track what was sent

---

## Integration with Frontend

I coordinated with Muneera on:

**Export Features:**
- She needed to know the endpoint URLs
- We agreed on the file naming format
- I told her to show a loading spinner while PDF generates (it takes a few seconds)

**Reports Dashboard:**
- I gave her the exact JSON response format so she could build the UI
- She wanted the revenue formatted with 2 decimal places, which I ensured

**Email Notifications:**
- She needed to know that emails are sent automatically
- She added small notifications in the UI like "Confirmation email sent to your inbox"
- We agreed that the flow should still work even if email fails (no need to show an error to the user if email fails)

---

## Code Quality

**What I'm proud of:**
- Clean separation of email logic into its own file
- Good error handling (email failures don't break registration)
- SQL queries are simple and readable
- API responses are consistent with Sprint 3

**What could be better:**
- Email templates are just PHP string concatenation - should use a proper template engine
- PDF generation code is all in one big function - should break it into smaller functions
- No logging for email send failures - should log these for debugging

---

## Security Considerations

**Email Configuration:**
- SMTP credentials are in a config file that's not committed to Git
- Added config/email-config.php to .gitignore

**SQL Injection:**
- Used prepared statements for all database queries
- All user input is sanitized

**Email Injection:**
- Validated email addresses before sending
- Used PHPMailer's built-in sanitization

---

## Conclusion

Sprint 4 was intense but successful. We delivered all three features in just 2 days. The export enhancements make the admin panel more professional, the reports dashboard gives admins useful insights, and email notifications make the system feel much more complete.

The tight timeline meant I had to make some compromises (plain text emails, no logo in PDF), but all the core functionality works well.

I'm satisfied with what we accomplished. The backend is now feature-complete for our MVP. Any future work would be enhancements and polish rather than core functionality.

---

**Prepared by:** Fariba Mohammadi (Backend Lead)  
**Date:** December 2, 2025  
**Sprint:** Sprint 4 Complete

