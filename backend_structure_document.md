# Backend Structure Document — BrewFood Connect

## 1. Overview
Although BrewFood Connect is built using Bubble.io (a no-code platform), it still has a clear backend structure powered by Bubble’s built-in database, custom data types, and workflow logic. This document outlines the architecture behind the scenes, enabling feature delivery, data handling, and future scalability.

---

## 2. Core Concepts in Bubble

### Data Types (Equivalent to Database Tables)
Bubble uses custom data types with fields to structure the app’s backend database.

### Workflows (Equivalent to Backend Logic)
Bubble workflows replace traditional backend endpoints. They are triggered by user actions, scheduled events, or conditions.

### Privacy Rules
Control who can read, write, or modify each data type based on the current user’s role or ownership.

---

## 3. Data Model Structure

### `User`
- `Role`: Text (Vendor, Brewery, Admin)
- `Email`: Text
- `Name`: Text
- `Profile Photo`: Image
- `Business Name`: Text
- `Location`: Geographic address
- `Bio / Description`: Text

### `Slot`
- `Brewery`: Linked to User (type Brewery)
- `Date`: Date
- `Start Time`: Time (or part of Date)
- `End Time`: Time
- `Status`: Text (Open, Requested, Confirmed, Closed)
- `Max Vendors`: Number (optional, for future batching support)

### `BookingRequest`
- `Vendor`: Linked to User
- `Slot`: Linked to Slot
- `Status`: Text (Pending, Approved, Rejected)
- `Message`: Text (optional note from vendor)

### `Notification`
- `Recipient`: Linked to User
- `Message`: Text
- `Type`: Text (New Slot, Booking Request, Approval, Rejection)
- `Read`: Boolean
- `Timestamp`: Date

---

## 4. Backend Workflows

### User-Triggered Workflows
- **Create Slot** (Breweries)
  - Action: Create a new `Slot` record
  - Notify vendors (optional future enhancement)

- **Request Booking** (Vendors)
  - Action: Create a new `BookingRequest`
  - Notify brewery

- **Approve / Reject Booking** (Breweries)
  - Action: Change `BookingRequest` status
  - Update `Slot` status if approved
  - Notify vendor

### Scheduled Workflows (Planned Enhancements)
- **Daily Reminders**
  - Notify vendors and breweries of upcoming bookings

- **Slot Expiry**
  - Auto-close unconfirmed slots after a certain time

---

## 5. Privacy Rules

### `User`
- Users can only view or modify their own profile

### `Slot`
- Brewery users can modify their own slots
- Vendors can view only slots marked as "Open"

### `BookingRequest`
- Only the associated vendor and brewery can view
- Only breweries can approve/reject

### `Notification`
- Only visible to the recipient

---

## 6. API Integration (Planned)
- Bubble’s API Connector will be used in the future for:
  - Google Calendar Sync
  - Twilio SMS notifications
  - Analytics or external CRMs if needed

---

## 7. Versioning & Deployment
- Bubble provides a **Development** and **Live** environment
- Changes are tested in Development before pushing to Live
- Database structure is versioned with the app

---

## 8. Admin Tools
- Admin users can view all data types
- Special admin-only pages allow:
  - Viewing all bookings
  - Managing brewery and vendor accounts
  - Enforcing booking limits or suspending users

---

## 9. Summary
While no-code in nature, BrewFood Connect’s backend mirrors the architecture of a traditional relational app. With clearly defined data types, workflow logic, and role-based privacy controls, it supports a robust MVP that’s easy to maintain and extend as the platform grows.

