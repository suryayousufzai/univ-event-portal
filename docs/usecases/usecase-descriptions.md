# Use case descriptions – University event registration portal

---

### **UC-01: Register account**
**Actor:** Visitor  
**Description:** A visitor opens a new account by entering their name, email, and password. After submission, the system verifies the information and creates the user’s profile.  
**Precondition:** The visitor does not already have a registered account.  
**Postcondition:** A new user account is created, and a confirmation email is sent to the registered address.

---

### **UC-02: Login**
**Actor:** Registered user  
**Description:** A registered user logs in to the system with valid credentials. The system verifies the username and password before granting access.  
**Precondition:** The user must have an active account.  
**Postcondition:** The system displays the user’s dashboard, showing their event registrations and profile.

---

### **UC-03: Browse and Search events**
**Actor:** Visitor / Registered user  
**Description:** The user explores events by browsing the event list or using search filters to find specific ones.  
**Postcondition:** The system displays a list of events that match the search or browsing criteria.

---

### **UC-04: Register for event**
**Actor:** Registered User  
**Description:** The user selects an event and signs up to attend. If the event requires payment, the system redirects to the payment gateway for processing.  
**Postcondition:** The registration is confirmed and saved in the system, and a confirmation email is sent to the user.

---

### **UC-05: Cancel registration**
**Actor:** Registered User  
**Description:** The user cancels a previously made event registration. The system updates the registration status and releases the reserved seat.  
**Postcondition:** The registration is canceled, and the event seat becomes available to other users.

---

### **UC-06: Download ticket**
**Actor:** Registered User  
**Description:** Once successfully registered for an event, the user can download the event ticket in PDF format.  
**Postcondition:** The ticket file is generated and downloaded to the user’s device.

---

### **UC-07: Manage events**
**Actor:** Admin  
**Description:** The admin creates, edits, or deletes events by managing details such as title, date, venue, and description.  
**Postcondition:** Event information in the database is updated accordingly.

---

### **UC-08: View attendees**
**Actor:** Admin  
**Description:** The admin views the list of attendees for each event to review participant details or export data for records.  
**Postcondition:** The attendee list is displayed or exported successfully.

---

### **UC-09: Generate reports**
**Actor:** Admin  
**Description:** The admin generates analytical reports summarizing event statistics such as registrations, attendance, and revenue.  
**Postcondition:** A summary report is displayed on the dashboard or exported for further analysis.


---

### UC-10: Send confirmation email
**Actor:** Email Service  
**Description:** Sends automatic email when a user registers or cancels.  
**Postcondition:** Email successfully delivered.

