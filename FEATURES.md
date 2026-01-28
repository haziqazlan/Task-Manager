# Features

I started with basic CRUD operations and kept adding features as I learned more. Here's everything the app can do now:

## Authentication

**Registration & Login**
- Standard email/password signup
- Password must be at least 6 characters (I validate both frontend and backend)
- Checks for duplicate emails
- Returns JWT token that expires after 7 days

**Security**
- Passwords are hashed with bcrypt (never stored in plain text)
- JWTs are used for all authenticated requests
- Each user can only see their own tasks (checked server-side)
- Token stored in localStorage (yeah I know, not the most secure, but good enough for this)

**UX Improvements**
- Show/hide password toggle (the eye icon)
- "Forgot password?" link (frontend only for now - would need to wire up email service)
- Specific error messages instead of generic "Authentication failed"
  - "Invalid email or password"
  - "This email is already registered"
  - "Password must be at least 6 characters"
- Success messages like "Welcome back!" when you login

## Task Management

**Creating Tasks**
- Title (required)
- Description (optional)
- Priority: Low/Medium/High
- Due date (optional, can't select past dates)
- All fields validated before submission

**Editing Tasks**
- Click the pencil icon to edit
- Can change title, description, priority, and due date
- Save button to confirm changes
- Updates happen instantly

**Task States**
- Pending (default)
- Completed (click the circle to toggle)
- One click to switch between states

**Deleting**
- Confirmation prompt before delete
- Added this after accidentally deleting a task I needed

**Overdue Detection**
- Tasks with past due dates get highlighted in red
- Shows "OVERDUE" label
- Only applies to pending tasks (completed ones don't count as overdue)

## Organization

**Search**
- Search bar that filters tasks by title or description
- Updates in real-time as you type
- Shows "No results" message when nothing matches
- Clear button (X) to reset search

**Filtering**
- All tasks
- Pending only
- Completed only
- Shows count for each filter (e.g., "Pending (5)")

**Sorting**
- Newest first (default)
- Oldest first
- Priority (High → Medium → Low)
- Due date (earliest first, tasks without dates go to the end)

Search + filter + sort all work together. So you can search for "project", filter by pending, and sort by priority.

## Statistics Dashboard

Five cards at the top showing:
- **Total Tasks** - everything you've created
- **Pending** - tasks you haven't finished
- **Completed** - tasks you've checked off
- **Overdue** - pending tasks past their due date
- **High Priority** - pending tasks marked as high priority

Plus a progress bar showing your completion rate. When you complete everything, it says "Amazing work!" which feels nice.

All stats update immediately when you create, complete, or delete tasks.

## UI/UX

**Responsive Design**
- Works on phones (tested down to 320px width)
- Tablet layout adjusts the grid
- Desktop shows everything side by side
- Navbar is sticky so you can always logout

**Visual Feedback**
- Success messages (green) for actions like "Task created!"
- Error messages (red) for failures
- All messages auto-dismiss after 5 seconds
- Can manually close messages with X button
- Loading states on buttons ("Processing...", "Creating...")
- Button is disabled and cursor changes during loading

**Task Cards**
- Priority badges color-coded (red/yellow/green)
- Completed tasks get gray background and strikethrough
- Due dates shown with calendar icon
- Created date shown in small text
- Hover effects on cards

**Empty States**
- Different messages based on context:
  - "Create your first task to get started!" when you have no tasks
  - "No tasks in this category" when filter returns nothing
  - "No tasks found matching your search" when search returns nothing

**Animations**
- Messages slide down when they appear
- Buttons have hover effects
- Task completion checkmark animates
- Smooth transitions everywhere

## Technical Features

**API Structure**
- RESTful endpoints
- Proper HTTP methods (GET, POST, PUT, DELETE)
- JWT in Authorization header
- JSON request/response bodies

**Error Handling**
- Network errors caught and displayed
- Invalid inputs validated before sending to server
- Backend validation as well (never trust the client)
- User-friendly error messages

**Data Persistence**
- Everything saved to MongoDB
- Logout doesn't lose your tasks
- Can close browser and come back later

**Performance**
- Search and sort happen client-side (no extra API calls)
- Tasks fetched once on login, then managed locally
- Only makes API calls when data actually changes

## What's Not Implemented Yet

Things I thought about adding but haven't gotten to:

- **Email verification** - Would need an email service like SendGrid
- **Password reset** - Same issue, need email functionality
- **Task categories/tags** - Thought about it but didn't want to overcomplicate
- **Attachments** - Would need file upload handling
- **Sharing tasks** - Would require user relationships in database
- **Notifications** - Browser notifications or email reminders
- **Dark mode** - Everyone wants this but I focused on functionality first
- **Keyboard shortcuts** - Would be nice for power users
- **Export to CSV** - Easy to add, just haven't done it yet
- **Recurring tasks** - More complex than it sounds

## Browser Support

Tested on:
- Chrome (main browser I use)
- Firefox
- Safari
- Edge

Doesn't work on IE11 (but who cares about IE in 2024).

## Accessibility

I tried to make it accessible but there's definitely room for improvement:
- All buttons have hover states
- Forms have labels
- Error messages are readable
- Color contrast is decent
- Could add ARIA labels
- Could add keyboard navigation
- Screen reader support not tested

This is one area I want to learn more about for my next project.
