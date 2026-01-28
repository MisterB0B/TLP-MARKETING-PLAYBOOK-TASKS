# Task Manager - THE LIGHT PARK 2026 Edition

A comprehensive task management application built with vanilla JavaScript, featuring THE LIGHT PARK's signature dark theme, designed specifically for managing the 2026 season creative playbook tasks.

![Task Manager](https://img.shields.io/badge/version-2.0.0-purple) 
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
- **Delete**: Click the "Delete" button and confirm
- **View Notes**: Click "Show Notes" to expand the notes section
- **Add Notes**: Type your note and click "Add Note"

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

The application includes 18 tasks from THE LIGHT PARK 2026 Creative Playbook:

### February 2026 (5 tasks)
- DJ Polar Ice Avatar Development (High Priority)
- Pixel Penguin Character Design (High Priority)
- Oklahoma City Park Layout Design (High Priority)
- Tent Experience Enhancement (High Priority)
- Marketing Assets Organization (Medium Priority)

### March 2026 (5 tasks)
- YouTube Channel Launch (Medium Priority)
- Festival Map Prototype Development (High Priority)
- Mobile App Development (High Priority)
- Theme Song/Jingle Creation (High Priority)
- New Audio Track Production (High Priority)

### April 2026 (3 tasks)
- Bumper Track Integration (High Priority)
- Site Layout Finalization (High Priority)
- Branding Finalization (High Priority)

### May 2026 (3 tasks)
- Social Media Launch (High Priority)
- Tent Improvement Production (High Priority)
- Early Bird Sales Planning (Medium Priority)

### June 2026 (2 tasks)
- Community Outreach (Medium Priority)
- App Audio Content Creation (Medium Priority)

Each task includes:
- Detailed descriptions
- Assigned team members
- Priority levels
- Category tags
- Some tasks include sample notes

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

## 🔒 Privacy

This application:
- Runs entirely in your browser
- Does not collect or transmit any data
- Stores all data locally on your device
- Requires no server or database
- No external API calls

## 🆕 Version 2.0 Updates

### New Features
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

---

**Note**: This application is designed to work immediately without any setup. Simply open `index.html` in your browser and start managing THE LIGHT PARK 2026 season tasks!