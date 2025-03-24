# Application Flow Document — BrewFood Connect

## 1. Overview
BrewFood Connect is a web-based platform built with Bubble.io that connects breweries with food vendors by streamlining the event scheduling and booking process. The app provides intuitive dashboards for both user types and handles the full booking workflow, from availability creation to final confirmation.

---

## 2. User Roles & Journeys

### **Breweries**
1. **Login / Sign Up**
2. **Set Up Profile** (Location, Contact, Preferences)
3. **Create Availability Schedule**
4. **View Incoming Vendor Requests**
5. **Approve / Deny Requests**
6. **Monitor Calendar of Confirmed Bookings**

### **Vendors**
1. **Login / Sign Up**
2. **Set Up Profile** (Photos, Cuisine Type, Past Events)
3. **Browse Available Brewery Slots**
4. **Request Booking**
5. **Await Approval**
6. **Track Confirmed Events in Calendar View**

### **Admin**
1. **Access Admin Dashboard**
2. **Manage Users (Breweries & Vendors)**
3. **Monitor Booking Volume / Platform Usage**
4. **Update Platform Settings or Limits**

---

## 3. Platform Flows

### **Booking Flow**
1. **Brewery Creates Slot** → Added to public vendor-facing schedule.
2. **Vendor Browses Slots** → Applies for desired slot.
3. **Brewery Receives Notification** → Approves or Rejects.
4. **System Sends Confirmation** → Updates both user dashboards.
5. **Confirmed Slot Appears in Brewery & Vendor Calendars**

### **Notification Flow**
- Bubble triggers internal notifications (via workflows) for:
  - New slot availability (to subscribed vendors)
  - Booking request submitted
  - Booking approved/denied

---

## 4. Core Pages & Navigation

### **Public Landing Page**
- Mission Statement
- Call-to-Action for Breweries and Vendors
- Demo Video or Screenshots (Optional)

### **User Dashboard (Post-Login)**
- **Breweries**: Schedule manager, booking requests, calendar
- **Vendors**: Available slots, request history, upcoming events

### **Admin Panel**
- User list, roles
- Activity log (requests, confirmations)
- Booking limit controls (e.g., per brewery)

---

## 5. Bubble.io Notes
- **Backend Workflows** handle all approval logic, calendar updates, and notifications.
- **Custom Data Types**:
  - `User` (fields: role, profile info)
  - `Slot` (fields: brewery, date, time, status)
  - `BookingRequest` (fields: vendor, slot, status)
- **Security & Privacy**:
  - Role-based visibility controls on all pages.
  - Users can only access their own data.

---

## 6. Future Flow Enhancements (Post-MVP)
- **Calendar Sync**: Two-way sync with Google Calendar for breweries.
- **SMS Notifications**: Reminders for both parties using Twilio or similar.
- **Recurring Slots**: Brewery ability to auto-create repeating events.
- **Vendor Waitlists**: If slot is full, vendors can join a queue.

---

## 7. Flow Diagram (To Be Added)
[A simple Bubble.io visual or external diagram tool can show the sequence of events from both user perspectives.]

---

## 8. Summary
The app flow centers around one core loop: **availability → request → approval → confirmation**. The use of Bubble.io enables rapid iteration of this logic while supporting scalability and custom workflows as the product evolves.
