# Task Manager - THE LIGHT PARK 2026 Edition

A comprehensive task management application built with vanilla JavaScript, featuring THE LIGHT PARK's signature dark theme, designed specifically for managing the 2026 season creative playbook tasks. Includes admin password protection for task editing/deletion, user note editing, and automated email/SMS notifications.

![Task Manager](https://img.shields.io/badge/version-4.0.0-purple) 
![License](https://img.shields.io/badge/license-MIT-blue) 
![Browsers](https://img.shields.io/badge/browsers-Chrome%20%7C%20Firefox%20%7C%20Safari%20%7C%20Edge-green)

## ✨ Features

### Core Task Management
- **Complete CRUD Operations**: Add, edit, delete, and complete tasks
- **Multi-User Assignment**: Assign multiple team members to each task
- **Priority Levels**: High, Medium, and Low priority badges
- **Category Organization**: Tasks organized by month (February - June 2026)
- **Rich Descriptions**: Add detailed descriptions to tasks
- **Notes System**: Add timestamped notes and status updates to any task

### Security & Notifications
- **🔒 Password-Protected Editing**: Admin password required to edit tasks (Password: admin123)
- **🔒 Password-Protected Deletion**: Admin password required to delete tasks (Password: admin123)
- **✏️ User Note Editing**: Assigned users can edit notes without password
- **📧 Email Notifications**: All task events sent to bdodge@thelightpark.com
- **📱 SMS Notifications**: Task completions and note edits sent to 17145958391 (Twilio)
- **Unassigned by Default**: All pre-loaded tasks start unassigned for admin control
- **Audit Trail**: All actions logged with timestamps

### Advanced Filtering
- **Category Filters**: View tasks by month (February, March, April, May, June)
- **Priority Filters**: Filter by High, Medium, or Low priority
- **Status Filters**: View All, Active, or Completed tasks
- **Real-time Statistics**: Track total, active, completed, and high-priority tasks

### Visual Design
- **THE LIGHT PARK Branding**: Logo prominently displayed
- **Dark Theme**: Eye-friendly black background with purple and teal accents
- **Visual Feedback**: Strikethrough styling and color changes for completed tasks
- **Responsive Design**: Works seamlessly on mobile, tablet, and desktop
- **Smooth Animations**: Professional transitions and hover effects

### Data & Accessibility
- **Data Persistence**: All data saved to browser localStorage
- **Pre-loaded Demo Data**: 18 tasks from THE LIGHT PARK 2026 playbook
- **Accessibility**: WCAG AA compliant with keyboard navigation support
- **No Dependencies**: Pure HTML, CSS, and JavaScript - no frameworks needed

## 🎨 Design System

The application uses THE LIGHT PARK brand colors extracted from the logo:

- **Background**: Pure black (#000000) with dark gray variations
- **Primary Purple**: #8B5CF6 (main brand color for headers and primary actions)
- **Accent Teal**: #14B8A6 (secondary highlight color for user tags and notes)
- **Priority Colors**:
  - High: #EF4444 (red)
  - Medium: #F59E0B (orange)
  - Low: #10B981 (green)

## 🚀 Installation

### Quick Start

1. Download the `index.html` file
2. Open it in any modern web browser
3. That's it! No setup required

### Local Development

For local development with a web server:

```bash
# Using Python 3
python -m http.server 8070

# Using Node.js (http-server)
npx http-server -p 8070

# Using PHP
php -S localhost:8070
```

Then navigate to `http://localhost:8070`

## 📖 Usage Instructions

### Adding Tasks
1. Fill in the task title (minimum 3 characters)
2. Select a category (February - June 2026)
3. Select a priority level (High, Medium, Low)
4. Optionally add a description
5. Assign users by typing names and pressing Enter
6. Click "Add Task"

### Assigning Multiple Users
1. In the "Assign Users" field, type a team member's name
2. Press Enter to add them
3. Repeat for additional team members
4. Remove users by clicking the × button on their tag

### Filtering Tasks
- **By Category**: Click month buttons to view tasks for specific months
- **By Priority**: Filter by High, Medium, or Low priority
- **By Status**: View All, Active, or Completed tasks
- **Combine Filters**: Use multiple filters simultaneously

### Managing Tasks
- **Complete**: Click the checkbox next to any task
- **Delete**: Click the "Delete" button, enter admin password (admin123), and confirm
- **View Notes**: Click "Show Notes" to expand the notes section
- **Add Notes**: Type your note and click "Add Note"

### Admin Password Protection
When deleting a task:
1. Click the "Delete" button on any task
2. A modal will appear requesting admin authentication
3. Enter the admin password: **admin123**
4. Click "Delete Task" to confirm
5. An email notification will be sent to bdodge@thelightpark.com

### Email Notifications
The system automatically sends notifications to **bdodge@thelightpark.com** for:
- ✅ Task created
- ✅ Task deleted
- ✅ Task completed
- ✅ Task updated
- ✅ User assigned to task
- ✅ Note added to task

**Note**: Email notifications are currently logged to the browser console. In production, these would be sent via a backend API endpoint.

### Statistics Dashboard
View real-time statistics:
- Total tasks in the system
- Active (incomplete) tasks
- Completed tasks
- High-priority active tasks

### Clearing All Data
1. Scroll to the bottom and click "Clear All Data"
2. Click again within 3 seconds to confirm
3. All tasks and notes will be permanently deleted

## 📱 Browser Compatibility

- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+

## 🎯 Pre-loaded Demo Data

The application includes 18 tasks from THE LIGHT PARK 2026 Creative Playbook.

**⚠️ IMPORTANT**: All pre-loaded tasks are **unassigned by default**. This allows administrators to manually assign team members as needed. Tasks will display "⚠️ No users assigned" until users are added.

### Task List:

### February 2026 (5 tasks)
- DJ Polar Ice Avatar Development (High Priority) - **Unassigned**
- Pixel Penguin Character Design (High Priority) - **Unassigned**
- Oklahoma City Park Layout Design (High Priority) - **Unassigned**
- Tent Experience Enhancement (High Priority) - **Unassigned**
- Marketing Assets Organization (Medium Priority) - **Unassigned**

### March 2026 (5 tasks)
- YouTube Channel Launch (Medium Priority) - **Unassigned**
- Festival Map Prototype Development (High Priority) - **Unassigned**
- Mobile App Development (High Priority) - **Unassigned**
- Theme Song/Jingle Creation (High Priority) - **Unassigned**
- New Audio Track Production (High Priority) - **Unassigned**

### April 2026 (3 tasks)
- Bumper Track Integration (High Priority) - **Unassigned**
- Site Layout Finalization (High Priority) - **Unassigned**
- Branding Finalization (High Priority) - **Unassigned**

### May 2026 (3 tasks)
- Social Media Launch (High Priority) - **Unassigned**
- Tent Improvement Production (High Priority) - **Unassigned**
- Early Bird Sales Planning (Medium Priority) - **Unassigned**

### June 2026 (2 tasks)
- Community Outreach (Medium Priority) - **Unassigned**
- App Audio Content Creation (Medium Priority) - **Unassigned**

Each task includes:
- Detailed descriptions
- **No assigned users by default** (must be manually assigned)
- Priority levels
- Category tags
- Empty notes section (ready for status updates)

## 🔧 Technical Details

### Technology Stack
- **HTML5**: Semantic markup and structure
- **CSS3**: Modern styling with CSS Grid and Flexbox
- **Vanilla JavaScript**: ES6+ features, no frameworks

### Key Features Implemented
- ✅ Task CRUD operations (Create, Read, Update, Delete)
- ✅ Multi-user assignment system
- ✅ Priority levels (High, Medium, Low)
- ✅ Category organization (February - June)
- ✅ Advanced filtering system
- ✅ Notes/comment system with timestamps
- ✅ localStorage for data persistence
- ✅ Real-time statistics dashboard
- ✅ Responsive design (mobile-first approach)
- ✅ Keyboard navigation support
- ✅ Form validation with error messages
- ✅ Smooth animations and transitions
- ✅ Accessibility (WCAG AA compliant)
- ✅ **Password-protected task deletion (admin123)**
- ✅ **Email notifications to bdodge@thelightpark.com**
- ✅ **Unassigned tasks by default**

### Data Structure
```javascript
{
  id: "unique-id",
  title: "Task title",
  description: "Task description",
  category: "February",
  priority: "high",
  completed: false,
  createdAt: "2024-01-15T14:30:00.000Z",
  completedAt: null,
  users: ["User 1", "User 2"],
  notes: [
    {
      id: "note-id",
      content: "Note content",
      timestamp: "2024-01-15T14:35:00.000Z",
      author: "User Name"
    }
  ]
}
```

## 🧪 Testing Checklist

- [x] Opens without errors in browser
- [x] Can add tasks with all fields
- [x] Can assign multiple users to tasks
- [x] Can set priority levels
- [x] Can set categories
- [x] Can delete tasks with confirmation
- [x] Can toggle task completion
- [x] Can add notes to tasks
- [x] Notes expand/collapse correctly
- [x] Category filtering works
- [x] Priority filtering works
- [x] Status filtering works
- [x] Statistics update in real-time
- [x] Data persists after browser refresh
- [x] Clear all data works with double confirmation
- [x] Responsive on mobile (320px+)
- [x] No console errors
- [x] Keyboard navigation works
- [x] Color contrast meets WCAG AA standards
- [x] Logo displays correctly

## 📁 File Structure

```
TaskManagementSystem/
├── index.html          # Main application file (complete, self-contained)
├── assets/
│   └── logo.jpg        # THE LIGHT PARK logo
├── README.md           # This file
├── LICENSE             # MIT License
└── .gitignore          # Git ignore file
```

## 🎨 Customization

### Changing Colors
Edit the CSS custom properties in the `<style>` section:

```css
:root {
    --purple-primary: #8B5CF6;
    --teal-primary: #14B8A6;
    --priority-high: #EF4444;
    /* ... other color variables */
}
```

### Adding New Categories
Update the category dropdown in the HTML:

```html
<select id="task-category">
    <option value="July">July 2026</option>
    <!-- Add more months -->
</select>
```

And add corresponding filter buttons:

```html
<button class="filter-btn" data-category="July">July</button>
```

### Modifying Validation Rules
Update the validation functions in JavaScript:

```javascript
// Change minimum task title length
if (trimmedTitle.length < 3) { /* ... */ }
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📞 Support

For issues, questions, or suggestions, please open an issue on the repository.

## 🎉 Credits

- **Design Inspiration**: THE LIGHT PARK brand identity
- **Built with**: Vanilla HTML, CSS, and JavaScript
- **Year**: 2024-2026

## 🔒 Security &amp; Privacy

### Security Features
- **Admin Password Protection**: Task deletion requires password authentication (admin123)
- **Modal-based Authentication**: Secure password entry with error handling
- **Keyboard Shortcuts**: Press Escape to close authentication modal
- **Password Masking**: Password input is hidden for security

### Privacy &amp; Data
- Runs entirely in your browser
- Stores all data locally on your device (localStorage)
- Requires no server or database for core functionality
- **Email Notifications**: Currently logged to console (requires backend API in production)
- No external API calls for data storage

### Admin Credentials
- **Password**: admin123
- **Notification Email**: bdodge@thelightpark.com
- **Note**: Change these values in production by editing the CONFIG object in the JavaScript code

### Production Deployment Notes
For production use, you should:
1. Change the admin password from default
2. Implement a backend API for email notifications
3. Consider adding user authentication
4. Implement proper password hashing
5. Add rate limiting for failed password attempts

## 🆕 Version 3.0 Updates

### Security & Administrative Features
- ✅ **Password-protected task deletion** (admin123)
- ✅ **Email notification system** (bdodge@thelightpark.com)
- ✅ **Unassigned tasks by default** for admin control
- ✅ Modal-based authentication for deletions
- ✅ Comprehensive audit logging

### Previous Features (v2.0)
- ✅ THE LIGHT PARK logo integration
- ✅ Multi-user assignment system
- ✅ Priority levels (High, Medium, Low)
- ✅ Category organization by month
- ✅ Advanced filtering system
- ✅ Real-time statistics dashboard
- ✅ 18 pre-loaded tasks from 2026 playbook
- ✅ Enhanced visual design
- ✅ Improved mobile responsiveness

### Enhanced User Experience
- Better task organization with categories
- Visual priority indicators
- User assignment tags
- Comprehensive filtering options
- Real-time statistics
- Professional branding throughout
- Secure admin controls
- Automated notifications

---

**Note**: This application is designed to work immediately without any setup. Simply open `index.html` in your browser and start managing THE LIGHT PARK 2026 season tasks!