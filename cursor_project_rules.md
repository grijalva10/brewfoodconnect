# Cursor Project Rules — BrewFood Connect

This document outlines the working rules and best practices for contributing to the BrewFood Connect project, built using Bubble.io. These rules help maintain consistency, clarity, and scalability as the project evolves.

---

## 1. Development Environment

- **Platform**: [Bubble.io](https://bubble.io)
- **Environments**: 
  - `Development`: All changes are made and tested here.
  - `Live`: Production-facing version, deploy only after full testing.
- Use version control in Bubble to manage feature checkpoints before pushing to live.

---

## 2. Role-Based Permissions

- **Admin**: Full access to user management, bookings, slots, and platform settings.
- **Breweries**: Can create slots, view and manage incoming requests, and approve/reject vendors.
- **Vendors**: Can browse slots, submit booking requests, and manage their profile.
- **Developers (Internal/External)**: Only make changes in the `Development` version unless explicitly approved to deploy.

---

## 3. Naming Conventions

### Data Types
- Use **PascalCase** (e.g., `BookingRequest`, `Slot`, `Notification`)
- Use clear, descriptive names (avoid generic names like “Data” or “Thing”)

### Fields
- Use **camelCase** for field names (e.g., `startTime`, `vendorNote`)
- Avoid abbreviations unless widely accepted (e.g., `email`, not `em`)

### Workflows
- Name workflows according to their action + object (e.g., `Create Slot`, `Approve BookingRequest`)
- Group reusable workflows under folders if possible

---

## 4. Workflow Rules

- Use **custom events** to group logic and avoid duplication.
- Every user-triggered workflow must include error handling (e.g., show alert if a field is missing).
- Avoid deeply nested conditionals; break into reusable workflow steps or conditions when possible.

---

## 5. Database Rules

- Each data type must include a `Created By` field unless inherently tied to the `Current User`.
- Never expose full user lists to clients unless user has Admin rights.
- Add `Status` fields where possible instead of deleting records — soft deletes are preferred.

---

## 6. Deployment Rules

- All deployments to `Live` must be tested in `Development` and reviewed internally.
- Use Bubble’s “Run as” feature to test as different user roles before pushing.
- Update internal documentation or Loom walkthroughs when workflows or data models change.

---

## 7. Design Consistency

- Use global styles for typography, buttons, and spacing.
- Keep UI minimalist — only display essential information.
- Ensure accessibility with good contrast and large tap targets for mobile users.

---

## 8. Communication & Change Requests

- Use Notion or ClickUp to track feature requests, bugs, and priorities.
- Each change request must include:
  - Brief Description
  - User Role Impacted
  - Expected Outcome
- Use Loom for visual explanations if workflows are involved.

---

## 9. Feature Flags & Scalability

- When adding new features (e.g., Google Calendar, SMS), wrap them in conditional logic or hide/show based on admin toggles.
- Maintain modularity — new features should not break the core availability → request → confirmation loop.

---

## 10. Security & Privacy

- Always implement Bubble Privacy Rules for each data type.
- Validate all user actions (e.g., a vendor should not be able to modify a brewery’s slot).
- Mask private information in UI where unnecessary (e.g., brewery contact info visible only after booking is confirmed).

---

## 11. Summary

These rules are designed to keep BrewFood Connect fast, lean, and scalable. Stick to them, and we’ll avoid tech debt, confusion, and inconsistent user experience as we grow.

